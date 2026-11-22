# Gallery prototype baseline for the native macOS migration

On November 11, 2026, Linger measured a gallery prototype on one Apple Silicon Mac (Mac15,3, 24 GiB RAM) before the AppKit and SwiftUI migration. The native prototype used an AppKit reuse grid, ImageIO thumbnail decoding, and a read-only Rust and SQLite projection. The Web comparison used a WKWebView with a production React bundle and mounted every card.

The input was an isolated copy of **169 valid images**. The 1,000- and 5,000-item tiers repeated those files to exercise UI scaling. Runs used a 1440 × 920 point window at 2× scale. The table shows medians of three runs per condition.

| Gallery items | First viewport ready, Web / native 384 px | Main-thread timer p95, Web / native 384 px | Native peak host RSS, 1024 px / 384 px |
| ---: | ---: | ---: | ---: |
| 169 | 584 / 182 ms | 18 / 10.8 ms | 659 / 255 MiB |
| 1,000 (repeated) | 682 / 189 ms | 81 / 10.9 ms | 653 / 233 MiB |
| 5,000 (repeated) | 1,801 / 182 ms | 205 / 10.9 ms | 651 / 232 MiB |

Changing the thumbnail decode limit from 1024 px to 384 px reduced host peak RSS by about **61%–64%** within the same native prototype. Full-resolution viewing used a separate decode path.

## Measurement limits

- First viewport readiness covers layout and visible image decoding after the test harness starts. The Web and native harnesses showed approximately 16 and 25 initial cards, respectively. These measurements cannot establish a full-app cold-start or cross-stack speedup.
- The timer column records intervals for a 10 ms main-thread timer during about three seconds of scrolling. It measures event-loop responsiveness. At 5,000 items the Web harness recorded only 12–19 callbacks per run, so the p95 describes a short sample. Frame rate and input-to-display latency require separate measurement.
- RSS compares thumbnail sizes inside one native host. WKWebView's separate WebContent, GPU, and Networking processes make host RSS insufficient for a cross-stack memory comparison.
- Repeated references stress the number of UI items while keeping the underlying corpus at 169 images. They cannot establish capacity or indexing performance for 5,000 unique files.

[Native migration release notes](https://withlinger.com/changelog/#v0-6-0) · [Native architecture article](https://withlinger.com/resources/why-we-built-native-mac-app/)
