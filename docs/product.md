# Product and availability

Linger is a private, local-first visual reference library for macOS, created by Lucius Miao at BlackHarbor Analytics Limited.

The goal is to preserve enough context to make a saved reference useful later: the image or excerpt, where it came from, and what you noticed about it.

## A reference workflow

1. **Collect.** Import local files or use the browser extension to save supported media, a page link, an article, or selected text. Article extraction depends on the page; a saved link is not a complete offline website copy.
2. **Add context.** Keep source links, personal notes, and tags alongside the reference. Your words remain distinct from optional machine-generated descriptions.
3. **Return to an idea.** Browse visually or search stored text clues. Optional model-assisted recall is a separate capability; a relevant-looking result is not a guarantee that every detail in a query matches.
4. **Arrange references.** A lightweight canvas helps compare images and notes during a session. The current canvas is not a durable project document: it remains while moving between app pages, but is not retained after quitting the application.

## Platform and scope

- The current desktop target is macOS.
- The core library uses local storage. Cloud library sync and team collaboration are not part of the current product.
- Browser capture supports specific page and media types; it does not promise unrestricted access to social platforms or protected content.
- AI processing is optional and off by default. The application also has account and licensing services; local-first does not mean that every operation works without a network connection.

## Availability

As of October 28, 2026, the application is in private validation and public installer distribution is paused. This repository does not grant access to a private build or distribute an installer.

The [browser demo](https://withlinger.com/demo/) uses curated sample content. It lets you explore the interface, but does not connect to your desktop library, exercise native file access, or provide the desktop MCP server. Demo changes are temporary.

See [withlinger.com](https://withlinger.com/) for current product information and availability, and [data and privacy](data-and-privacy.md) for the boundary between local storage and network services.
