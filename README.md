# TadaPay Marketplace Skill

Find APIs and services for agents. Search by use case, payment protocol, and network, then retrieve the information needed to access a selected product.

The skill connects to TadaPay's maintained directory at **https://tadapay.ai/mcp**. The catalog is shared with [TadaPay Marketplace](https://tadapay.ai/ecosystem), so catalog updates are available without reinstalling the skill.

## What it provides

- Merchant and product search with catalog-level and product-type filters.
- Consistent network names and identifiers.
- Payment options with their own amount, asset, network, source, and review scope.
- Product endpoints, request formats, examples, and documentation where supplied by the provider.
- Official protocol guides for wallet and payment-client setup.

Discovery is available without a wallet. Payments are handled by the user's chosen payment client using the merchant's current requirements.

## Install

Use an agent application that supports local skills and Streamable HTTP MCP connections. Download or clone this repository, install the skill, and connect the directory.

### 1. Install the skill

Copy `skills/tadapay-marketplace` to the appropriate location, retaining the folder name:

| Application | Personal installation | Project installation |
| --- | --- | --- |
| Codex | `~/.agents/skills/tadapay-marketplace` | `.agents/skills/tadapay-marketplace` |
| Claude Code | `~/.claude/skills/tadapay-marketplace` | `.claude/skills/tadapay-marketplace` |

`~` denotes your user home directory. Choose the scope you need and review an existing installation before replacing it.

### 2. Connect the directory

Codex:

```sh
codex mcp add tadapay-marketplace --url https://tadapay.ai/mcp
```

Claude Code:

```sh
claude mcp add --transport http --scope user tadapay-marketplace https://tadapay.ai/mcp
```

Approve the connection in your application and start a new session if required. Confirm that `search_products` and `get_product` are available.

For file-based setup, use the [Codex configuration](examples/codex.config.toml) or [Claude Code configuration](examples/claude-code.mcp.json). Merge the Codex entry into `~/.codex/config.toml`, or the Claude Code example into your project's `.mcp.json`, preserving existing settings. Other compatible applications can use the same MCP URL.

Installation references: [Codex skills](https://learn.chatgpt.com/docs/build-skills), [Codex MCP](https://developers.openai.com/codex/mcp), [Claude Code skills](https://code.claude.com/docs/en/skills), [Claude Code MCP](https://code.claude.com/docs/en/mcp).

## Use

Invoke `$tadapay-marketplace` in Codex or `/tadapay-marketplace` in Claude Code. The skill can also be selected automatically for a relevant request.

> Find weather APIs that accept x402 on Base. Prefer reviewed options that match my requirements.

> Find an MPP model API on Tempo. Show its request format and the basis for its price.

> I already have a payment client. Give me the endpoint and request details for this product.

> Show the official payment-client documentation for this product's protocol.

## Selecting a product

Recommendations preserve the requested service, protocol, and network. Among equally relevant matching documented options, the skill prefers Verified, Listed, then Discovered products.

| Level | Meaning |
| --- | --- |
| Discovered | Collected from public sources. |
| Listed | Endpoint and protocol checks completed, with operator review of documented payment options. |
| Verified | Listed criteria met and TadaPay SDK integration confirmed. |

Review applies to the documented payment route. These levels describe technical checks and integration, not completed payments or guaranteed delivery.

Each payment option carries its own pricing evidence. A directory reference price, an observed challenge, and dynamic pricing serve different purposes; the merchant's fresh challenge determines the current requirements for a particular request.

Wallet guidance links to protocol-maintained documentation. The user chooses and configures their payment client.

## Repository and service

This repository contains the skill, application metadata, and connection examples. TadaPay operates the MCP service and maintains the catalog separately.

Search terms and filters are sent to the directory. Keep queries focused on product discovery and keep credentials and personal records out of them.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for contributions and [SECURITY.md](SECURITY.md) for sensitive reports.

## License

[MIT](LICENSE). The license covers the repository files. The service, third-party product data, and trademarks retain their respective terms.
