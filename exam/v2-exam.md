# neotoi-coder v2 Exam — 100 Questions

---

## TIER 1 — Fundamentals (Q1–Q12, weight 1.0)

**Q1**

Write a Dioxus 0.7 component called Greeting that takes a name: String prop and renders Hello, {name}! inside an h1 tag with class text-2xl font-bold. Use #[component] macro with inline prop syntax.

**Q2**

Create a Dioxus 0.7 component with a button that increments a counter using use_signal. Display the count in a span below the button. Include mut on the signal binding.

**Q3**

Convert this exactly to Dioxus 0.7 RSX, no added attributes:
```html
<p class="text-gray-700">Hello <strong>world</strong>.</p>
```

**Q4**

Create a Dioxus 0.7 component that renders a list of five hardcoded city names using a for loop in RSX. Each li must have a stable key attribute.

**Q5**

Write a Dioxus 0.7 Toggle component. Track on/off with use_signal<bool>. Render a button that calls .toggle(). Display "On" or "Off" derived inline — no secondary signals.

**Q6**

Convert this exactly to Dioxus 0.7 RSX:
```html
<button type="button" aria-pressed="false" class="px-4 py-2">Toggle</button>
```

**Q7**

Create a Dioxus 0.7 component that conditionally renders a div only when a use_signal<bool> is true. When false render nothing using the correct empty RSX syntax.

**Q8**

Write a Dioxus 0.7 Card component that takes title: String and body: String props. Render in a styled div using Tailwind v4. Use #[component] macro.

**Q9**

Create a Dioxus 0.7 component with a text input bound to a use_signal<String>. Display the current value below the input as the user types using oninput. Use e.value() not e.value().unwrap_or_default().

**Q10**

Write a Dioxus 0.7 component that renders a nav element containing three anchor links. The nav must have aria_label: "Main navigation". No added attributes beyond what is specified.

**Q11**

Create a Dioxus 0.7 StatusBadge component. Take a status: String prop. Use a match expression directly inside the class attribute: "active" → green, "inactive" → gray, "error" → red, _ → yellow. No intermediate variables.

**Q12**

Write a Dioxus 0.7 component that renders a footer with copyright text and three social media links. Each link must have aria_label describing the destination. Footer must have role: "contentinfo".

---

## TIER 2 — RSX Syntax (Q13–Q24, weight 1.0)

**Q13**

Convert this exactly:
```html
<figure class="mt-4">
  <img src="/photo.jpg" alt="Team photo" width="800" height="600">
  <figcaption class="text-sm text-gray-500">Our team at the 2025 summit.</figcaption>
</figure>
```

**Q14**

Convert this exactly:
```html
<nav aria-label="Breadcrumb">
  <ol class="flex gap-2">
    <li><a href="/">Home</a></li>
    <li aria-hidden="true">/</li>
    <li><a href="/blog">Blog</a></li>
  </ol>
</nav>
```

**Q15**

Convert this exactly:
```html
<section aria-labelledby="section-title" class="py-8">
  <h2 id="section-title" class="text-2xl font-bold">Latest <mark>Updates</mark></h2>
  <p class="mt-2 text-gray-600">View the <a href="/changelog" class="underline text-blue-600">full changelog</a>.</p>
</section>
```

**Q16**

Convert this exactly:
```html
<p class="text-sm">Updated <time datetime="2026-03-11">March 11</time> by <strong>admin</strong>.</p>
```

**Q17**

Write a Dioxus 0.7 RSX block that renders a div with three children: text node "Hello", a span with class font-bold containing "world", and text node ".". No wrapping component — just the RSX block.

**Q18**

Write a Dioxus 0.7 component that renders an input of type email with a linked label. The label must use r#for pointing to the input's id. Input must have id, r#type, placeholder, and aria_describedby pointing to a hint paragraph. Hint always in DOM.

**Q19**

Create a Dioxus 0.7 component with a select dropdown. Each option must have a value attribute. Track selected value with use_signal. Update on onchange. Signal binding must be mut.

**Q20**

Write a Dioxus 0.7 component that renders an inline SVG icon. The SVG must have view_box, stroke_width, stroke_linecap, and stroke_linejoin in correct snake_case RSX. Include aria_hidden: "true" as it is decorative. Use data-slot not data_slot for data attributes.

**Q21**

Convert this exactly:
```html
<details class="border rounded p-4">
  <summary class="font-medium cursor-pointer">Show more</summary>
  <p class="mt-2 text-gray-600">Additional content here.</p>
</details>
```

**Q22**

Write a Dioxus 0.7 RSX block for a blog post card. Include: article element, h2 with post title, p with excerpt, a link with aria_label describing the post, and a time element with datetime attribute. No component wrapper needed.

**Q23**

Create a Dioxus 0.7 component with a textarea. Track value with use_signal<String>. Show character count derived inline. Enforce max 500 characters in oninput. Label uses r#for pointing to textarea id.

**Q24**

Convert this exactly — preserve all attributes and nesting:
```html
<div role="alert" aria-labelledby="error-title" class="rounded border border-red-300 p-4">
  <h2 id="error-title" class="font-semibold text-red-700">Error</h2>
  <p class="text-red-600">Something went wrong. Please try again.</p>
</div>
```

---

## TIER 3 — Signal Hygiene (Q25–Q36, weight 1.0)

**Q25**

Build a Dioxus 0.7 password strength indicator. One use_signal for input value. Derive strength label and bar color inline: under 6 chars weak/red, under 10 medium/yellow, otherwise strong/green. No secondary signals.

**Q26**

Create a Dioxus 0.7 character-limited textarea. One use_signal for value. Show remaining characters derived inline. Turn counter red when under 20 remaining. Max 280 characters enforced in oninput.

**Q27**

Build a Dioxus 0.7 multi-step form with 3 steps. One use_signal<u32> for current step. Derive step label and progress percentage inline. Show only current step fields. Back button must use step - 1 not hardcoded values.

**Q28**

Create a Dioxus 0.7 multi-select checkbox list. Track selected IDs in one use_signal<Vec<u32>>. Derive selected count inline. Include Select All / Deselect All. Each checkbox checked derived from whether its ID is in the signal.

**Q29**

Build a Dioxus 0.7 RangeSlider. Track value with use_signal<f32>. Derive label inline: "Low" under 33.0, "Medium" under 66.0, "High" otherwise. Include aria_valuenow, aria_valuemin: "0", aria_valuemax: "100" on the input element not a wrapper div.

**Q30**

Create a Dioxus 0.7 ThemeToggle. One use_signal tracks "light" or "dark". Derive button label and icon class inline. Apply different background classes based on theme. No secondary signals.

**Q31**

Build a Dioxus 0.7 SearchFilter. One use_signal<String> for query. Derive filtered list inline from hardcoded Vec<&str> of 10 items. Render only matching items. Show count derived inline. No secondary signals.

**Q32**

Create a Dioxus 0.7 PriceCalculator. Take unit_price: f32 and tax_rate: f32 as props. One use_signal<u32> for quantity. Derive subtotal, tax, and total inline. No secondary signals.

**Q33**

Build a Dioxus 0.7 StepCounter. Track steps with use_signal<u32>. Derive progress percentage inline against hardcoded goal of 10000. Render progress bar using derived percentage as inline style width. Include role: "progressbar" with aria_valuenow, aria_valuemin, aria_valuemax on the progress element.

**Q34**

Create a Dioxus 0.7 form with email and password fields. One use_signal per field. Derive validation state inline — no secondary signals for errors. Show field-level errors conditionally with role: "alert". Both errors must have aria_labelledby pointing to a heading id.

**Q35**

Build a Dioxus 0.7 ColorPicker component. One use_signal<String> for selected color from a hardcoded list of 6 colors. Derive the preview div's background class inline using match. Show selected color name inline. No secondary signals.

**Q36**

Create a Dioxus 0.7 CountdownTimer component. One use_signal<u32> for seconds remaining. Derive minutes and seconds display inline. Show warning class when under 60 seconds. Show danger class when under 10 seconds. No secondary signals.

---

## TIER 4 — WCAG 2.2 AAA and ARIA (Q37–Q50, weight 1.5)

**Q37**

Build a Dioxus 0.7 notification banner. role: "alert", aria_live: "assertive", aria_labelledby pointing to a real h2 id inside it. Close button with aria_label. Empty state uses rsx! {}. Conditionally rendered in DOM.

**Q38**

Create a Dioxus 0.7 modal dialog. role: "dialog", aria_modal: "true", aria_labelledby pointing to modal title id. Close on Escape via onkeydown. Backdrop overlay. Conditionally rendered.

**Q39**

Build a Dioxus 0.7 Accordion. Each button has aria_expanded, aria_controls pointing to panel id. Panel has matching id, role: "region", aria_labelledby pointing back to button id. Panel content conditionally rendered in DOM.

**Q40**

Create a Dioxus 0.7 RadioGroup. role: "radiogroup" on container. aria_labelledby pointing to group heading id. Each radio has linked label via r#for/id. Track selected with one use_signal.

**Q41**

Build a Dioxus 0.7 accessible tooltip. Trigger button has aria_describedby pointing to tooltip id unconditionally. Tooltip has role: "tooltip" and stable id. Tooltip always in DOM — show/hide via CSS class not DOM removal. Signal controls visibility class.

**Q42**

Create a Dioxus 0.7 skip navigation link. Visually hidden until focused. href: "#main-content". Matching id: "main-content" on main landmark. Correct Tailwind v4 sr-only + focus-visible classes.

**Q43**

Build a Dioxus 0.7 LiveSearch. Input has aria_autocomplete: "list", aria_controls pointing to results id, aria_expanded derived from whether results visible. Results has role: "listbox". Each result has role: "option" and aria_selected — results must be children of the listbox not siblings.

**Q44**

Create a Dioxus 0.7 DataTable with sortable columns. Each sortable th has aria_sort derived inline: "ascending", "descending", or "none". Track sort with one use_signal<(String, bool)>. Alternating row colors derived inline.

**Q45**

Build a Dioxus 0.7 AlertBanner. Takes variant: String prop. Match directly in class attribute: "info" → blue, "warning" → yellow, "error" → red, "success" → green. Container has role: "alert" and aria_labelledby pointing to heading id inside it.

**Q46**

Create a Dioxus 0.7 settings form. Fields: username, email, bio, notifications checkbox. Each field has label with r#for, input with id and aria_describedby pointing to hint id. Hints always in DOM. Errors conditional with role: "alert" and aria_labelledby. Submit uses prevent_default. One use_signal per field.

**Q47**

Build a Dioxus 0.7 ProgressTracker showing 4 steps. Current step tracked with use_signal<usize>. Each step has aria_current: "step" when active. Container has role: "list". Each step has role: "listitem". Completed steps have aria_label indicating completion.

**Q48**

Create a Dioxus 0.7 image gallery. Each image has descriptive alt text. Decorative dividers use aria_hidden: "true" (unquoted). Navigation buttons have aria_label. Current image indicator uses aria_current: "true". Track current index with use_signal<usize>.

**Q49**

Build a Dioxus 0.7 Tabs component without using primitives. Container has role: "tablist". Each tab button has role: "tab", aria_selected derived inline, aria_controls pointing to panel id. Each panel has role: "tabpanel", id, aria_labelledby. Only active panel rendered in DOM.

**Q50**

Create a Dioxus 0.7 SearchCombobox. Input has role: "combobox", aria_expanded derived inline, aria_autocomplete: "list", aria_controls pointing to listbox id. Listbox has role: "listbox". Each option has role: "option", aria_selected. Options are children of listbox.

---

## TIER 5 — use_resource and async (Q51–Q58, weight 1.5)

**Q51**

Fetch a list of posts from /api/posts using use_resource and reqwest. Three-arm match in RSX: None spinner with role: "status" and aria_label, Some(Err) error div with role: "alert" and aria_labelledby pointing to heading id, Some(Ok) list with stable keys. No .ok() wrapper.

**Q52**

Build a paginated list. use_resource reads a page signal inside the async closure. Prev/next buttons update the signal. Derive total page count inline. aria_label on both buttons. aria_disabled derived inline. Three-arm match only.

**Q53**

Create a category selector that fetches items per category via use_resource. Resource reads category signal inside the closure. Three-arm match in RSX. Category buttons styled with match-in-class. No secondary signals.

**Q54**

Build a UserProfile that fetches from /api/user/1 via use_resource. Loading shows skeleton. Error shows dismissible banner with role: "alert" and aria_labelledby. Success shows name, email, avatar initial derived inline. Three-arm match only. No .ok().

**Q55**

Create a real-time search via use_resource. Resource reads query signal inside closure. Three-arm match in RSX. Input has full ARIA autocomplete attributes. Results have role: "listbox" with role: "option" children. No secondary signals.

**Q56**

Build a use_resource that fetches data only when a use_signal<bool> is true. Show a placeholder when false. Three-arm match when resource is active. Trigger button toggles the signal. No secondary signals.

**Q57**

Create a Dioxus 0.7 component that uses use_resource with error retry. Three-arm match with Some(Err) showing a retry button that calls .restart() on the resource. Loading arm has role: "status". Success arm renders a list with stable keys.

**Q58**

Build a multi-resource component that fetches user data and their posts separately using two use_resource calls. Combine results inline in RSX — show loading if either is None, show error if either is Some(Err), show combined view when both are Some(Ok).

---

## TIER 6 — Hard Reasoning (Q59–Q68, weight 2.0)

Scoring: Think block 0–3, code 0–3. Combined 4+/6 = pass. Need 5/10 passes.

**Q59**

Build a Dioxus 0.7 TreeView for arbitrarily deep nested nodes. Each node has label: String and children: Vec<Node>. Track expanded state per node id in one use_signal<HashSet<u32>>. The <think> block must address: why self-referential recursion is problematic in Dioxus 0.7 and what render strategy avoids it. Full ARIA: role: "tree", role: "treeitem", aria_expanded, aria_level derived correctly per depth.

**Q60**

Build a Dioxus 0.7 optimistic UI todo list. Adding shows item immediately as pending. use_resource POST confirms or rejects. On failure remove item and show role: "alert". One use_signal<Vec<TodoItem>> where each has is_pending: bool. The <think> block must address: race condition between optimistic insert and async response, and key instability when removing items.

**Q61**

Create a Dioxus 0.7 virtualized list approximation for 10,000 items using windowed rendering. Track scroll offset with use_signal. Derive visible 20-item window inline. The <think> block must address: why true virtualization requires use_eval JS interop and the tradeoffs. Each item must have aria_posinset and aria_setsize reflecting full list position.

**Q62**

Design a Dioxus 0.7 ThemeProvider using use_context_provider. Deeply nested ThemedCard and ThemedButton consume via use_context — no prop drilling. The <think> block must address: what happens when use_context is called with no provider ancestor (it panics, does NOT return None), and how to safely guarantee provider existence.

**Q63**

Build a Dioxus 0.7 form wizard with 5 steps using context provider for shared state — no prop drilling, no global signals. Validate each step before advancing. The <think> block must address: how context differs from signals for shared mutable state, why Signal<FormState> wrapped in context is preferred over prop passing, and how validation errors persist across step navigation.

**Q64**

Create a Dioxus 0.7 component that implements debounced search using use_resource and use_signal. The resource only fires after 300ms of no input. The <think> block must address: why debouncing requires either JS interop via use_eval or a background task, and what the tradeoffs are between the two approaches in Dioxus 0.7.

**Q65**

Build a Dioxus 0.7 drag-and-drop list reordering component. Track item order with use_signal<Vec<usize>>. The <think> block must address: why native HTML5 drag events need careful handling in Dioxus RSX, how to use ondragstart, ondragover, ondrop event handlers, and what ARIA attributes make drag-and-drop accessible (aria_grabbed, aria_dropeffect).

**Q66**

Create a Dioxus 0.7 InfiniteScroll component that loads more items when the user scrolls near the bottom. The <think> block must address: why scroll detection requires use_eval for DOM access in Dioxus, how to communicate scroll events back to Rust via dioxus.send() and eval.recv(), and how to manage the loading state signal correctly to prevent duplicate fetches.

**Q67**

Build a Dioxus 0.7 component that uses WritableResultExt from Dioxus 0.7.4. Create a use_signal<Result<String, String>>. Use WritableResultExt methods to update only the Ok value. The <think> block must address: what WritableResultExt adds over manual match-and-set, when to use it vs direct .set(), and the ownership implications.

**Q68**

Design a Dioxus 0.7 WebSocketChat component using the 0.7.4 WebSocket Stream+Sink API. Track messages with use_signal<Vec<String>>. The <think> block must address: how use_resource integrates with the async WebSocket stream, how to handle reconnection, and why the message signal must be captured by value not reference in the async closure.

---

## TIER 7 — Dioxus Primitives + CSS Modules (Q69–Q80, weight 1.5)

**Q69**

Using dioxus-primitives, render a Checkbox. Import from dioxus_primitives::checkbox. Style with Tailwind v4: gray border unchecked, blue fill checked. Derive style inline from signal. Linked label via r#for/id. Fire on_checked_change updating use_signal<bool>. Do NOT manually add ARIA.

**Q70**

Using dioxus-primitives, build a modal dialog. Import Dialog, DialogTrigger, DialogContent, DialogTitle, DialogClose from dioxus_primitives::dialog. Style with Tailwind v4. Do NOT add role: "dialog" or aria_modal manually.

**Q71**

Using dioxus-primitives, build an Accordion with three items. Import from dioxus_primitives::accordion. Trigger gets full-width flex row with rotating chevron via Tailwind v4. Do NOT add aria_expanded manually.

**Q72**

Using dioxus-primitives, build Tabs with three tabs. Import from dioxus_primitives::tabs. Active tab gets blue underline via Tailwind v4. Do NOT add aria_selected or role: "tab" manually.

**Q73**

Using dioxus-primitives, build a Tooltip. Import from dioxus_primitives::tooltip. Trigger is a button. Content says "This feature is in beta." Style with Tailwind v4. Do NOT add role: "tooltip" or aria_describedby manually. Use Tooltip not TooltipRoot.

**Q74**

Using dioxus-primitives, build a Select for choosing a country. Import from dioxus_primitives::select. At least 3 SelectItem options. Track selected with use_signal<String> via on_value_change. Style with Tailwind v4. Do NOT add role: "listbox", role: "option", or aria_selected manually.

**Q75**

Using dioxus-primitives, build a RadioGroup for plan selection: "Free", "Pro", "Enterprise". Import from dioxus_primitives::radio_group. Use RadioGroupItem not RadioItem. Track with use_signal<String>. Style selected with blue ring. Do NOT add role: "radiogroup", role: "radio", or aria_checked manually.

**Q76**

Using dioxus-primitives, build a searchable combobox combining Select with a filter input. Import from dioxus_primitives::select. Filter query via use_signal<String>. Derive filtered list inline — no secondary signals. Filter input must have aria_label: "Search options". Do NOT add listbox ARIA manually.

**Q77**

Create a Dioxus 0.7 Card styled entirely with CSS modules. Use styles!() macro with correct first argument to load card.module.css. Apply STYLES.card, STYLES.title, STYLES.body. Include document::Link. Show companion card.module.css. No Tailwind classes.

**Q78**

Build a Dioxus 0.7 AlertDialog using dioxus-primitives Dialog styled with CSS modules. Use styles!() to load alert_dialog.module.css. Apply scoped classes to overlay, panel, title, description, action button. on_confirm: EventHandler<()> prop. Do NOT add role: "dialog" or aria_modal manually. Show companion CSS.

**Q79**

Using dioxus-primitives, build a full navigation menu. Import from dioxus_primitives::navigation_menu. Include at least 3 top-level items with dropdown content. Style with Tailwind v4. Do NOT manually add ARIA roles that the primitive manages.

**Q80**

Create a Dioxus 0.7 component that mixes dioxus-primitives Switch with CSS modules for the track and thumb styling. Import from dioxus_primitives::switch. Use styles!() for the custom styles. Track state with on_checked_change. Include linked label. Do NOT add role: "switch" or aria_checked manually.

---

## TIER 8 — GlobalSignal, i18n, Dark Mode (Q81–Q88, weight 1.5)

**Q81**

Create src/state.rs declaring two GlobalSignal statics: LANG for language ("en") and THEME for theme ("light"). Show correct write syntax using .write() not .set(). Show correct read syntax. Explain why .set() fails on statics in a comment.

**Q82**

Build a Dioxus 0.7 component that reads LANG from a GlobalSignal and resolves i18n strings before the rsx! block. Show let t_title = if LANG() == "vi" { "..." } else { "..." } pattern. Use {t_title} inside RSX. No secondary signals.

**Q83**

Create a Dioxus 0.7 App component that uses use_effect to watch THEME GlobalSignal and toggle .dark class on document.documentElement via document::eval. Show the correct eval string and how THEME is read inside the effect closure.

**Q84**

Build a Dioxus 0.7 LanguageToggle button. Reads LANG GlobalSignal. On click writes *LANG.write() = "vi" or *LANG.write() = "en" toggling between them. Includes aria_label derived inline from current language. No secondary signals.

**Q85**

Create a Dioxus 0.7 sticky navigation component that uses use_hook to set up a JS scroll listener. Use document::eval to inject the scroll listener. Use dioxus.send() to communicate scroll position back to Rust. Use eval.recv::<bool>() to receive is_scrolled. Update use_signal<bool> on receipt.

**Q86**

Build a complete Dioxus 0.7 MainNav with: GlobalSignal language toggle, GlobalSignal theme toggle, sticky scroll behavior via use_hook, mobile menu via use_signal<bool>. All interactive elements have aria_label. Focus-visible rings on all buttons.

**Q87**

Create a Dioxus 0.7 hero component with full EN/VI i18n. Resolve all strings via pre-rsx let bindings reading LANG GlobalSignal. Include h1, subtitle p, CTA button — all translated. Background SVG uses defs { pattern { } } structure with matching id. aria_hidden: "true" (unquoted) on decorative SVG.

**Q88**

Build a Dioxus 0.7 ThemeProvider pattern that does NOT use GlobalSignal. Instead use use_context_provider with a Signal<Theme> enum. Child components consume via use_context::<Signal<Theme>>(). Show why this panics without a provider and how to guarantee safety.

---

## TIER 9 — Static Content Navigator (Q89–Q94, weight 1.5)

**Q89**

Build a Dioxus 0.7 PostList that filters a hardcoded Vec<Post> using use_memo. One use_signal<String> for search query. Derive filtered list inline. Show count derived inline. Each Post has title, slug, tags. No secondary signals. WCAG: role: "status" on count.

**Q90**

Create a Dioxus 0.7 tag filter component. Hardcoded Vec<&str> of 8 tags. One use_signal<Option<&str>> for selected tag. Filter post list inline using use_memo. Active tag button gets different Tailwind class derived inline. Clear filter button when tag is selected.

**Q91**

Build a Dioxus 0.7 content navigator with two signals: use_signal<String> for search and use_signal<String> for sort ("newest" or "oldest"). Derive filtered AND sorted list using use_memo. Sort buttons update the sort signal. No secondary signals.

**Q92**

Create a Dioxus 0.7 NavIntent component that maps a use_signal<String> intent value to a filtered content view. Intent options: "latest", "older", "tutorials", "all". Use match in RSX to render different filtered views per intent. Buttons set intent signal directly. WCAG: aria_current: "true" on active intent button.

**Q93**

Build a Dioxus 0.7 PostCard component that takes a Post struct prop with title: String, slug: String, tags: Vec<String>, published_at: String. Render a card with title link, tag badges, and date. Link href derived from slug. Tag badges use aria_label. WCAG AAA contrast via semantic tokens.

**Q94**

Create a Dioxus 0.7 search results component. Takes query: String prop. Filters hardcoded posts inline. Shows "No results" state using rsx! {} empty pattern when empty. Shows count when results exist with role: "status". Results list uses stable keys on slug.

---

## TIER 10 — Dioxus 0.7.4 APIs (Q95–Q100, weight 2.0)

**Q95**

Demonstrate WritableResultExt from Dioxus 0.7.4. Create a use_signal<Result<UserData, String>>. Use WritableResultExt to update only the Ok variant without matching manually. Show the import path and at least two method calls. Explain in a comment when to prefer this over .set().

**Q96**

Build a Dioxus 0.7 component that uses use_context::<Theme>() correctly. Show use_context_provider in a parent. Show use_context::<Theme>() in a child. Include a comment explaining that use_context panics — does NOT return Option — if no provider exists in the ancestor tree. Show how to guarantee safety.

**Q97**

Create a Dioxus 0.7.4 WebSocketClient component using the new Stream+Sink WebSocket API. Connect to "wss://echo.example.com". Track messages with use_signal<Vec<String>>. Show send and receive. Handle connection errors in a role: "alert" banner.

**Q98**

Build a Dioxus 0.7 component demonstrating consume_context::<T>() vs use_context::<T>(). Show both in the same component. Explain the difference in a comment (both panic without provider, consume_context is the older name). Use a Theme enum as the context type.

**Q99**

Create a Dioxus 0.7 component that uses use_resource with the Dioxus 0.7.4 improved error handling. Fetch from /api/data. Three-arm match. In the Some(Err) arm use WritableResultExt on a separate error signal to track retry count. Retry button calls .restart() on the resource.

**Q100**

Build a complete Dioxus 0.7.4 BlogPost page component. Fetch post data via use_resource. Use WritableResultExt for optimistic like count updates. Track like state with use_signal<Result<u32, String>>. Full WCAG AAA: article landmark, heading hierarchy, like button with aria_pressed derived inline, aria_live: "polite" on like count.

---

## Publication Scorecard

| Tier | Questions | Weight | Max Points | Required |
|------|-----------|--------|------------|----------|
| T1 Fundamentals | Q1–12 | 1.0 | 12 | 10/12 |
| T2 RSX Syntax | Q13–24 | 1.0 | 12 | 10/12 |
| T3 Signal Hygiene | Q25–36 | 1.0 | 12 | 10/12 |
| T4 WCAG/ARIA | Q37–50 | 1.5 | 21 | 16/21 |
| T5 use_resource | Q51–58 | 1.5 | 12 | 9/12 |
| T6 Hard Reasoning | Q59–68 | 2.0 | 20 | 10/20 |
| T7 Primitives+CSS | Q69–80 | 1.5 | 18 | 13/18 |
| T8 GlobalSignal/i18n | Q81–88 | 1.5 | 12 | 9/12 |
| T9 Static Navigator | Q89–94 | 1.5 | 9 | 7/9 |
| T10 Dioxus 0.7.4 | Q95–100 | 2.0 | 12 | 9/12 |
| **Total** | **Q1–100** | | **140** | **103/140 (74%)** |

**v1.x threshold:** 74% (103/140)
**v2.0 threshold:** 85% (119/140)
