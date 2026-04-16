# Neotoi Coder v2.0 — Dioxus Benchmark

Five tasks where general models fail and Neotoi v2.0 succeeds.
Run against any OpenAI-compatible endpoint.

---

## Task 1 — Accessible Tooltip

**Prompt:**
Build a Dioxus 0.7 accessible tooltip. The trigger button must
reference the tooltip via aria_describedby unconditionally.
The tooltip must always be in the DOM — show/hide via CSS class,
not DOM removal.

**GPT-4o typical failure:**
```rust
// ❌ Removes tooltip from DOM — invisible to screen readers
if show_tooltip() {
    div { role: "tooltip", id: "hint", "Beta feature" }
}
button { "Feature" } // aria_describedby missing
```

**Neotoi v2.0:**
```rust
// ✅ Always in DOM, CSS controls visibility
div {
    role: "tooltip",
    id: "hint",
    class: if show_tooltip() { "visible" } else { "sr-only" },
    "Beta feature"
}
button {
    aria_describedby: "hint", // unconditional
    "Feature"
}
```

---

## Task 2 — use_resource Three-Arm Match

**Prompt:**
Fetch posts from /api/posts using use_resource. Handle all three
states: loading, error, success. Do not use .ok() wrapper.

**GPT-4o typical failure:**
```rust
// ❌ .ok() collapses error — loses error information
match resource.read().as_ref().ok() {
    None => rsx! { "Loading..." },
    Some(posts) => rsx! { /* render */ }
}
```

**Neotoi v2.0:**
```rust
// ✅ Three-arm match preserves all states
match resource.read().as_ref() {
    None => rsx! {
        div { role: "status", aria_label: "Loading posts", "Loading..." }
    },
    Some(Err(e)) => rsx! {
        div {
            role: "alert",
            aria_labelledby: "err-title",
            h2 { id: "err-title", "Error" }
            p { "{e}" }
        }
    },
    Some(Ok(posts)) => rsx! {
        ul {
            for post in posts {
                li { key: "{post.id}", "{post.title}" }
            }
        }
    }
}
```

---

## Task 3 — GlobalSignal Write Semantics

**Prompt:**
Create a language toggle that switches between "en" and "vi"
using a GlobalSignal<&'static str>.

**GPT-4o / DeepSeek typical failure:**
```rust
// ❌ .set() fails to compile on static GlobalSignal
pub static LANG: GlobalSignal<&str> = Signal::global(|| "en");

LANG.set("vi"); // ERROR: cannot borrow as mutable
```

**Neotoi v2.0:**
```rust
// ✅ Interior mutability via .write()
pub static LANG: GlobalSignal<&'static str> = Signal::global(|| "en");

// In component:
*LANG.write() = if LANG() == "en" { "vi" } else { "en" };
```

---

## Task 4 — data-slot Hyphen Convention

**Prompt:**
Render a Dioxus 0.7 SVG icon with a data-slot attribute
set to "icon".

**GPT-4o typical failure:**
```rust
// ❌ Underscore renders as data_slot — invalid HTML attribute
svg {
    data_slot: "icon",
    // renders as: <svg data_slot="icon">
}
```

**Neotoi v2.0:**
```rust
// ✅ Quoted hyphen for data-* attributes
svg {
    "data-slot": "icon",
    // renders as: <svg data-slot="icon">
}
```

---

## Task 5 — use_context Panic Behavior

**Prompt:**
Build a ThemeProvider using use_context_provider. A child
component consumes it via use_context. Explain what happens
if no provider exists.

**GPT-4o typical failure:**
```rust
// ❌ use_context does NOT return Option — this won't compile
let theme = use_context::<Theme>();
if let Some(t) = theme { // type mismatch
    // ...
}
```

**Neotoi v2.0:**
```rust
// ✅ use_context panics without provider — always provide first
fn App() -> Element {
    // Provider MUST be ancestor — not sibling, not child
    use_context_provider(|| Theme::Light);
    rsx! { ThemeConsumer {} }
}

#[component]
fn ThemeConsumer() -> Element {
    // Safe — provider exists in ancestor tree
    // Would PANIC if App() didn't call use_context_provider
    let theme = use_context::<Theme>();
    rsx! { div { "{theme:?}" } }
}
```
