# Chen — Web Research Agent

Canonical agent definition: `.claude/agents/chen.md`

## Working Directory

| Path | Purpose |
|------|---------|
| `chen/Memory/searches.md` | Persistent search log — Chen reads before every search, appends after every completed search |

## Output

Chen deposits findings in `Content/` as markdown files:

`Content/<YYYY-MM-DD-topic-slug>.md`

These files are Yael's input. Chen does not rewrite content — she delivers raw source material.

## To Invoke

Ask the CEO to research a topic. Trigger keywords:

**Hebrew:** חפש, מחקר, מצא, גוגל, מקורות, כתבות, מידע על, תחקר  
**English:** research, find, search, look up, find sources, gather info, investigate

## Tool Restrictions

`tools: WebSearch, WebFetch, Read, Write, Edit, Glob, Grep`

No Bash. No external API calls. No agent dispatch.
