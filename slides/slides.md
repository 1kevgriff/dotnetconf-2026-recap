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
