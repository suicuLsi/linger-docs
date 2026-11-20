# Linger

**A private, local-first design reference library for macOS.**

Keep images, screenshots, links, and the reason you saved them in one local library. Linger runs on Apple Silicon Macs with macOS 14 or later. The desktop app uses AppKit and SwiftUI with a shared Rust core and SQLite storage. Each Mac keeps its own library, with no built-in cloud sync.

[Download for Mac](https://withlinger.com/download) · [Pricing and licenses](https://withlinger.com/pricing/) · [Browser demo](https://withlinger.com/demo/)

The public download includes a **7-day free desktop trial** from your first sign-in, with no card required. Regular one-time prices are **$39 USD for Personal** and **$79 USD for Lifetime**. See the pricing page for current offers and update coverage.

## Start here

| Read | Use it to |
| --- | --- |
| [Product and availability](docs/product.md) | Check system requirements, trial terms, and the reference workflow. |
| [Data and privacy](docs/data-and-privacy.md) | Understand managed files, SQLite storage, and when data can leave your Mac. |
| [MCP guide](docs/mcp.md) | Connect a local agent with read-only access by default and opt in to write tools if needed. |
| [MCP configuration and examples](examples/mcp/README.md) | Copy Codex or Claude Desktop settings, run a read-only check, and inspect the published tool schemas. |
| [Personal notes and AI analysis](docs/personal-notes-and-ai.md) | Understand how Linger stores machine observations separately from your words. |

## Engineering notes and benchmarks

| Topic | Official article | GitHub reference |
| --- | --- | --- |
| Local stdio MCP and bring-your-own-key (BYOK) AI | [Connect your local design reference library to AI agents via MCP](https://withlinger.com/resources/mcp-design-reference-library/) | [Client configurations and tool schemas](examples/mcp/README.md) |
| Library storage and ownership | [Local-first design reference architecture on Mac](https://withlinger.com/resources/local-first-reference-library/)¹ | [Managed copies, SQLite, and privacy](docs/data-and-privacy.md) |
| Native macOS migration | [Why we rebuilt Linger as a native Mac app](https://withlinger.com/resources/why-we-built-native-mac-app/)¹ | [Native gallery baseline and measurement limits](benchmarks/native-migration-baseline.md) |
| Recall ranking experiments | [Finding an image you can almost remember](https://withlinger.com/resources/how-linger-recall-evolved/) | [80-query evaluation summary and data links](benchmarks/recall-80-query-summary.md) |

¹ These two article URLs returned HTTP 404 on November 20, 2026. The linked GitHub references are available here.

![Linger's browser demo showing a visual library of museum reference images](assets/library-demo.webp)

*Curated museum references in the browser demo. [Image sources and demo limits](docs/demo-and-sources.md).*

## Author and product

Linger is created by **Lucius Miao** at **BlackHarbor Analytics Limited**. Development began in June 2026. The creator maintains these documentation and engineering notes from Linger's implementation and development records, with AI-assisted drafting and editing.

[GitHub](https://github.com/suicuLsi) · [LinkedIn](https://www.linkedin.com/in/lucius-miao-820b57429/) · [X](https://x.com/suicuLsi) · [About Linger](https://withlinger.com/about/)

For documentation corrections, [open an issue](https://github.com/suicuLsi/linger-docs/issues) with the page and the expected correction. Keep private library content and credentials out of public reports.

This repository contains public documentation, configuration examples, and benchmark summaries. Download the installer from the official site. Linger's application source remains private. Copyright © 2026 BlackHarbor Analytics Limited. Application source code and trademarks are not licensed by this repository. The MCP configuration and synthetic requests may be copied and adapted for integrations. Museum artwork credits are listed separately.
