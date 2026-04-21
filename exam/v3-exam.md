# Neotoi Coder v3 — New Exam Questions

These questions cover gaps from v2.0 exam failures
and new Dioxus 0.7.3-0.7.5 features.

---

## TIER 2 FIXES — RSX Precision (replaces Q8, Q21)

**Q8-v3**
Convert this exactly to Dioxus 0.7 RSX — no added
attributes, no missing attributes, no reordering:
```html
<button type="button" class="px-4 py-2 rounded">
  Toggle
</button>
```
Must use r#type: not type:. Must include "Toggle"
text node. Must not add aria or class modifications.

**Q21-v3**
Convert this exactly to Dioxus 0.7 RSX:
```html
<details class="border rounded p-4">
  <summary class="font-medium cursor-pointer">
    Show more
  </summary>
  <p class="mt-2 text-gray-600">
    Additional content here.
  </p>
</details>
```
Output must be Dioxus RSX not React JSX.
No className, no useState, no onClick.

---

## TIER 7 — Scoped CSS and CSS Modules (0.7.3)

**Q78-v3 — Native Scoped CSS**
Create a Dioxus 0.7.3 component using the native
scoped CSS feature. Use the css!() macro to define
scoped styles inline. Apply scoped class to a card
div with title and body. Show the correct import.

Expected pattern:
```rust
use dioxus::prelude::*;

#[component]
fn Card(title: String, body: String) -> Element {
    let styles = css!(
        ".card { border: 1px solid #e2e8f0; }"
        ".card-title { font-weight: bold; }"
    );
    rsx! {
        div {
            class: "{styles} card",
            h2 { class: "card-title", "{title}" }
            p { "{body}" }
        }
    }
}
```

**Q79-v3 — CSS Modules 0.7.3 Native**
Create a Dioxus 0.7.3 component using native CSS
modules support (not the styles!() macro approach).
Show the correct import syntax for a .module.css
file and apply scoped classes to a navigation bar.
Include the companion nav.module.css file.

---

## TIER 8 — New Event Handlers (0.7.3)

**Q85-v3 — scrollend Event**
Build a Dioxus 0.7.3 component that detects when
scrolling has ended using the new onscrollend event.
Track scroll state with use_signal<bool>.
Show skeleton content while scrolling, real content
when stopped. Include role="status" aria_live on
the status indicator.

**Q86-v3 — auxclick Event**
Create a Dioxus 0.7.3 component with a link that
handles middle-click via onauxclick. Track click
count with use_signal<u32>. Show count inline.
Include aria_label on the link.

---

## TIER 10 — Dioxus 0.7.4/0.7.5 API Fixes

**Q97-v3 — WebSocket Stream+Sink (real implementation)**
Build a Dioxus 0.7.4 WebSocket chat component using
the actual Stream+Sink API. Import from dioxus::prelude.
Connect to wss://echo.example.com.
Track messages with use_signal<Vec<String>>.

The <think> block must address:
- Correct import path for WebSocket in Dioxus 0.7.4
- How use_resource integrates with async Stream
- How to send via Sink trait methods
- Reconnection strategy on disconnect

Do NOT simulate with tokio::sleep.
Show actual stream.next() and sink.send() calls.

**Q98-v3 — consume_context vs use_context placement**
Create a Dioxus 0.7 component demonstrating that
use_context_provider and use_context must both be
called in the component body BEFORE rsx! — never
inside rsx! macro blocks.

Show:
- WRONG: provide_context called inside rsx! {} 
- CORRECT: provide_context called before rsx! {}
- Both consume_context and use_context behavior
- Panic comment for missing provider

---

## TIER 11 — Server Functions (0.7.3) [NEW TIER]
Weight: 1.5 | Max: 9 points

**Q101 — Server-Only Extractors**
Create a Dioxus 0.7.3 fullstack component using
anonymous server functions with server-only extractors.
Show the #[server] attribute with extractor syntax.
The extractor should read an Authorization header.
Client component calls the server function and
handles the Result with three-arm match.

**Q102 — Fullstack WebSocket**
Build a Dioxus 0.7.3 fullstack WebSocket component
using the one-line websocket syntax. Show both
server and client side. Track connection state with
use_signal. Handle disconnect gracefully.

**Q103 — Server Function Error Codes**
Create a Dioxus 0.7.3 server function that returns
custom HTTP status codes on error. Show ServerFnError
with status code integration. Client handles specific
error variants differently in the three-arm match.

---

## Updated Scoring for v3 Exam

| Tier | Questions | Weight | Max |
|---|---|---|---|
| T1 Fundamentals | Q1-12 | 1.0 | 12 |
| T2 RSX Syntax | Q13-24 | 1.0 | 12 |
| T3 Signal Hygiene | Q25-36 | 1.0 | 12 |
| T4 WCAG/ARIA | Q37-50 | 1.5 | 21 |
| T5 use_resource | Q51-58 | 1.5 | 12 |
| T6 Hard Reasoning | Q59-68 | 2.0 | 20 |
| T7 Primitives+CSS | Q69-80 | 1.5 | 18 |
| T8 GlobalSignal/i18n | Q81-88 | 1.5 | 12 |
| T9 Static Navigator | Q89-94 | 1.5 | 9 |
| T10 Dioxus 0.7.4 | Q95-100 | 2.0 | 12 |
| T11 Server Functions | Q101-103 | 1.5 | 4.5 |
| **Total** | **Q1-103** | | **144.5** |

v3.0 release threshold: 85% = 123/144.5
