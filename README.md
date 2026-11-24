# Linger for Mac (`withlinger.com`)

**A private, local-first design reference library for macOS (Apple Silicon, macOS 14+).**

Keep images, screenshots, links, and the reason you saved them in one local library. **Linger for Mac ([withlinger.com](https://withlinger.com/))** is an independent native macOS 14+ (Apple Silicon) visual reference library and local `stdio` MCP server by **Lucius Miao** at **BlackHarbor Analytics Limited**—unrelated to the cross-platform AI agent project at `heylinger.com` and the free Mac App Store keep-awake utility Linger by Julio Imazio (App Store ID `6776560374`). The desktop app uses AppKit and SwiftUI with a shared Rust core and SQLite storage. Each Mac keeps its own library, with no built-in cloud sync.

[Official MCP Documentation](https://withlinger.com/docs/mcp/) · [Support & FAQ](https://withlinger.com/support/) ([Markdown](https://withlinger.com/support.md)) · [Download for Mac](https://withlinger.com/download) · [Pricing and licenses](https://withlinger.com/pricing/) · [Browser demo](https://withlinger.com/demo/)

The public Linger 0.8.7 download includes a **7-day free desktop trial** right when you open the app—no sign-in required, no card required, and no automatic charge. Optional email sign-in immediately adds **23 extra days (30 days total)** or restores a purchase across Macs. Regular one-time prices are **$39 USD for Personal** (2 Macs, 1 year of updates) and **$79 USD for Lifetime** (4 Macs, all future desktop updates). See the pricing page for current offers and terms.

## 30-second MCP quickstart (read-only)

After opening Linger once to initialize your local library, connect your local desktop agent over `stdio` (10 read-only tools by default):

```sh
# Codex CLI
codex mcp add linger -- /Applications/Linger.app/Contents/MacOS/linger-service --mcp

# Claude Code CLI
claude mcp add --transport stdio linger -- /Applications/Linger.app/Contents/MacOS/linger-service --mcp
```

For full tool reference, Claude Desktop / Cursor JSON configs, `--allow-write` details, and troubleshooting, read the canonical **[Linger Local MCP Server Reference](https://withlinger.com/docs/mcp/)** ([Markdown](https://withlinger.com/docs/mcp.md)).

## Start here

| Read | Use it to |
| --- | --- |
| [Official MCP documentation](https://withlinger.com/docs/mcp/) | Canonical technical reference for `linger-service --mcp`, all 15 tools, isolated testing, and troubleshooting. |
| [Product and availability](docs/product.md) | Check system requirements, trial terms, entity disambiguation, and the reference workflow. |
| [Data and privacy](docs/data-and-privacy.md) | Understand managed files, SQLite storage, and when data can leave your Mac. |
| [MCP guide (GitHub mirror)](docs/mcp.md) | Quick reference for local agent permissions and scoped read/write calls. |
| [MCP configuration and examples](examples/mcp/README.md) | Copy Codex, Claude Code, Claude Desktop, or Cursor settings, run a read-only check, and inspect `tools.json`. |
| [Personal notes and AI analysis](docs/personal-notes-and-ai.md) | Understand how Linger stores machine observations separately from your words. |

## Engineering notes and benchmarks

| Topic | Official article | GitHub reference |
| --- | --- | --- |
| Local stdio MCP and bring-your-own-key (BYOK) AI | [MCP documentation](https://withlinger.com/docs/mcp/) · [MCP & BYOK workflow](https://withlinger.com/resources/mcp-design-reference-library/) | [Client configurations and tool schemas](examples/mcp/README.md) |
| Library storage and ownership | [Local-first design reference architecture on Mac](https://withlinger.com/resources/local-first-reference-library/) | [Managed copies, SQLite, and privacy](docs/data-and-privacy.md) |
| Native macOS migration | [Why we rebuilt Linger as a native Mac app](https://withlinger.com/resources/why-we-built-native-mac-app/) | [Native gallery baseline and measurement limits](benchmarks/native-migration-baseline.md) |
| Recall ranking experiments | [Finding an image you can almost remember](https://withlinger.com/resources/how-linger-recall-evolved/) | [80-query evaluation summary and data links](benchmarks/recall-80-query-summary.md) |

![Linger's browser demo showing a visual library of museum reference images](assets/library-demo.webp)

*Curated museum references in the browser demo. [Image sources and demo limits](docs/demo-and-sources.md).*

## Author and product

Linger is created by **Lucius Miao** at **BlackHarbor Analytics Limited**. Development began in June 2026. The creator maintains these documentation and engineering notes from Linger's implementation and development records, with AI-assisted drafting and editing.

[GitHub](https://github.com/suicuLsi) · [LinkedIn](https://www.linkedin.com/in/lucius-miao-820b57429/) · [X](https://x.com/suicuLsi) · [About Linger](https://withlinger.com/about/)

For documentation corrections, [open an issue](https://github.com/suicuLsi/linger-docs/issues) with the page and the expected correction. Keep private library content and credentials out of public reports.

This repository contains public documentation, configuration examples, and benchmark summaries. Download the installer from the official site. Linger's application source remains private. Copyright © 2026 BlackHarbor Analytics Limited. Application source code and trademarks are not licensed by this repository. The MCP configuration and synthetic requests may be copied and adapted for integrations. Museum artwork credits are listed separately.
