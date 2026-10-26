# Verdict

Design review as MCP tools.

**Live:** https://verdict.allthepossibles.com (docs: `/docs`)
**Built by:** [All the Possibles](https://allthepossibles.com)
**Registry:** `com.allthepossibles/verdict` in the official MCP Registry

## What it does

Six review prompts I kept pasting into Claude before shipping UI, exposed as tools so an agent can run them before it hands work back:

- `critique_experience`: a structured critique of a page or flow.
- `generate_state_matrix`: every state a feature can be in (empty, loading, error, partial, overflow) and which ones the design covers.
- `map_journey`: the user journey through a flow, with the step where people fall out.
- `audit_copy`: button labels, error messages, and empty-state text, with rewrites.
- `find_assumptions`: what a PRD assumes without saying so.
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
curl https://verdict.allthepossibles.com/api/tools
```

lists the six tools with their input schemas; each one is `POST /api/<tool_name>` with the same JSON body the MCP tool takes, plus an optional `x-anthropic-key` header.

Full reference: https://verdict.allthepossibles.com/docs

## Pricing

- **Bring your own key:** send your Anthropic key in an `x-anthropic-key` header and every call runs on your account. No daily cap (20 calls a minute), nothing metered, the key is never stored or logged.
- **Demo:** two calls a day per caller without a key.
- **Hosted:** $5/month Basic or $19/month Pro if you would rather not manage a key. Pro on every All the Possibles product is also included in the [Membership](https://allthepossibles.com) ($15/month or $150/year).

## Issues

Open one here. Say which tool gave the weakest output and what you expected instead; that is the order things get fixed in.
