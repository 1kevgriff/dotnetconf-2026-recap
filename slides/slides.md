---
theme: default
title: .NET Conf 2026 Recap
info: |
  ## .NET Conf 2026 Recap
  Kevin Griffin - Microsoft MVP
  Day 1 highlights, captured live from the stream.
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

- Day 1 highlights
- Kevin Griffin
- Microsoft MVP

<!--
[title]
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
[about me] 30 seconds max.
-->

---
layout: "session"
num: 1
time: "11:00 AM"
speakers: "Scott Hanselman, Damian Edwards + guests"
---

# Keynote: .NET 11 ships

<!--
[Session 1 · Keynote] Scott Hanselman, Damian Edwards, Chet Husk, Daniel Roth, Gerald Versluis, Luis Quintanilla, Wendy Breiding, Drew Noakes.
-->

---
layout: "shot"
image: "/shots/110905.jpg"
time: "11:09"
---

# .NET 11 is GA

<!--
- Released today. get.dot.net
- Damian Edwards: "five eras, one platform" (Windows, Web, Mobile, Cloud, AI)
-->

---
layout: "shot"
image: "/shots/110459.jpg"
time: "11:04"
---

# 2002 homework OS, running on .NET 11

<!--
- Hanselman's TinyOS from .NET 1 days, updated and running on .NET 11
- The point: .NET code is durable
-->

---
layout: "shot"
image: "/shots/110920.jpg"
time: "11:09"
---

# C# 15

<!--
- Unions, closed hierarchies, collection arguments
- Labeled break, extension indexers
- Memory safety preview
-->

---
layout: "shot"
image: "/shots/111254.jpg"
time: "11:12"
---

# Unions: add a case, every switch lights up

<!--
- union Pet(Dog, Cat, Bird, Hamster)
- Add Hamster: every non-exhaustive switch is flagged
-->

---
layout: "shot"
image: "/shots/111728.jpg"
time: "11:17"
---

# .NET CLI on Native AOT: 66–75% faster startup

<!--
- Chet Husk: CLI usage about 3x in the past year
- File-based apps can #include other .cs files
- dotnet run device prompts, dotnetup installer
-->

---
layout: "shot"
image: "/shots/111823.jpg"
time: "11:18"
---

# MSBuild `-mt`: 37% faster incremental builds

<!--
- Multithreaded MSBuild
- Warm incremental build on OrchardCore
-->

---
layout: "shot"
image: "/shots/112046.jpg"
time: "11:20"
---

# Runtime async: 0 bytes allocated

<!--
- No state machines, no ValueTask needed
- 0 B per op vs 216–504 B with state machines
- Default in .NET 12
-->

---
layout: "shot"
image: "/shots/112220.jpg"
time: "11:22"
---

# Memory safety v2: the Rust/Swift model, stricter

<!--
- Unsafe is off by default
- An unmarked unsafe call is an error
- Preview in .NET 11, GA in .NET 12
-->

---
layout: "section"
kicker: "ASP.NET Core 11"
---

# Web

<!--
[Daniel Roth] ASP.NET Core and Blazor.
-->

---
layout: "shot"
image: "/shots/112531.jpg"
time: "11:25"
---

# Unions end to end

<!--
- System.Text.Json writes only the active case. No wrapper, no type field.
- OpenAPI 3.2: the union shows as anyOf
-->

---
layout: "shot"
image: "/shots/112649.jpg"
time: "11:26"
---

# One async validation rule: Blazor and API

<!--
- AsyncValidationAttribute (InStock example)
- Blazor: spinner while the check runs
- API: out of stock returns 400
- Also new: IAsyncValidatableObject (Daniel Roth session, 12:46)
-->

---
layout: "shot"
image: "/shots/112845.jpg"
time: "11:28"
---

# CSRF protection, built in

<!--
- Uses Fetch Metadata headers (Sec-Fetch-Site)
- No antiforgery tokens
-->

---
layout: "shot"
image: "/shots/112950.jpg"
time: "11:29"
---

# More in ASP.NET Core 11

<!--
- Feature grid. Pick 1–2 to call out.
-->

---
layout: "section"
kicker: ".NET MAUI"
---

# Mobile

<!--
[Gerald Versluis] .NET MAUI.
-->

---
layout: "statement"
---

1,600 PRs a month. ~80% by Copilot.

<!--
- MAUI team PR volume, about 4x what it was
- 11:30 ET
-->

---
layout: "shot"
image: "/shots/113143.jpg"
time: "11:31"
---

# MAUI 11: one runtime, more platforms

<!--
- CoreCLR everywhere: Android, iOS, Mac Catalyst
- Native AOT: 2.4x faster startup, 14% smaller on Android
- Linux + WebAssembly via Avalonia (preview)
- Team ships 1,600+ PRs/month, ~80% by Copilot
-->

---
layout: "shot"
image: "/shots/113240.jpg"
time: "11:32"
---

# MAUI 11: the paper cuts, fixed

<!--
- Passkeys, Material 3, long press, tab/toolbar badges
- C# UI template: dotnet new maui --ui csharp
- Fixed with Copilot. DevFlow lets agents drive your app.
- MAUI session (14:46): Material 3 on Android = set one property in your csproj
-->

---
layout: "shot"
image: "/shots/113401.jpg"
time: "11:34"
---

# The .NET Conf app: open source, built with agents

<!--
- github.com/jfversluis/dotnetconf-app
- In the stores. Followed through every MAUI session this week.
-->

---
layout: "section"
kicker: "Modernization + AI"
---

# AI

<!--
[Luis Quintanilla] Modernization and AI.
-->

---
layout: "shot"
image: "/shots/113638.jpg"
time: "11:36"
---

# Modernize: 155x faster, 8 servers to 1

<!--
- Ateleris / FHNW: 155x faster, 8 servers to 1
- Intune: weeks saved with AI-assisted migration
- Windows 365 runs 100+ .NET microservices
-->

---
layout: "shot"
image: "/shots/113851.jpg"
time: "11:38"
---

# Windows 365: clone, F5, 100+ services

<!--
- Aspire AppHost composes 100+ microservices locally
- Reliability first: readiness checks, same tooling on dev, CI, build
- Then agentic AI on top
-->

---
layout: "shot"
image: "/shots/114038.jpg"
time: "11:40"
---

# Agents in a box: C# sets the rules

<!--
- Check, plan, fix, validate, learn
- One repo at a time, same test gate as human PRs
- Humans approve every PR
- Quote: "Passing tests is not the same as approving the change."
-->

---
layout: "shot"
image: "/shots/114148.jpg"
time: "11:41"
---

# .NET AI: 170M+ downloads

<!--
- Shared foundations: Microsoft.Extensions.AI, VectorData, DataIngestion (preview)
- Agent Framework, MCP C# SDK, OpenAI and Anthropic SDKs, OllamaSharp
-->

---
layout: "shot"
image: "/shots/114351.jpg"
time: "11:43"
---

# Llama on Windows: local models, built on .NET

<!--
- Hugging Face + llama.cpp teams. .NET 10 + WinUI 3 tray app.
- Open source, free at llama.app, in the Microsoft Store
- Also: Jellyfin semantic search, RoutingChatClient routes local vs cloud models
-->

---
layout: "shot"
image: "/shots/114545.jpg"
time: "11:45"
---

# What's new in .NET + AI

<!--
- Official OpenAI and Anthropic SDK integrations with MEAI
- DocumentExtractionClient, RoutingChatClient (experimental)
- OpenAI Decisions API: probabilities and scores, not chat
- AG-UI + Blazor AI Components (experimental)
- MCP C# SDK 2.0
- Caution: most are experimental. The stream slide said "DRAFT: confirm document-extraction package availability."
-->

---
layout: "section"
kicker: "Agentic development"
---

# Agents

<!--
[Wendy Breiding] Agentic development.
-->

---
layout: "shot"
image: "/shots/114707.jpg"
time: "11:47"
---

# Copilot app: fix a race condition

<!--
- Prompt: two people reserve the last RSVP spot, only one gets in
- Reproduced with a file-based app
- Copilot picks the model, loads a C# expert skill, uses LSP code search
-->

---
layout: "shot"
image: "/shots/114845.jpg"
time: "11:48"
---

# dotnet/skills: −41% tokens, −73% time

<!--
- github.com/dotnet/skills, eval dashboard at dotnet.github.io/skills
- csharp-expert skill on Claude Sonnet 5: -41% tokens, -73% time
- Roslyn as an agent tool: up to 50% less memory
-->

---
layout: "section"
kicker: "Next-gen inner loop"
---

# Faster, by doing less

<!--
[Drew Noakes] Next-gen inner loop. 11:50 ET.
- Copilot's RSVP race fix verified on stage
-->

---
layout: "statement"
---

Your machine has company.

<!--
- With agents running, dev tools can't own the whole machine
- C# Dev Kit 11 re-architected for performance
-->

---
layout: "shot"
image: "/shots/115215.jpg"
time: "11:52"
---

# C# Dev Kit 11: incremental build 36s → 2s

<!--
- ~77% lower workspace load times
- 80%+ less server memory: Roslyn repo 2 GB → ~300 MB
- 36s → 2s incremental build on Aspire's 407 projects
- Pre-release channel today, stable "really soon"
- Agents warm the build for your other tools
-->

---
layout: "section"
kicker: "Keynote close"
---

# 4 days. 60+ sessions.

<!--
[Kathy Sullivan, Maddy Montaquila] 11:54 ET.
- Ask the team live: dotnetconfquestions.com
-->

---
layout: "shot"
image: "/shots/115537.jpg"
time: "11:55"
---

# Microsoft builds with .NET too

<!--
- Copilot, Teams, Bing, Xbox, Azure, Exchange Online, Windows 365, Intune
- aka.ms/dotnet-developer-stories
-->

---
layout: "shot"
image: "/shots/115635.jpg"
time: "11:56"
---

# Download .NET 11: get.dot.net

<!--
- winget and other installers "soon"
-->

---
layout: "session"
num: 2
time: "12:00 PM"
speakers: "Mads Torgersen, Dustin Campbell"
---

# What's new in C#

<!--
[Session 2]
-->

---
layout: "statement"
---

Unions: 18 years in the making.

<!--
- 12:00 ET. Mads: "we were talking about it ... like 18 years ago"
- C# version = .NET version + 4, so C# 15
- Demo: Dog, Cat, Bird, Shark from libraries you don't own
-->

---
layout: "shot"
image: "/shots/120317.jpg"
time: "12:03"
---

# Before: `object`, and a switch that's never exhaustive

<!--
- List<object> accepts anything, so the switch warns CS8509
- Fix: union Pet(Dog, Cat, Bird), then List<Pet>. A Shark no longer fits.
-->

---
layout: "shot"
image: "/shots/120500.jpg"
time: "12:05"
---

# After: Shark is a compile error

<!--
- Case types convert implicitly to the union
- Remove the Shark arm: the switch is exhaustive, no discard needed
- Make a case nullable (Cat?) and you must add a null arm
-->

---
layout: "shot"
image: "/shots/120737.jpg"
time: "12:07"
---

# Unions are real types

<!--
- Generic type parameters, function members (`this switch`)
- No extra state: the value inside is the state
- Case types: any type convertible to object, incl. type parameters
- Default union is a struct. Add [Union] to any class/struct to roll your own; the compiler lists what's missing (e.g. a Value property).
- Under the hood: an object? Value plus one constructor per case type. Conversion calls the constructor; pattern matching reads Value.
- Hand-write a [Union] (IUnion) to avoid boxing value types, or to adapt an existing union-like type.
-->

---
layout: "shot"
image: "/shots/121715.jpg"
time: "12:17"
---

# `closed`: only your assembly can inherit

<!--
- Setup: public abstract Operation, another project adds EvilAdd, so no exhaustive switch
- `closed` makes the class implicitly abstract
- Subclasses in other assemblies are errors
- The switch is exhaustive again
-->

---
layout: "default"
codeSize: "22"
---

# Collection expressions take constructor args

```csharp
// before
var tags = new HashSet<string>(StringComparer.OrdinalIgnoreCase) { "one", "two" };

// C# 15
HashSet<string> tags = [with(StringComparer.OrdinalIgnoreCase), "one", "two"];
```

<!--
- 12:20 ET. with(...) passes constructor args: a comparer, a capacity
- Ctrl+. in the IDE offers the fix
- Screenshot: /shots/122000.jpg (not shown)
-->

---
layout: "default"
codeSize: "22"
---

# Labeled `break` and `continue`

```csharp
outer: for (int i = 0; i < 19; i++)
{
    for (int j = 0; j < 23; j++)
    {
        if ((i + j) % 2 == 0)
        {
            break outer;
        }
    }
}
```

<!--
- 12:21 ET. Replaces the "am I done yet" flag variable
- Works with continue too
- IDE refactoring: "use labeled jump statement"
-->

---
layout: "shot"
image: "/shots/122230.jpg"
time: "12:22"
---

# Extension indexers

<!--
- Index into types you don't own
- Builds on C# 14 extension blocks (properties came first)
- The extension block syntax scales to new member kinds
- Wrap-up (12:24): memory safety preview lets you mark your own APIs unsafe and track it transitively; async is "not different, just faster" with runtime async
-->

---
layout: "statement"
---

`closed` for your hierarchy. `union` for types you don't own.

<!--
- 12:26 ET Q&A
- closed: the list is your direct descendants
- union: types not in a hierarchy, or you don't control (e.g. data over the wire)
- Generated unions are structs, so implicitly sealed
- System.Text.Json supports unions (some cases still need attributes)
- No new runtime needed: older consumers (e.g. .NET Framework 4.8) read .Value, without union pattern matching
-->

---
layout: "session"
num: 3
time: "12:30 PM"
speakers: "Daniel Roth"
---

# Modern web development with ASP.NET Core & Blazor in .NET 11

<!--
[Session 3]
-->

---
layout: "shot"
image: "/shots/123125.jpg"
time: "12:31"
---

# MSN feeds on .NET 10: 29% lower P95 GC pauses

<!--
- Tens of billions of monthly page views. MSN, Edge, Windows feeds.
- .NET 8 → 10: 29% lower P95 GC pauses, 11% lower async plugin latency, 20% shorter thread-pool queues
-->

---
layout: "shot"
image: "/shots/123244.jpg"
time: "12:32"
---

# Kestrel: bad requests, ~30% cheaper to reject

<!--
- Malformed HTTP/1.1 requests: no more throw-and-propagate
- Returns an error result and uses pre-allocated response fragments
- ~30% higher bad-request throughput (single-core benchmark)
- "Cycles that are free for your normal website traffic"
-->

---
layout: "shot"
image: "/shots/123422.jpg"
time: "12:34"
---

# CSRF without tokens: ~4x form posts/sec

<!--
- Fetch Metadata (Sec-Fetch-Site), on by default
- No tokens to generate or validate
- ~4x requests/sec, ~65% less allocation per request vs antiforgery tokens
- Demo: no antiforgery code in Program.cs
- Q&A (13:00): falls back to Origin headers for older browsers; antiforgery middleware still composes if you want both
-->

---
layout: "shot"
image: "/shots/123740.jpg"
time: "12:37"
---

# SignalR: refresh auth without reconnecting

<!--
- Long-lived connections can outlive their credentials
- .NET 11: SignalR re-authenticates with fresh tokens on the same connection
- Blazor Server uses the same machinery to keep auth state current
- Opt in: enable authentication refresh on SignalR hub options; Blazor: withAuthenticationRefresh
- Demo (12:39): admin revokes refund permission, open page updates live, typed form data kept
- Caveat: refresh runs on an interval, when the token is about to expire. Not instant.
-->

---
layout: "shot"
image: "/shots/124137.jpg"
time: "12:41"
---

# 5 developers, 11M page views a year

<!--
- Toscano Digital: real-estate portal + Blazor CRM
- 4.6M sessions/year (speaker rounded to "about 5 million")
- Customer-reported figures
-->

---
layout: "shot"
image: "/shots/124215.jpg"
time: "12:42"
---

# Free, MIT-licensed Blazor components

<!--
- Infragistics: 50+ Ignite UI for Blazor components
- Syncfusion Toolkit for Blazor
- MIT, free for commercial use. Separate from their paid suites.
- Both contributed to Blazor itself: new analyzers (Infragistics), framework + scaffolding (Syncfusion)
-->

---
layout: "shot"
image: "/shots/124850.jpg"
time: "12:48"
---

# Blazor Virtualize: variable-height rows

<!--
- Rows grow with their content
- Anchor modes: pin to start, end, both, or neither
- ScrollToItemAsync(index); stable position as items change
- Demo: ~10,000 items scroll smoothly, jump to item 5,000
-->

---
layout: "shot"
image: "/shots/125133.jpg"
time: "12:51"
---

# Razor tooling: rename across C# and Razor

<!--
- Cross-language rename, faster Hot Reload
- EditorConfig C# style in .razor files
- ~/ asset paths instead of @Assets["..."]
- Emmet support
-->

---
layout: "shot"
image: "/shots/125457.jpg"
time: "12:54"
---

# Blazor + Aspire: debug browser and backend together

<!--
- Aspire: dashboard, service discovery, WebAssembly debugging
- New Blazor Gateway: one host for dev and prod, static assets, API proxy
- Web Workers: run .NET off the UI thread
- Also: Entra ID auth scaffolding (dotnet scaffold or VS); ASP.NET Core + Blazor plugins at github.com/dotnet/skills
- Demo (12:57): analysis on the UI thread freezes the page; on a Web Worker it stays responsive. "Debug in Browser" button in the Aspire dashboard.
- Caveat: the demo ran Aspire 17 daily builds
-->

---
layout: "session"
num: 4
time: "1:00 PM"
speakers: "Chet Husk"
---

# Moving `dotnet` Ahead (of Time)!

<!--
[Session 4]
-->

---
layout: "shot"
image: "/shots/130256.jpg"
time: "13:02"
---

# `dotnet --version`: 118 ms → 33 ms

<!--
- Native AOT CLI vs managed, macOS arm64
- tool list --local: 121 → 32 ms; user-secrets list: 142 → 54 ms
- "Billions and billions of commands" run on the CLI every month
- Compounds (13:05 chart): 3-command SDK check 374 → 118 ms (−69%); tool list + run 297 → 110 ms (−63%)
- AOT now covers core diagnostics, solution commands, most tool management
- Next: build commands, tool install/restore, dotnet new
- Twist: the CLI is a Native AOT library; `dotnet` itself is the native muxer
-->

---
layout: "shot"
image: "/shots/130903.jpg"
time: "13:09"
---

# The CLI is a library now

<!--
- Native `dotnet` muxer picks the SDK, loads the SDK's Native AOT library
- Eligible commands run native: no CoreCLR startup
- Everything else falls back in-process to the managed CLI (hostfxr starts CoreCLR)
-->

---
layout: "shot"
image: "/shots/131100.jpg"
time: "13:11"
---

# Going AOT: what had to change

<!--
- Reflection discovery → known types, generated metadata (incl. load-bearing Assembly.Location)
- Runtime codegen → static code paths
- Dynamic deps → accurate annotations, reachable-code tests
- "Sometimes this is entire rewrites, which sucks, but it's not super frequent." Mostly annotations.
- Gotcha (13:12): a Native AOT library has no meaningful base directory (it points at the host), so the SDK needed an explicit "SDK root"
- Partners (13:14): NuGet made its JSON reading/writing AOT-capable; early experiments with MSBuild evaluation in AOT. Approach: "strangler fig" the CLI.
-->

---
layout: "statement"
---

No free lunch: AOT trades size for speed.

<!--
- 13:16 ET. AOT CLI first added ~5 MB to the SDK bundle
- AOT tool command resolution: +2.19 MiB (~100 ms saved)
- Build-free MTP test: +1.02 MiB
- Size delta checked on every build
- "Budget the SDK, not just the DLL" (13:18): symlink dedup cut 53 MB compressed / 140 MB extracted from the Linux x64 SDK tarball (speaker said "about 150"); AOT spent ~15–20 MB of that
- Design question (13:20): "What do we get out of this chunk of size, and can we get it another way?" PR slash command posts AOT size diffs; Chet's SizeSpy tool reads the compiler/trimmer DGML files to find "dominators" (oversized members).
-->

---
layout: "statement"
---

XML parsing cost 5 MB: XSD → network → crypto.

<!--
- 13:22 ET. The BCL XML reader pulled in ~5 MB of a ~15 MB AOT binary per platform
- Fix: a hand-written recursive-descent parser for one format, saved 5+ MB
- Same idea for embedded resources: localization now read from existing satellite assemblies
- Takeaway: check what your dependencies drag in
- More tips (13:24): use narrow, purpose-built APIs (a Hex1b change saved the Aspire CLI "like 300 KB"); use runtime feature switches; test through a muxer-like harness (they built one called "DN")
-->

---
layout: "statement"
---

Ship your .NET tools Native AOT. Fast and easy — you don't have to choose.

<!--
- 13:26 ET, Chet's wrap-up
- RID-specific Native AOT tools supported since .NET 10
- Parity first: when unsure, fall back to the managed implementation
- AOT payoff beyond startup: explicit, testable architecture
- Q&A (13:28): dotnetup was the team's AOT practice project; Chet made it install .NET 11 "10 minutes before this talk"
- No Rust/C++ comparison done. The win: speed without a rewrite or leaving .NET.
-->

---
layout: "session"
num: 5
time: "1:30 PM"
speakers: "Klaus Löffelmann"
---

# Why WinForms must not change — yet reinvented itself with .NET 11

<!--
[Session 5]
- Theme: huge WinForms history vs constant renewal; "WinForms down the road its own migration tool"
- Demo prop: a second laptop running Windows XP and Visual Studio 2005. It didn't work on stream ("it's not going to work"), so he went straight to demos.
-->

---
layout: "shot"
image: "/shots/133753.jpg"
time: "13:37"
---

# WinForms before: classic visual styles

<!--
- Old FlatStyle-era properties, unused since Windows XP took over rendering, are revived
- Used to make styles close to today's Windows design language
- "Primarily driven by accessibility"
- Demo: a customer entry form in dark mode (VisualStylesModeDemo)
-->

---
layout: "shot"
image: "/shots/133906.jpg"
time: "13:39"
---

# After: one line of code, `Net11` styles

<!--
- New methods/properties on Application: one line changes the whole app's look
- Visual styles mode is an enum: Net11 now, Net12 and Net13 planned
- Same controls: modern Windows look, toggle switches, dark mode
- GroupBox (13:40): flat style fixes the classic low-contrast frame
- CAVEAT (13:50): new styles are "logically a lot larger"; pixel-perfect layouts won't work because control locations stay the same
- Fix coming "very soon": Copilot skills in Visual Studio that move pixel-placed controls into a TableLayoutPanel
-->

---
layout: "statement"
---

"This is not about styling. This has all to do with accessibility."

<!--
- Klaus Löffelmann, 13:42 ET
- Net11 styles follow the Windows accent color (demo: red → blue) and text size, live
- Classic checkbox: a 12x12 pixel "landing area"
-->

---
layout: "shot"
image: "/shots/134428.jpg"
time: "13:44"
---

# Vendor gone? Built-in styles can replace it

<!--
- Cash register demo (13:44)
- Old apps often use control libraries from vendors "probably no longer in business"
- Changing the built-in style changes the whole register's look
-->

---
layout: "statement"
---

`SuspendPainting`: one `using`, any nesting depth.

<!--
- New WinForms .NET 11 API, 13:46 ET
- Before: SuspendLayout at every level of nested containers (TableLayoutPanel in TableLayoutPanel...), and no way to suspend painting
- Now: get a scope, wrap it in `using`; painting and layout are suspended however deep the nesting
- Exact call shape not shown on stream; check docs before quoting code
-->

---
layout: "default"
codeSize: "20"
---

# No more white flash in dark mode

```csharp
// Program.Main (from the demo)
Application.SetColorMode(SystemColorMode.System);            // .NET 9+
Application.SetDefaultVisualStylesMode(DemoConstants.StartupVisualStylesMode);
Application.SetDefaultFormRevealMode(DemoConstants.StartupFormRevealMode);

Application.Run(new MainForm());
```

<!--
- 13:48 ET. "Pretty much all the apps that are providing dark mode have this flash."
- Deferred reveal hides intermediate startup paints. Modes: Deferred and Classic. Deferred "cloaks" the window "like a Klingon ship" until it's built.
- Effect (13:54): startup "feels like it's there instantly ... almost like it was written in C++". Demo code: planned for the .NET Conf repo.
- DemoConstants are the demo's own values; the visual styles mode is the Net11 enum
- Source: screenshot /shots/134952.jpg
-->

---
layout: "statement"
---

Compiler errors written for Copilot to read.

<!--
- 13:56 ET. New WinForms analyzers keep designer code sound
- Problem: Copilot puts for-loops or local functions in designer code, then the designer can't open the form
- The analyzers emit build errors phrased as commands to Copilot ("unroll that, write it step-by-step")
- Copilot compiles, reads the error, fixes it. Worked even with "the more capable local models"
- Q&A (13:58): analyzers add determinism to the AI loop. WinForms skills PR "on the way" in dotnet/skills.
-->

---
layout: "session"
num: 6
time: "2:00 PM"
speakers: "Luis Quintanilla"
---

# The .NET AI Stack: What's New, What's Next, and How It Fits Together

<!--
[Session 6]
- Layers (from title slide): Experiences, Agents, Tools, Multimodal, Context, Decisions, Models
- Foundations: Microsoft.Extensions.AI, VectorData, DataIngestion (170M+ downloads, see keynote slide)
- 14:02: Luis added semantic search to Jellyfin on his home Raspberry Pi with .NET embedding generation. Demo app next: "Media Studio" (Blazor Hybrid) — AI "goes beyond chat".
-->

---
layout: "shot"
image: "/shots/140515.jpg"
time: "14:05"
---

# A research paper in, a narrated video out

<!--
- "Media Studio": one .NET app (Blazor Hybrid), runs locally
- 1 Bring the paper → 2 Read it → 3 Draft with an agent (typed, cited scenes) → 4 A person fixes and saves → 5 Produce (voice, cover, motion, film)
- AI "goes beyond chat"
- Demo (14:07): ask for a video "for beginners"; storyboard appears "after a few seconds"; side pane is an event log, "not quite a chat history"
- 14:09: AG-UI + Blazor AI Components. "Scene two is too abstract, make it simpler" → agent updates the storyboard live
- Final video shown was pre-made ("Prepared from the same project you just watched"), not rendered live
-->

---
layout: "shot"
image: "/shots/141130.jpg"
time: "14:11"
---

# The .NET AI stack: each contract does one job

<!--
- Pink = new: AgentBoundary (hosts an agent in a Blazor page), AG-UI, DocumentExtractionClient, RoutingChatClient (picks the model per request), Decisions API (typed answer with probabilities)
- Existing: IChatClient, AIAgent, AIFunction, ITextToSpeechClient, IRealtimeClient, IImageGenerator
- Demo mixed cloud (OpenAI, Anthropic Claude, Mistral OCR, GitHub Copilot SDK) and local (PdfPig, Kokoro, Whisper.net, ONNX) providers in one app
- Shared: Microsoft.Extensions.AI, Microsoft.Extensions.DataIngestion
- 14:13 "Follow one request. PDF in, film out: every hop is a .NET contract": DocumentExtractionClient → IngestionDocument → RoutingChatClient + IDecisionClient → AIAgent → AgentBoundary (you edit) → ITextToSpeechClient / IImageGenerator → film. Alt slide: /shots/141306.jpg
-->

---
layout: "default"
codeSize: "20"
---

# GPT or Claude: same `IChatClient`

```csharp
// Each official SDK has an AsIChatClient adapter
IChatClient gpt = new OpenAIClient(...)
    .GetResponsesClient().AsIChatClient("gpt-6.1-sol");

IChatClient claude = new AnthropicClient(...)
    .AsIChatClient("claude-sonnet-5-5");

// Same call, either model
var a = await gpt.GetResponseAsync(prompt);
var b = await claude.GetResponseAsync(prompt);
```

<!--
- 14:14 ET. Official OpenAI and Anthropic C# SDKs now have native IChatClient adapters
- App code stays the same; only initialization changes. Sample: aka.ms/meai/start
- Packages: Microsoft.Extensions.AI, Microsoft.Extensions.AI.OpenAI, Anthropic
- Code copied from the stream slide (/shots/141458.jpg), "simplified from Planning.cs + FoundryAnthropic.cs"
- Side note: the final film is stitched with plain code, "no AI at that point"
-->

---
layout: "shot"
image: "/shots/141635.jpg"
time: "14:16"
---

# `RoutingChatClient`: your policy picks the model

<!--
- NEW. The policy is a plain record (LocalOnly, RequireJson, AllowTools, MinimumProbability, ...)
- 1 Policy filters the pool → 2 Decisions API scores what's left → 3 not sure enough: named fallback, or stop
- The router is still just an IChatClient
-->

---
layout: "shot"
image: "/shots/141913.jpg"
time: "14:19"
---

# `DocumentExtractionClient`: swap the reader, keep your code

<!--
- NEW. One contract: a file in; pages, sections, tables, images out
- Three readers: PdfPig (local), Mistral OCR (cloud), any vision IChatClient
- Packages: Microsoft.Extensions.DocumentExtraction + CommunityToolkit.DocumentExtraction.{PdfPig, Mistral, VisionLanguageModel}
- Keynote caveat still applies: experimental, confirm package availability
- Also (14:18): MEAI "core foundations and abstractions for these decision-style models" coming
- Flow (14:21): PDF → DocumentExtractionClient → IngestionDocument → chunks. Same whether the reader is Mistral, a chat client, or Azure Document Intelligence.
-->

---
layout: "shot"
image: "/shots/142237.jpg"
time: "14:22"
---

# No image model: a chat model draws SVG

<!--
- Custom IImageGenerator backed by an IChatClient
- Chat model returns SVG text → app validates it → renders to PNG
- Satisfies the contract: text in, image out. A native image model can drop in later.
- Voice (14:24): narration by Kokoro (local model); mic input transcribed locally with Whisper, or via OpenAI realtime
- Tools: a C# method exposed as a tool; MCP C# SDK is the other way. Session later covers SDK 2.0 and "serving skills over MCP".
-->

---
layout: "shot"
image: "/shots/142657.jpg"
time: "14:26"
---

# Put an agent in your UI: the agent proposes, the person decides

<!--
- NEW: AG-UI C# SDK (just released) — agent streams typed events (run, text, tool call, state change), works with any front end
- NEW: Blazor AI components — <AgentBoundary> hosts an agent; the person edits; Save persists
- Agent Framework on any IChatClient, or the GitHub Copilot SDK
-->

---
layout: "statement"
---

"The best AI demo today, because it wasn't a chatbot."

<!--
- 14:29 ET. Read on stream by the session host: "Kevin said that this was the best AI demo today because it wasn't a chatbot."
- Confirm this was your post before claiming it on stage (transcript says only "Kevin")
- Follow-ons: aka.ms/meai/start, aka.ms/openai/start; MCP C# SDK session (Stephen Halter), agentic UI with Blazor (Daniel Roth)
-->

---
layout: "session"
num: 7
time: "2:30 PM"
speakers: "Gerald Versluis"
---

# What's New in .NET MAUI in .NET 11

<!--
[Session 7]
- 14:34: 1,600 PRs last month, "an absolute record" (keynote stat slide)
- Partners: Syncfusion (engineers fix issues in dotnet/maui + free toolkit), Uno Platform (Android API bindings, co-maintains SkiaSharp), Avalonia (MAUI on Linux)
- 14:50: native passkeys (generate + validate); `dotnet run`, `test`, `watch` now work for MAUI with an interactive platform prompt (full session at 7:30 PM)
-->

---
layout: "statement"
---

Mono → CoreCLR: "you won't really see, but you will feel."

<!--
- Gerald Versluis, 14:37 ET: "the biggest change to .NET MAUI"
- Same runtime as ASP.NET Core and Azure on every MAUI platform
- Demo app: David Ortinau's Barista Notes (screenshot /shots/143737.jpg)
- Avalonia backend is now an option in the .NET MAUI templates for .NET 11
-->

---
layout: "shot"
image: "/shots/144153.jpg"
time: "14:41"
---

# MAUI on Android, NativeAOT: 974 → 280 ms median startup

<!--
- BaristaNotes, Pixel 5, Android 14, .NET 11 RC2, 30 launches per cell
- MAUI median cold start: Full R2R 973.5 ms → NativeAOT 280 ms (C# Android Views: 181 ms)
- Caveat on the chart: MAUI NativeAOT p90 is still 908 ms
- Package: 45.65 MiB (Full R2R) → 30.40 MiB (NativeAOT)
- "Android NativeAOT is experimental" (chart footnote)
- Numbers from the chart only; not spoken in the transcript
- iOS (iPhone 15 Pro, /shots/144228.jpg): MAUI median 490.3 → 321.8 ms with NativeAOT (C# UIKit 185.9); package 58.86 → 42.01 MiB
-->

---
layout: "statement"
---

XAML source generation on by default: Debug behaves like Release.

<!--
- 14:42 ET. XAML compiles to C# at build time with source generators
- No more "trimmed from the release build and boom, your app blows up in production"
- Already listed on the keynote MAUI slide; this is the "why"
-->

---
layout: "default"
codeSize: "20"
---

# C# expressions in XAML: goodbye, value converters

```xml
<!-- Before: a converter class, a resource, and a binding -->
<Button IsEnabled="{Binding IsBusy,
    Converter={StaticResource InverseBool}}" />

<!-- .NET 11 -->
<Button IsEnabled="{!IsBusy}" />

{$'Hello {Name}!'}
{Price * Quantity}
{Title ?? 'Untitled'}
{IsAdmin || IsOwner}
```

<!--
- 14:45 ET. Inline C# replaces most value converters
- Before also needed a whole InverseBoolConverter : IValueConverter class (Convert + ConvertBack)
- Code copied from the stream slide /shots/144523.jpg
-->

---
layout: "shot"
image: "/shots/145306.jpg"
time: "14:53"
---

# .NET MAUI Inspector: see inside your running app

<!--
- Live visual tree, properties, screenshot; record, replay and assert UI flows
- Copilot drives the same session through MCP tools
- Runs in VS Code, the GitHub Copilot app, Copilot CLI, any browser
- Part of MAUI Labs: github.com/dotnet/maui-labs
- Also (14:52): incremental XAML Hot Reload keeps state (no lost navigation stack or values), via dotnet watch
-->

---
layout: "shot"
image: "/shots/145430.jpg"
time: "14:54"
---

# MAUI Labs: 10+ experiments to try

<!--
- github.com/dotnet/maui-labs. "Who knows, some might graduate."
- DevFlow: like Playwright, for MAUI apps and agents
- MAUI CLI, Essentials.AI (on-device chat + embeddings), `maui ai init` (skills + MCP)
- New backends: Linux (GTK) and WPF
- `dotnet new mauitest` for device tests
-->

---
layout: "shot"
image: "/shots/145752.jpg"
time: "14:57"
---

# Heads up: MAUI 10 support ends May 2027

<!--
- Each MAUI version is patched for 18 months: support ends 6 months after the next major ships
- MAUI 10 → May 2027, even though .NET 10 itself is LTS. MAUI 11 → May 2028 (assumes .NET 12 ships Nov 2027)
- aka.ms/maui-support-policy
- Also (14:56): Essentials.AI uses on-device models (Apple Intelligence, Gemini Nano)
- Gerald (14:58): "Every .NET MAUI version has 18 months, period. So get on .NET 11 right now."
- Q&A "best IDE for MAUI?" → "What's an IDE?" Team "has not been in an IDE for a while", building toward the CLI
-->

---
layout: "session"
num: 8
time: "3:00 PM"
speakers: "Drew Noakes, Emanuel Fernandez Dell'Oca"
---

# C# Dev Kit 11: Faster Foundations for .NET Development — and What Comes Next

<!--
[Session 8] Keynote already has the Dev Kit 11 numbers slide (77% / 80% / 36s → 2s); add only new details here.
-->

---
layout: "statement"
---

"VS Code is terrible." It was 15 agents and hundreds of MSBuild workers.

<!--
- 15:03 ET. Dev Kit 11 origin story
- An internal team kept saying VS Code + C# Dev Kit "were terrible"; their VP escalated; "crashing on their machine"
- Reality: "5, 10, 15" agents solving GitHub issues on Macs with 256 GB RAM, and "hundreds and hundreds of MSBuild workers"
- Why Dev Kit 11 was re-architected for many agents on one machine
- The fix (15:04): a build queue that runs the agents' builds serially. Build throughput for all agents went UP — "the oversaturation of build nodes was actually hindering throughput."
-->

---
layout: "statement"
---

The trick: cache the build's project info. `.lscache`.

<!--
- 15:06 ET. The build's pre-compile step (evaluate + resolve inputs, globs, disk scans) is written to a .lscache file
- "Not really that revolutionary to write a cache file to disk"
- Reading it: "a few milliseconds". Asking MSBuild: "hundreds, maybe thousands of milliseconds"
- (My inference, not stated on stream: likely a big part of the keynote's ~77% faster workspace load)
- Next (15:16): reading/writing .lscache lives in the Roslyn repo (open source) and is going into the SDK, so "every build is capable of writing these files" and all tools benefit. "From a faster Dev Kit to a faster development loop."
-->

---
layout: "shot"
image: "/shots/150930.jpg"
time: "15:09"
---

# Opening the Roslyn repo: 89 s → 16 s

<!--
- Dev Kit v3 → v11, warm load, lower is better
- dotnet/roslyn (398 projects): 89.0 → 15.9 s
- dotnet/orleans (155 projects): 62.0 → 17.1 s
- microsoft/aspire (407 projects): 87.9 → 19.9 s
- ~77% faster. Intel Xeon Platinum 8370C, 8 cores, Windows 11 x64
- Numbers from the stream chart
- Memory (15:10): "80% less memory ... you can fit five C# Dev Kits in the space of one from before"
-->

---
layout: "shot"
image: "/shots/151107.jpg"
time: "15:11"
---

# BuildX: skip, copy, or build

<!--
- New build integration in Dev Kit 11
- Implementation-only edit, public API unchanged: build only H, skip unchanged projects, copy outputs where needed
- Confirmed (15:12): BuildX is behind the keynote number. Aspire.slnx, 407 projects: single change 36.1 → 2.1 s (−94%), median of 5
- No-op build: 34.4 → 0.9 s (−97%); the old 34.4 s was "almost entirely overhead"
- Alt chart slide: /shots/151239.jpg
- Demo (15:14): the agent's build already wrote the cache files, so VS Code opens with tests discovered and IntelliSense ready; the test re-run uses BuildX; ".lscaches are also shared across worktrees"
-->

---
layout: "shot"
image: "/shots/151821.jpg"
time: "15:18"
---

# MSBuild Coordinator: one build budget per machine

<!--
- 5, 10, 20 agent builds each asking for N nodes = more than the machine has
- Coordinator: a shared node budget; some builds run, the rest queue
- "Cheaper instances help. Growing concurrency still needs a budget."
- Opt-in, not default; participating builds only
- This is the product version of the origin story's build queue
- Also (15:20): "we want to prioritize the human" — the coordinator decides which builds go first. If an agent's build already produced the .lscache, the IDE can skip its own "design-time build".
- BuildX CLI demo on OrchardCore follows
-->

---
layout: "default"
codeSize: "20"
---

# `dotnet buildx` on OrchardCore

```text
$ dotnet buildx src/OrchardCore.Cms.Web/OrchardCore.Cms.Web.csproj
buildx: all 215 projects up-to-date (388 ms). Nothing to build.

# edit OrchardCoreConstants.cs (a core project), build again
buildx: done in 13378 ms: 2 built, 201 accelerated (612 files copied), 12 skipped.
```

<!--
- 15:22 ET. No-op build of 215 projects: 388 ms
- One change in a core project: 2 projects built, 201 "accelerated" (outputs copied), 12 skipped
- Caveat: that 13.4 s run included a NuGet restore and starting the buildx server
- Q&A (15:28): buildx sits next to `dotnet build`, like `docker buildx` next to `docker build`. Starts as a separate tool, being moved into the SDK; "I do have a dream that it replaces it."
- Output copied from the stream terminal (/shots/152232.jpg); a line with a local user path left out
- Exploring, not committed (15:24): agents are trained on `dotnet build` / `dotnet test`, so if an agent is detected those commands could use the faster paths. Optimizations that might surprise a human are fine for an agent if a log message says "this optimization has been applied" — the agent will read the docs.
-->

---
layout: "statement"
---

20–40% of your agent loop is running .NET tools.

<!--
- 15:26 ET: "in your agent loop, 20 to 40% of that time is actually running .NET tools"
- Ideas to shrink it: infer which tests actually need to run; get errors from a background LSP instead of a build
- Worktrees: "Don't make the next person start over." A new worktree reuses the project data (and maybe binaries) an agent's build already wrote. Broader reuse is "direction", not shipped (/shots/152736.jpg)
-->

---
layout: "session"
num: 9
time: "3:30 PM"
speakers: "Chet Husk"
---

# More Processes, More Problems: Multithreaded MSBuild

<!--
[Session 9] Keynote already has the `-mt` slide (−37% warm incremental on OrchardCore); add only new details.
-->

---
layout: "shot"
image: "/shots/153347.jpg"
time: "15:33"
---

# `-mt` warm incremental: −68% on Windows, −13% on Linux

<!--
- OrchardCore warm incremental. Windows 54.58 → 17.36 s (−68.2%). Linux 25.47 → 22.13 s (−13.1%)
- Cold build (per notes agent, not on this chart): −23.5% Windows, −11.9% Linux
- DIFFERENT from the keynote's −37% (28.4 → 17.9 s, "ASP.NET's shared hardware, 100 projects"). The −mt time is about the same (~17-18 s); the "Normal" baseline differs. Don't quote both as the same measurement.
- Windows gains much more than Linux: Linux's normal build is already faster
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
