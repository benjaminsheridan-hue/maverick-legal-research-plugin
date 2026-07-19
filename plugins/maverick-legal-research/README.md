# Maverick Legal Research

Use Maverick's production statute, regulation, and CourtListener case-law
research directly from Codex or Claude Code. The plugin includes a shared legal
research skill and connects to the read-only remote MCP server at
`https://api.mavericklegalresearch.com/mcp`.

The server reports the stable `maverick-research-v1` contract. Its search tool
supports explicit `usc`, `cfr`, `state_statute`, and `state_admin_rule` corpus
scope; exact statute and case tools provide bounded full text for authorities
used in the final work product.

An active Maverick trial or subscription is required. OAuth is the default; a
per-seat `msk_*` API key remains available for unattended environments and
existing key-based clients can continue using it until their owner opts into
OAuth.

## Codex

Add the public marketplace:

```sh
codex plugin marketplace add benjaminsheridan-hue/maverick-legal-research-plugin
```

Restart the ChatGPT desktop app, open **Plugins**, choose **Maverick Legal
Research**, and install the plugin. The first research call opens the Maverick
portal for OAuth consent.

Direct MCP fallback:

```sh
codex mcp add maverick --url https://api.mavericklegalresearch.com/mcp
```

## Claude Code

```text
/plugin marketplace add benjaminsheridan-hue/maverick-legal-research-plugin
/plugin install maverick-legal-research@maverick-legal-research
```

Direct MCP fallback:

```sh
claude mcp add --transport http maverick https://api.mavericklegalresearch.com/mcp
```

## API-key fallback

Set `MAVERICK_API_KEY` to the per-seat key shown once in the Maverick portal,
then configure that environment variable as the MCP server's Bearer token:

```sh
codex mcp add maverick --url https://api.mavericklegalresearch.com/mcp --bearer-token-env-var MAVERICK_API_KEY
claude mcp add --transport http --header 'Authorization: Bearer ${MAVERICK_API_KEY}' maverick https://api.mavericklegalresearch.com/mcp
```

Do not commit keys or paste them into a shared plugin file.

Manage connected clients and revoke access at
`https://app.mavericklegalresearch.com/connect`.

[Privacy](https://mavericklegalresearch.com/privacy) ·
[Terms](https://mavericklegalresearch.com/terms)
