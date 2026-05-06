# gpt-image-gen

Generate a PNG image via the OpenAI Images API and save it to a caller-specified path.

## When to Use

Any time an agent needs to produce an image. The caller provides a complete prompt and an output path; this skill handles the API call, decoding, saving, and verification.

## Prerequisites

- `OPENAI_API_KEY` must be present in `.env` at the project root.
- `curl` must be available in the shell.
- Either `jq` (primary) or Python 3 (fallback) must be available for decoding.

## Parameters

| Parameter | Description |
|-----------|-------------|
| `PROMPT` | The complete image generation prompt (plain text — do not pre-escape) |
| `OUTPUT_PATH` | Destination file path including `.png` extension (e.g. `yuval/outputs/2026-05-06-hero.png`) |

Model, size, quality, and format are fixed: `gpt-image-1`, `1024x1024`, `medium`, `png`.

## Execution

### Step 1 — Load the API key

```bash
source .env
```

### Step 2 — Detect jq

```bash
command -v jq >/dev/null 2>&1 && USE_JQ=true || USE_JQ=false
```

### Step 3A — Call API and save (primary: curl + jq)

Use when `USE_JQ=true`. The prompt is stored in a shell variable so Python handles JSON serialisation — this avoids manual quote-escaping inside the `curl -d` argument.

```bash
source .env
PROMPT='<your prompt text here>'
OUTPUT_PATH='<output file path>.png'

python -c "import json,sys; print(json.dumps({'model':'gpt-image-1','prompt':sys.argv[1],'size':'1024x1024','quality':'medium','output_format':'png'}),end='')" "$PROMPT" \
  | curl -s -X POST "https://api.openai.com/v1/images/generations" \
      -H "Authorization: Bearer $OPENAI_API_KEY" \
      -H "Content-Type: application/json" \
      -d @- \
  | jq -r '.data[0].b64_json' | base64 --decode > "$OUTPUT_PATH"
```

### Step 3B — Call API and save (fallback: Python end-to-end)

Use when `USE_JQ=false` (e.g. Git Bash on Windows without jq), or when jq is unavailable.

```bash
source .env
python - <<'PYEOF'
import os, json, base64, urllib.request

OPENAI_API_KEY = os.environ["OPENAI_API_KEY"]
PROMPT = """<your prompt text here>"""
OUTPUT_PATH = "<output file path>.png"

body = json.dumps({
    "model": "gpt-image-1",
    "prompt": PROMPT,
    "size": "1024x1024",
    "quality": "medium",
    "output_format": "png"
}).encode()

req = urllib.request.Request(
    "https://api.openai.com/v1/images/generations",
    data=body,
    headers={
        "Authorization": f"Bearer {OPENAI_API_KEY}",
        "Content-Type": "application/json"
    }
)
response = json.loads(urllib.request.urlopen(req).read())
with open(OUTPUT_PATH, "wb") as f:
    f.write(base64.b64decode(response["data"][0]["b64_json"]))
print(f"Saved: {OUTPUT_PATH}")
PYEOF
```

### Step 4 — Verify

```bash
[ -s "$OUTPUT_PATH" ] && echo "OK: $OUTPUT_PATH" || echo "FAILED: file missing or empty"
```

If verification fails, capture and report the raw API response body before claiming failure. Do not retry silently.

## Error Handling

- `OPENAI_API_KEY` empty or unset → stop, report "OPENAI_API_KEY not set in .env"
- API response contains `"error"` key → extract `.error.message` and report; do not decode
- Output file missing or zero bytes after decode → report "image save failed" with raw response
