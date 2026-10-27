# Why Linger keeps personal notes separate from AI analysis

By **[Lucius Miao](https://www.linkedin.com/in/lucius-miao-820b57429/)**, creator of Linger at BlackHarbor Analytics Limited. Published October 28, 2026.

This development note describes an implemented product decision. It was drafted and edited with AI assistance, using the current implementation and development records. The example below is fictional; it is not a customer quote or a model benchmark.

## An image description cannot explain why you saved it

Imagine saving a photograph of a room. Your note says:

> The light reminds me of my grandmother's kitchen.

A model might describe the same image as:

> Warm window light, wooden furniture, muted colors.

Both can help you return to the reference. They answer different questions. The first preserves a personal association. The second supplies visible features that may make the image easier to retrieve.

If an application merges those statements into one editable summary, it becomes difficult to tell which words came from you. A later analysis can also make an older memory look as though it has changed. In a reference library, preserving that distinction matters more than producing a polished paragraph.

## The separation in Linger

Linger keeps three kinds of information distinct:

| Information | Role |
| --- | --- |
| Personal notes and tags | What the user explicitly recorded. |
| Machine analysis | Descriptions, tags, OCR, and summaries produced by an analysis client. |
| Aesthetic vocabulary suggestions | Proposed terms supported by specific references, still presented as suggestions. |

Machine analysis is stored as revisions. Updating it does not overwrite personal notes, personal tags, or the original source. When a user corrects machine tags, that correction is stored separately so another analysis does not silently replace the correction.

The MCP interface reflects this decision. A write includes an expected revision, and a stale write is rejected. This is a practical way to avoid an agent publishing an old interpretation over a newer result.

## Evidence before interpretation

A saved reference can support a statement about what is visible. It cannot, by itself, establish a lasting preference. Saving one red poster does not prove that red is your favorite color, or explain whether you saved it for its typography, subject, or layout.

For that reason, proposed aesthetic vocabulary stays attached to specific references and a stated reason. The system does not automatically promote it into a confirmed statement about the user.

The same distinction applies to uncertainty. OCR should transcribe legible text, rather than invent missing letters. A summary should be based on the complete saved body, rather than silently treating a truncated excerpt as a whole article. The MCP guide makes these boundaries explicit for connected agents.

## What this costs

Separate fields and revisions require more explanation in the interface. They also leave disagreement visible: a user may describe an image differently from a model. Linger accepts that cost because the library is meant to preserve the user's context.

This architecture does not make model output correct. Optional analysis still needs a chosen provider, a defined scope, and useful results. Nor does storing a library locally mean an external analysis runs locally: selected text and previews can leave the device when a user enables a remote client or model.

The design gives each kind of information a clear origin. That makes it easier to revise an interpretation while keeping the original reason for saving something intact.

Related: [data and privacy](data-and-privacy.md) · [MCP workflow](mcp.md) · [Linger](https://withlinger.com/)
