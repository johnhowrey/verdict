# Verdict

Design review as MCP tools.

**Live:** https://verdict.allthepossibles.com (docs: `/docs`)
**Built by:** [All the Possibles](https://allthepossibles.com)
**Registry:** `com.allthepossibles/verdict` in the official MCP Registry

## What it does

Six review prompts I kept pasting into Claude before shipping UI, exposed as tools so an agent can run them before it hands work back:

- `critique_experience`: a structured critique of a page or flow.
- `list_states`: every state a feature can be in (empty, loading, error, partial, overflow) and which ones the design covers.
- `map_journey`: the user journey through a flow, with the step where people fall out.
- `audit_copy`: button labels, error messages, and empty-state text, with rewrites.
- `surface_assumptions`: what a PRD assumes without saying so.
- `check_terminology`: the same thing called by different names across a product.

The prompts started as the free Claude skills in [design-review-skills](https://github.com/johnhowrey/design-review-skills). The reviews run on Claude.

## Using it

**As an MCP server:**

```json
{
  "mcpServers": {
    "verdict": { "url": "https://verdict.allthepossibles.com/mcp" }
  }
}
```

**REST:**

```
curl -X POST https://verdict.allthepossibles.com/api/critique \
  -H "content-type: application/json" \
  -H "x-anthropic-key: sk-ant-..." \
  -d '{"url": "https://example.com/pricing"}'
```

Full reference: https://verdict.allthepossibles.com/docs

## Pricing

- **Bring your own key:** send your Anthropic key in an `x-anthropic-key` header and every call runs on your account. No limit, nothing metered, the key is never stored or logged.
- **Demo:** two calls a day per caller without a key.
- **Hosted:** $5/month Basic or $19/month Pro if you would rather not manage a key. Both are in the [Studio Bundle](https://allthepossibles.com).

## Issues

Open one here. Say which tool gave the weakest output and what you expected instead; that is the order things get fixed in.
