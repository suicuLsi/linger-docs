# Data and privacy

This is a technical overview of the current design, checked on October 28, 2026. It is not a substitute for the privacy terms presented on the website or in the application.

## Your local library

Linger stores library records locally in SQLite. Imported files are copied into a managed library; importing does not modify the original source file. Stored notes, tags, and source links supply context for finding a reference again.

Moving an item to the library's trash is recoverable. Permanently removing it can remove Linger's managed copy, preview, and record; it must not remove the original external source file. Keep an independent backup of valuable material: local storage alone is not a backup strategy.

## Personal words and machine observations

Personal notes and tags are stored separately from machine analysis. An analysis update appends a revision instead of replacing what the user wrote. User corrections to machine tags are also preserved separately from the original generated analysis.

A proposed aesthetic term remains a suggestion with supporting references. It is not automatically treated as the user's preference. Read the [design note](personal-notes-and-ai.md) for the reasoning behind this distinction.

## When content can leave the device

AI processing is optional and starts disabled. If you enable an external model API, Codex, or an external MCP agent, the text and image previews needed for the authorized task can be sent to that client or provider. Its account, retention, and data-use terms apply. A local MCP connection does not imply local model inference.

MCP access is read-only unless write tools are explicitly enabled. Read-only access can still reveal retrieved content to the connected client, so scope requests to the collection or items you intend to share. The interface does not offer arbitrary file reads, SQL access, or library deletion tools.

On macOS, user-supplied API credentials are stored in the system Keychain rather than as readable keys in the library database. This is not a claim that all library files are encrypted by Linger.

## Accounts and licensing

The current private candidate requires email sign-in for account, trial, and license management. These services use the network and are separate from library storage. Signing out clears the local session and closes library access; it does not delete the library.

Offline access depends on an already signed-in account and a valid cached entitlement. First sign-in and external model requests require connectivity. This page does not promise unrestricted offline access or cloud backup.

## Public examples

The examples in this repository use fictional IDs and synthetic descriptions. The demo screenshot uses the website's curated museum sample content. No private library export or customer data is included.
