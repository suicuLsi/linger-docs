# Data and privacy

Linger is a native Mac app with an AppKit and SwiftUI interface and a shared Rust core. It keeps your reference library on your Mac. See [product and availability](product.md) for the supported Macs, public download, and trial.

## Your local library

Linger stores library records locally in SQLite. It copies imported files into the managed library and leaves external source files in place. Notes, tags, source links, and project canvases are saved locally. Each Mac has a separate library, with no built-in cloud sync or shared cloud library.

Moving an item to the library's trash is recoverable. Permanently removing it can remove the managed copy, preview, and record. The original file outside the library is left untouched. Back up the library separately if you want a copy outside that Mac.

## Personal words and machine observations

Linger stores personal notes and tags separately from machine analysis. An analysis update appends a revision. User corrections to machine tags are preserved separately from generated analysis.

An aesthetic vocabulary entry is a suggestion with supporting references. Read the [design note](personal-notes-and-ai.md) for how Linger distinguishes suggestions from a user's stated preferences.

## When content can leave the device

Core browsing and saved-text search use local data. AI processing is optional and starts disabled. When you enable an external model API, Codex, or an external MCP agent, text and previews needed for the task may be sent to that client or model provider. Its account, retention, and data-use terms apply. The client connects to Linger over local stdio and can use a remote model for inference.

The [MCP server](https://withlinger.com/docs/mcp/) defaults to read-only. Reading can expose the retrieved text or preview to the connected client, so request only the items needed for the task. The server provides a defined set of tools without arbitrary file access, SQL, or deletion.

Linger stores BYOK API credentials in the macOS Keychain. Library files and previews use separate local storage.

## Accounts and licensing

A 7-day full trial begins when you open Linger, with no sign-in required. Optional email sign-in (which adds 23 extra trial days for 30 days total), activation codes, and license management use online services separate from library storage. Offline use relies on an active local trial or cached entitlement. Signing out clears the local session while retaining the library files. After a trial expires, existing content remains available for browsing, basic search, and export. See [desktop trial and license data](https://withlinger.com/privacy/) and [pricing and licenses](https://withlinger.com/pricing/).

## Public examples

The MCP requests in this repository use fictional IDs and descriptions. The [demo screenshot](demo-and-sources.md) shows curated museum reference content. The benchmark pages publish aggregate measurements and link to the official anonymized Recall ranks.
