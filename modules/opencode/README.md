# opencode

Configures [opencode](https://opencode.ai) with Exa AI web search enabled.

## What It Does

- Exports `OPENCODE_ENABLE_EXA=1` to enable the `websearch` tool in opencode sessions

## Prerequisites

- opencode installed (e.g. `npm i -g opencode-ai`)

## Additional Configuration

To auto-approve websearch without prompting, add to your `opencode.json`:

```json
{
  "$schema": "https://opencode.ai/config.json",
  "permission": {
    "websearch": "allow"
  }
}
```
