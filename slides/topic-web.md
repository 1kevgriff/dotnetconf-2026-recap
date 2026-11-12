---
theme: default
title: .NET Conf 2026 Recap - ASP.NET Core and Blazor
info: |
  ## .NET Conf 2026 Recap - ASP.NET Core and Blazor
  Kevin Griffin - Microsoft MVP
  ASP.NET Core and Blazor: highlights from Day 1 (2026-11-10) and Day 2 (2026-11-11), captured live.
author: Kevin Griffin
class: text-left
lineNumbers: false
drawings:
  persist: false
transition: fade
mdc: true
fonts:
  sans: Source Sans 3
  mono: JetBrains Mono
  provider: none
layout: "cover"
variant: "title"
image: "/cast-kevin.jpg"
---

# .NET Conf 2026 Recap

- ASP.NET Core and Blazor
- Kevin Griffin
- Microsoft MVP

<!--
- [title]
- Say: This is a .NET Conf 2026 recap on one topic: ASP.NET Core and Blazor. It pulls the highlights from Day 1 (2026-11-10) and Day 2 (2026-11-11), captured live from the stream.
- Sessions in this deck:
  - 01 From the keynote: Web (Day 1, 11:00 AM)
  - 02 Modern web development with ASP.NET Core & Blazor in .NET 11 (Day 1, 12:30 PM)
  - 03 Blazor Server in .NET 11: Fast, resilient, and scalable (Day 2, 1:31 PM)
- Every number on these slides came from a speaker or an on-screen slide. Experimental and preview items are marked as such.
- Source: dotnetconf.net/agenda; stream transcripts and screenshots from both days.
-->

---
layout: "cover"
variant: "bio"
transition: slide-up
image: "/kevin-griffin.png"
---

# Kevin Griffin

- Independent Consultant
- CTO, Shows On Sale
- Microsoft MVP
- consultwithgriff.com  ·  @1kevgriff

<!--
- [about me] 30 seconds max.
- Say: I'm Kevin Griffin: independent consultant, CTO at Shows On Sale, and a Microsoft MVP. Find me at consultwithgriff.com or @1kevgriff.
- Keep it short. Use only what is on the slide.
- Transition: I watched both main days live so you don't have to. Here's what shipped.
-->

---
layout: "session"
num: 1
time: "Day 1 · 11:00 AM"
speakers: "Scott Hanselman, Damian Edwards + guests"
---

# From the keynote: Web

<!--
- [Session 01 · part of the Day 1 keynote] 11:00 AM ET, 2026-11-10.
- Say: The Day 1 keynote was a one-hour tour of .NET 11. These slides are the keynote parts about ASP.NET Core and Blazor.
- Next slides: Unions end to end, async validation, built-in CSRF, more in ASP.NET Core 11.
-->

---
layout: "shot"
image: "/shots/112531.jpg"
time: "Day 1 · 11:25"
---

# Unions end to end

<!--
- System.Text.Json writes only the active case. No wrapper, no type field.
- OpenAPI 3.2: the union shows as anyOf
- Say: The C# union from Mads's demo works all the way through ASP.NET Core: in the API, in the JSON, in the OpenAPI document, and in Razor.
- Code: public union Resolution(RefundResolution, ReplacementResolution); Minimal APIs return the union directly.
- Verbatim (Roth): "we don't have to take all those properties and stick them on the same C-sharp class and then remember which combinations are valid."
- Verbatim: "There's no need for a union wrapper or any sort of type discriminator." .NET 11 uses OpenAPI 3.2.
- Blazor: a Razor component switches on the union cases and renders the matching UI.
- Why it matters: your API contract matches your domain model, with no hand-written discriminator code.
- Source: 11:24-11:26 ET, 20261110-112401.txt; shots 112431.jpg, 112531.jpg.
-->

---
layout: "shot"
image: "/shots/112649.jpg"
time: "Day 1 · 11:26"
---

# One async validation rule: Blazor and API

<!--
- AsyncValidationAttribute (InStock example)
- Blazor: spinner while the check runs
- API: out of stock returns 400
- Also new: IAsyncValidatableObject (Daniel Roth session, 12:46)
- Say: Async validation is new in .NET 11. One attribute checks inventory, and the same rule runs in the Blazor form and in the API.
- InStockAttribute derives from the new AsyncValidationAttribute. The normal DataAnnotationsValidator component runs async rules.
- EditContext exposes a validation-pending state, so the UI can show a spinner while the check runs.
- API result (verbatim): "we got 400. Sorry, that model's not currently available." In stock: "200 OK."
- Why it matters: no duplicate validation logic between front end and back end, even for checks that call a database or service.
- Source: 11:26-11:28 ET, 20261110-112604.txt; shot 112649.jpg.
-->

---
layout: "shot"
image: "/shots/112845.jpg"
time: "Day 1 · 11:28"
---

# CSRF protection, built in

<!--
- Uses Fetch Metadata headers (Sec-Fetch-Site)
- No antiforgery tokens
- Say: ASP.NET Core 11 blocks cross-site request forgery automatically, using headers the browser already sends.
- Demo: a page on the same host (localhost) but a different port posts to the app. That is same-site but not same-origin, so ASP.NET Core rejects it.
- The same request from the app itself shows same-origin and goes through.
- Verbatim (Roth): "It didn't have to do anything and it didn't have to mess around with anti-forgery tokens. So, it's secure and performant by default."
- Why it matters: one less thing to wire up, and no token round-trips.
- Source: 11:28-11:29 ET, 20261110-112800.txt; shot 112845.jpg.
-->

---
layout: "shot"
image: "/shots/112950.jpg"
time: "Day 1 · 11:29"
---

# More in ASP.NET Core 11

<!--
- Feature grid. Pick 1–2 to call out.
- Say: Dan said there are "tons of new features for web developers, for Blazor, minimal APIs, and SignalR." Here are the rest.
- Grid items: Virtualize (variable heights, scroll to item); QuickGrid state in the URL; async validation; OpenAPI 3.2 on by default with Server-Sent Events; TempData in SSR.
- More: circuit pause (server-triggered or on tab inactivity); relative navigation (NavigateTo and NavLink); SignalR auth refresh on live connections; Blazor WASM server (new lightweight Gateway host); localized validation.
- Why it matters: many small Blazor and API quality-of-life fixes ship with no migration work.
- Source: 11:29 ET, 20261110-112800.txt; shot 112950.jpg.
-->

---
layout: "session"
num: 2
time: "Day 1 · 12:30 PM"
speakers: "Daniel Roth"
---

# Modern web development with ASP.NET Core & Blazor in .NET 11

<!--
[Session 02 · Day 1]
- Say: Session 3 is Daniel Roth on ASP.NET Core and Blazor in .NET 11. His frame was trust: perform, protect, deliver.
- 12:30 PM ET. Speaker: Daniel Roth, principal product manager for ASP.NET Core and Blazor
- Verbatim close: "Trust to perform, trust to protect, and trust to deliver."
- Next slides: MSN perf on .NET 10, Kestrel bad-request cost, token-free CSRF, SignalR auth refresh, Toscano customer story, free MIT Blazor components, Virtualize, Razor tooling, Blazor + Aspire
- Also covered, not on a slide: C# unions in Minimal APIs and Blazor (OpenAPI 3.2 schemas), async validation (async validation attribute, IAsyncValidatableObject)
- Get started: get.net/11 (said on stream as "get.net slash 11")
- Why it matters: many of these gains come by upgrading, with little code change.
- Source: 12:30–12:58 ET, transcripts/20261110-123000.txt to 20261110-125801.txt
-->

---
layout: "shot"
image: "/shots/123125.jpg"
time: "Day 1 · 12:31"
---

# MSN feeds on .NET 10: 29% lower P95 GC pauses

<!--
- Say: Microsoft runs .NET at scale. The MSN, Edge, and Windows feeds team upgraded from .NET 8 to .NET 10 and got these numbers.
- Tens of billions of monthly page views. MSN, Edge, Windows feeds.
- .NET 8 → 10: 29% lower P95 GC pauses, 11% lower async plugin latency, 20% shorter thread-pool queues
- .NET powers Copilot, Teams, Bing, Azure, and Xbox; "real production workloads, not just framework benchmarks"
- Verbatim: "you don't need Microsoft's traffic volume to benefit from that investment."
- .NET 11 web stack: JIT and allocation work, faster JSON/strings/regex/HTTP, lower observability overhead; Blazor: smaller WebAssembly downloads, static SSR caching, pause idle server circuits
- "Many of these improvements come simply by upgrading."
- Why it matters: a runtime upgrade alone can cut GC pauses and latency.
- Source: 12:30–12:32 ET, transcripts/20261110-123000.txt and 20261110-123204.txt; shot /shots/123125.jpg
-->

---
layout: "shot"
image: "/shots/123244.jpg"
time: "Day 1 · 12:32"
---

# Kestrel: bad requests, ~30% cheaper to reject

<!--
- Say: Kestrel used to throw exceptions to reject malformed requests. In .NET 11 it returns an error result, so bad requests cost less.
- Malformed HTTP/1.1 requests: no more throw-and-propagate
- Returns an error result and uses pre-allocated response fragments
- ~30% higher bad-request throughput (single-core benchmark)
- "Cycles that are free for your normal website traffic"
- Why it matters: under junk or attack traffic, more CPU stays free for real users.
- Source: 12:32–12:34 ET, transcripts/20261110-123204.txt; shot /shots/123244.jpg
-->

---
layout: "shot"
image: "/shots/123422.jpg"
time: "Day 1 · 12:34"
---

# CSRF without tokens: ~4x form posts/sec

<!--
- Say: CSRF protection is now on by default with browser Fetch Metadata headers. No antiforgery tokens, and it is faster.
- Fetch Metadata (Sec-Fetch-Site), on by default
- No tokens to generate or validate
- ~4x requests/sec, ~65% less allocation per request vs antiforgery tokens
- Demo: no antiforgery code in Program.cs
- Q&A (13:00): falls back to Origin headers for older browsers; antiforgery middleware still composes if you want both
- Demo: a form post from a different port (different origin) got 400 Bad Request; the same post from the app passed
- Why it matters: less security plumbing and better throughput for form posts.
- Source: 12:34–12:37 ET, transcripts/20261110-123402.txt and 20261110-123600.txt; Q&A transcripts/20261110-130000.txt; shot /shots/123422.jpg
-->

---
layout: "shot"
image: "/shots/123740.jpg"
time: "Day 1 · 12:37"
---

# SignalR: refresh auth without reconnecting

<!--
- Say: SignalR and Blazor Server can now refresh auth on a live connection. Permission changes show up without a reconnect.
- Long-lived connections can outlive their credentials
- .NET 11: SignalR re-authenticates with fresh tokens on the same connection
- Blazor Server uses the same machinery to keep auth state current
- Opt in: enable authentication refresh on SignalR hub options; Blazor: withAuthenticationRefresh
- Demo (12:39): admin revokes refund permission, open page updates live, typed form data kept
- Caveat: refresh runs on an interval, when the token is about to expire. Not instant.
- Option: close on authentication expiration closes the connection if the refresh fails
- In the demo, Dan shortened the refresh time so it was easy to see
- Why it matters: long-lived Blazor Server sessions no longer keep stale permissions.
- Source: 12:37–12:41 ET, transcripts/20261110-123600.txt to 20261110-124002.txt; shot /shots/123740.jpg
-->

---
layout: "shot"
image: "/shots/124137.jpg"
time: "Day 1 · 12:41"
---

# 5 developers, 11M page views a year

<!--
- Say: Toscano Digital runs a public real-estate portal with five developers. That is about 11 million page views a year.
- Toscano Digital: real-estate portal + Blazor CRM
- 4.6M sessions/year (speaker rounded to "about 5 million")
- Customer-reported figures
- Slide figures: 5 developers, 4.6M sessions/year, 11M page views/year
- Requirements: search discoverability, mobile performance, rich interactivity. They combined .NET and Blazor rendering strategies.
- Verbatim: "They were able to be more productive by leveraging C Sharp full stack"
- Case study on the slide: dotnet.microsoft.com/platform/customers/toscano
- Why it matters: a small team can cover public web and internal CRM with one C# stack.
- Source: 12:41–12:42 ET, transcripts/20261110-124002.txt and 20261110-124200.txt; shot /shots/124137.jpg
-->

---
layout: "shot"
image: "/shots/124215.jpg"
time: "Day 1 · 12:42"
---

# Free, MIT-licensed Blazor components

<!--
- Say: Infragistics and Syncfusion released free, MIT-licensed Blazor component sets, and both contributed code to Blazor.
- Infragistics: 50+ Ignite UI for Blazor components
- Syncfusion Toolkit for Blazor
- MIT, free for commercial use. Separate from their paid suites.
- Both contributed to Blazor itself: new analyzers (Infragistics), framework + scaffolding (Syncfusion)
- Infragistics set includes Grid Lite, inputs, navigation, layouts; Syncfusion toolkit has charts, inputs, calendars, dialogs
- Dan used Grid Lite and a Syncfusion chart in his final demo
- Why it matters: you get production-grade components at no cost, including commercial use.
- Source: 12:42 ET, transcripts/20261110-124200.txt; demo use transcripts/20261110-125604.txt; shot /shots/124215.jpg
-->

---
layout: "shot"
image: "/shots/124850.jpg"
time: "Day 1 · 12:48"
---

# Blazor Virtualize: variable-height rows

<!--
- Say: Blazor Virtualize now supports rows of different heights, anchor modes, and jump-to-item.
- Rows grow with their content
- Anchor modes: pin to start, end, both, or neither
- ScrollToItemAsync(index); stable position as items change
- Demo: ~10,000 items scroll smoothly, jump to item 5,000
- Anchor to end: the view follows new items only when you are at the bottom; mid-list, the position stays stable
- Why it matters: chat logs, feeds, and queues no longer need a custom virtual list.
- Source: 12:48–12:51 ET, transcripts/20261110-124800.txt and 20261110-125003.txt; shot /shots/124850.jpg
-->

---
layout: "shot"
image: "/shots/125133.jpg"
time: "Day 1 · 12:51"
---

# Razor tooling: rename across C# and Razor

<!--
- Say: Razor tooling caught up with C#: cross-language refactors, EditorConfig formatting, and Emmet in Visual Studio.
- Cross-language rename, faster Hot Reload
- EditorConfig C# style in .razor files
- ~/ asset paths instead of @Assets["..."]
- Emmet support
- Also: remove and sort using directives in .razor files
- Works in Visual Studio and VS Code
- Why it matters: Razor files get the same editor quality as .cs files.
- Source: 12:51–12:54 ET, transcripts/20261110-125003.txt and 20261110-125200.txt; shot /shots/125133.jpg
-->

---
layout: "shot"
image: "/shots/125457.jpg"
time: "Day 1 · 12:54"
---

# Blazor + Aspire: debug browser and backend together

<!--
- Say: Aspire now runs and debugs Blazor WebAssembly with the backend, and .NET code can run on a Web Worker.
- Aspire: dashboard, service discovery, WebAssembly debugging
- New Blazor Gateway: one host for dev and prod, static assets, API proxy
- Web Workers: run .NET off the UI thread
- Also: Entra ID auth scaffolding (dotnet scaffold or VS); ASP.NET Core + Blazor plugins at github.com/dotnet/skills
- Demo (12:57): analysis on the UI thread freezes the page; on a Web Worker it stays responsive. "Debug in Browser" button in the Aspire dashboard.
- Caveat: the demo ran Aspire 17 daily builds
- New project templates: a client defaults project (Aspire setup in the WebAssembly app) and a worker project
- Debug tip (Q&A): use the dashboard's debug gesture; the browser Aspire opens at launch is not configured to debug WebAssembly
- Why it matters: full-stack Blazor WebAssembly debugging and a responsive UI under CPU load.
- Source: 12:54–13:00 ET, transcripts/20261110-125402.txt to 20261110-130000.txt; shot /shots/125457.jpg
-->

---
layout: "session"
num: 3
time: "Day 2 · 1:31 PM"
speakers: "Daniel Roth"
---

# Blazor Server in .NET 11: Fast, resilient, and scalable

<!--
- [Session 03 · Day 2] Daniel Roth. Started about 1:31 PM ET.
- His frame: render on the server to "deliver more with less": faster loads (HTML ready to display), logic close to data, efficient requests (complete them, cache public content). Slide "Render on the server: Deliver more with less" (shot 20261111/133141).
- Blazor modes, his words: static SSR renders HTML "and then completes the HTTP request. There's no persistent connection." Interactive server keeps state in "a circuit" over "a persistent real-time connection". WebAssembly for client-side work and offline; it can be pre-rendered too.
- Source: 13:31-13:33 ET, transcripts 20261111-133001 and 20261111-133203; dotnetconf.net/agenda (1:30 PM ET).
-->

---
layout: "shot"
image: "/shots/day2/133353.jpg"
time: "Day 2 · 13:33"
---

# Static SSR in .NET 11: dynamic pages, no circuit

<!--
- Say: .NET 11 makes static server-side rendering much more capable. You get sortable grids, client validation, state across requests, and caching, all without a live connection.
- On screen, "Static SSR: more capable in .NET 11", NEW items:
  - Smooth navigation: QuickGrid sort and page links (on top of enhanced navigation).
  - Immediate feedback: client-side validation (on top of enhanced forms).
  - State across requests: one-time TempData messages; continuing HTTP session.
  - Cache safe output: CacheView (a public region); output cache (a public response).
  - Footer: "Dynamic server-rendered experiences, without a live component tree."
- Demo (13:38), a care site all in static SSR:
  - QuickGrid code "looks exactly the same"; the page wraps it in the new CacheView component, with vary-by on the grid's query string parameters and about a 2-minute expiration.
  - A returns policy page uses the standard output cache attribute (whole HTTP response). Dan: CacheView caches "the component instances and also put them in memory or use the hybrid cache if one is configured".
  - A static support form shows validation feedback right away: "we're getting client-side validation, even though this is not an interactively rendered form ... in .NET 11, we added support for client-side validation".
- Why it matters: (Inference) many pages that needed interactive Blazor (and a circuit per user) can now be static SSR, with no server state held per user.
- Source: 13:33-13:39 ET, transcripts 20261111-133203 and 20261111-133804; slide shot 20261111/133353.
-->

---
layout: "shot"
image: "/shots/day2/134926.jpg"
time: "Day 2 · 13:49"
---

# Blazor circuits survive eviction and planned shutdowns

<!--
- Say: Blazor Server state now survives two kinds of interruption: a lost connection, and a planned server shutdown. New in .NET 11: you can ask a circuit to pause before you shut down.
- Connection loss, Dan (13:46): the server keeps a disconnected circuit in memory for a while, but "before it evicts the circuit, it will persist it. And if the components have been set up with persistent state, then that state can be reused to then resume that circuit later with a new circuit."
- Demo (13:48): he cut the network in browser dev tools. Aspire metrics went to "zero active circuits" (eviction shortened from the normal two minutes for the demo). Back online, the form state (delivery address, choices) came back: "none of that was lost because all of it got persisted."
- Planned shutdown, NEW IN .NET 11 (slide "Ask a circuit to pause"): `var accepted = await circuit.RequestCircuitPauseAsync(ct);` A CircuitHandler gives your app access to circuits; "Wait for pause completion within a shutdown budget."
- Dan: the paused state "can actually be stored client side instead of storing it on the server". And "an accepted request to pause the circuit does not mean the circuit is actually fully paused yet", so allow a short delay.
- Shutdown demo (13:50): he asked all circuits to pause, the app stopped ("It's not actually even running anymore"), then restarted; the paused clients reconnected with their state.
- Why it matters: deploys and node replacements no longer have to wipe in-progress user work in Blazor Server apps.
- Source: 13:46-13:52 ET, transcripts 20261111-134601, 20261111-134801 and 20261111-135002; slide "Ask a circuit to pause" (shot 20261111/134926).
-->

---
layout: "shot"
image: "/shots/day2/135237.jpg"
time: "Day 2 · 13:52"
---

# Auto Pause: hidden tab → circuit released → state back on return

<!--
- Say: New in .NET 11, Auto Pause frees the server circuit when a user's tab is hidden, and resumes it with saved state when the tab comes back. It is opt-in: one package and one line of config.
- On screen, "Auto Pause: opt in, set the policy / Release eligible circuits when a browser tab is hidden":
  - `dotnet add package Microsoft.AspNetCore.Components.Server.AutoPause`
  - `app.MapRazorComponents<App>().AddInteractiveServerRenderMode().WithBrowserOptions(options => options.AddAutoPause(pause => pause.HiddenDelay = TimeSpan.FromSeconds(8)));`
  - "Default: 2 minutes | Demo: 8 seconds | Selected state uses [PersistentState]."
- Dan (13:52): an idle circuit "just stays on the server and uses server resources without helping them. In .NET 11, we added a new auto-pause feature that can release eligible circuits". When the user returns, "their persisted pause circuit can be resumed ... without even noticing the interruption."
- Demo: minimized the tab; after about 8 s the active circuit count dropped (it "automatically got paused"); restoring the tab made a new circuit "and again we didn't lose any of our state".
- Why it matters: Blazor Server's main scaling cost (one circuit per open tab) drops for users who leave tabs open in the background.
- Source: 13:52-13:54 ET, transcript 20261111-135202; slide shot 20261111/135237.
-->

---
layout: "statement"
---

Start with static SSR. Add interactive server where needed. WebAssembly for compute and offline.

<!--
- Say: Dan Roth's advice for a fast, scalable Blazor app in .NET 11: static SSR first, then interactive server, then WebAssembly, and set the render mode per part of the app.
- Dan (13:56): "you'll start first with static server side rendering. That's your bread and butter. You download almost nothing to the browser". Then "if you feel like you have an experience that really requires additional interactivity, that's when I would start flipping on interactive server rendering". WebAssembly when you need to be "heavy on compute", "offline scenarios or UI interactions that are very low latency".
- "different parts of your app might have different characteristics ... you can set up the render modes for each part of your app".
- Where paused-circuit state goes (13:54): no browser connection (eviction after a disconnect) → on the server, in-memory cache by default, or HybridCache if enabled, so it can scale out. With a connection (graceful shutdown, Auto Pause) → "persist down to the client ... nicely protected", in the browser's local storage.
- On Aspire: "I would never build another ASP.NET Core Blazor app without wiring up Aspire." The demos used the Aspire dashboard for circuit metrics. For Blazor WebAssembly apps in Aspire (work with the Aspire team, shown on Day 1): "There's now a gesture to debug in browser in the Aspire dashboard."
- Scale baseline (Q&A, 13:59): "We have done very basic load balancing tests with Blazor server where it's like a single VM ... you can easily get tens of thousands of concurrent users on like a single simple VM on Azure as a baseline for Blazor server performance. And that's without doing a lot of the other tricks that I'm showing you." No exact numbers or VM size were given.
- Download: "Go ahead and download .NET 11 at get.net slash 11" (Dan, 13:54). Say: get.net/11.
- Why it matters: a clear default for new Blazor apps, with less server state per user.
- Source: 13:54-13:59 ET, transcripts 20261111-135402, 20261111-135602 and 20261111-135802.
-->

---
layout: "cover"
variant: "thanks"
image: "/kevin-griffin.png"
---

# Let's keep talking.

- consultwithgriff.com
- X · LinkedIn · GitHub: @1kevgriff
- Bluesky: @consultwithgriff.com

<!--
[thanks] Leave this up through Q&A.
-->
