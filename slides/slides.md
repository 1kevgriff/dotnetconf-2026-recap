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
- [title]
- Say: This is a recap of .NET Conf 2026 Day 1, captured live from the stream on 2026-11-10. We start with the keynote, where .NET 11 shipped, then the Day 1 sessions.
- Coverage: the keynote (11:00 AM ET) and the Day 1 sessions so far (sessions 1-9), from transcripts and screenshots taken during the stream.
- Every number on these slides came from a speaker or an on-screen slide. Experimental and preview items are marked as such.
- Why it matters: you get the .NET 11 highlights in one pass, without watching the full day of stream.
- Source: dotnetconf.net/agenda (Day 1 = 2026-11-10); stream transcripts from 10:55 AM ET.
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
- Transition: I watched Day 1 live so you don't have to. Here's what shipped.
-->

---
layout: "session"
num: 1
time: "11:00 AM"
speakers: "Scott Hanselman, Damian Edwards + guests"
---

# Keynote: .NET 11 ships

<!--
- [Session 1 · Keynote] Scott Hanselman, Damian Edwards, Chet Husk, Daniel Roth, Gerald Versluis, Luis Quintanilla, Wendy Breiding, Drew Noakes.
- Say: The keynote was a one-hour tour of .NET 11. Scott Hanselman and Damian Edwards opened it, then a parade of team members each took a few minutes.
- Time: 11:00 AM ET. Also on stage: Mads Torgersen (C# 15), Richard Lander (runtime), Kathy Sullivan and Maddy Montaquila (close). Video guests: Eric Guo (Windows 365), Jeff from Hugging Face.
- Theme: Damian Edwards: "if you take anything away from .NET Conf this year, let it be that .NET is durable."
- Next slides: .NET 11 GA, TinyOS, C# 15 and unions, CLI on Native AOT, MSBuild -mt, runtime async, memory safety; then Web, Mobile, AI, Agents, inner loop, and the close.
- Why it matters: the keynote is the map for everything else this week. Most items get a deep-dive session later.
- Source: 11:00-11:58 ET, transcripts 20261110-110004.txt through 20261110-115600.txt; agenda.md.
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
- Say: Damian Edwards made it official: .NET 11 is available today. Go to get.dot.net.
- Verbatim (Damian): "I'd love to announce that .NET 11 is now available. It's rolling out now."
- Verbatim (Damian): "if you take anything away from .NET Conf this year, let it be that .NET is durable."
- The five-eras slide: 2002 Windows, 2008 Web, 2008 Mobile, 2016 Cloud, Today AI ("Agents write, test and review code alongside us").
- Damian on the cloud era: performance became a feature because "It cost real money when you were running it on someone else's computer."
- Why it matters: .NET 11 is the new current release. You can install it today.
- Source: 11:07-11:09 ET, 20261110-110505.txt; shots 110705.jpg, 110905.jpg.
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
- Say: Scott Hanselman found the tiny operating system he wrote in .NET 1 as a college senior project, and brought it forward to .NET 11.
- He showed the original slides from TechEd Malaysia 2002. He called it a "virtual operating system" "all written in .NET 1".
- The "TinyOS Time Machine": power button, tiny floppy disks, live memory view, the original source, and a CRT glass effect. Verbatim: "still running my original homework."
- Verbatim (Hanselman, on .NET): "It's there. It's reliable. It's fast as heck."
- Fun extras: he has coded since 1984, his GitHub user ID is "under 3,000", and "It took me 11 years to get my four-year degree."
- Why it matters: code you wrote 24 years ago can still run on the newest runtime.
- Source: 11:02-11:06 ET, 20261110-110004.txt and 20261110-110505.txt; shot 110459.jpg.
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
- Say: Mads Torgersen's slide title was "C# 15: Cleaner, safer, faster." Unions are the headline feature.
- Union types: public union Pet(Dog, Cat); - exhaustive over the listed case types.
- Closed hierarchies: public closed class Pet; - a subclass from another assembly is an error.
- Collection arguments: HashSet<string> tags = [with(comparer), "one", "two", "three"]; - pass capacity or a comparer inline.
- Labeled break and continue ("break outer", no flag variables); extension indexers (index into types you don't own); memory safety preview (unsafe calls explicit and auditable).
- Why it matters: less boilerplate and more compiler checks in everyday C#.
- Source: 11:09 ET, shot 110920.jpg; 20261110-110505.txt.
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
- Say: Mads called unions "probably the most anticipated and requested" C# feature "for a long, long time." The demo shows why.
- Before: pets in a List<object>. No type safety, a Shark can sneak in, and the switch warns it is not exhaustive with no good fix.
- After: union Pet(Dog, Cat, Bird). The case types don't have to participate. Each case converts implicitly to Pet; other types don't. Matching on Shark is now an error, and the warning goes away.
- Verbatim (Mads): "ironically, with that warning going away, It sort of makes the warning useful again." Add Hamster and every consuming switch warns again: "this is now actionable."
- Verbatim (Mads): "clarity, safety, those are things that are great regardless of whether human or an agent are actually working on the code."
- Why it matters: you can model "one of these types" without a fake base class, and the compiler finds every place to update.
- Source: 11:10-11:13 ET, 20261110-110505.txt and 20261110-111004.txt; shot 111254.jpg. Deep dive: Mads + Dustin Campbell, 12:00 PM ET.
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
- Say: The .NET CLI itself is now a Native AOT app. Common commands start in about a quarter of the time.
- Numbers (slide): dotnet --help 203.4 ms -> 51.4 ms (75% less); dotnet user-jwts 205.7 -> 69.5 ms (66%); dotnet tool list 188.3 -> 56.1 ms (70%).
- Verbatim (Chet): usage "has roughly tripled in the past year alone" - from human and agent users.
- File-based apps: also work with dotnet package add, dotnet reference add, and format. Chet: "we're really approaching parity" with projects.
- Also: dotnet watch handles app crashes "much more gracefully"; container publish targets WSLC and macOS container runtimes natively; smaller SDK = smaller Docker images; new native dotnetup install manager.
- Why it matters: agents call the CLI constantly. Hundreds of milliseconds saved per call add up.
- Source: 11:13-11:17 ET, 20261110-111004.txt and 20261110-111503.txt; shots 111728.jpg, 111603.jpg. Deep dive: "Moving dotnet Ahead (of Time)!" 1:00 PM ET.
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
- Say: MSBuild has a multithreaded mode in .NET 11. You opt in with one flag: -mt.
- Numbers (slide): cold full build 104.7 s -> 92.4 s (12% less); warm incremental 28.4 s -> 17.9 s (37% less).
- Test setup (slide): OrchardCore, Windows, 100 projects, ASP.NET's shared hardware.
- Verbatim (Chet): important for "that iterative inner loop development that is so common with agents today."
- Why it matters: faster incremental builds help both you and any agent that rebuilds after each edit.
- Source: 11:18 ET, 20261110-111503.txt; shot 111823.jpg. Deep dive: "More Processes, More Problems - Multithreaded MSBuild" 3:30 PM ET.
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
- Say: Richard Lander showed runtime async. Your async code stays the same, but the compiler stops generating state machines and the JIT does the work.
- Opt in with an MSBuild Features property in .NET 11. Verbatim: "We expect it to be the default in .NET 12."
- Verbatim: "near-synchronous performance for async code, which is a claim that we've never been able to make before."
- Chart: 216 / 360 / 504 B per operation at 3 / 5 / 7 async frames with state machines; 0 B with runtime async. Synchronous-completion case. Benchmark: a C# port of Restic.
- Why it matters: free allocation savings in hot async paths, with no code changes.
- Source: 11:19-11:21 ET, 20261110-111503.txt and 20261110-112031.txt; shot 112046.jpg.
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
- Say: C# adopts the same unsafe-contract model as Rust and Swift, with near-identical syntax, but C# is the strictest of the three.
- Slide table: unmarked unsafe call - C# Error, Rust 2024 Error, Swift Warning. Unmarked op inside an unsafe member - C# Error, Rust and Swift Warning. Unsafe allowed by default - C# No, Rust and Swift Yes.
- Verbatim (Lander): "security is our top priority." He cited Microsoft's statement that "70% of vulnerabilities are due to memory safety issues."
- AllowUnsafeBlocks stays false by default, as since C# 1.0. New: unsafe expressions, so a method can expose a safe facade over unsafe code.
- Deep dive: Richard Lander + Andy Gocke. Agenda: 6:30 PM ET. (Lander said "3:30 PM" on stream; (Inference) that is Pacific time.)
- Why it matters: unsafe code becomes explicit and auditable, which helps security reviews.
- Source: 11:21-11:23 ET, 20261110-112031.txt and 20261110-112200.txt; shots 112116.jpg, 112220.jpg.
-->

---
layout: "section"
kicker: "ASP.NET Core 11"
---

# Web

<!--
- [Daniel Roth] ASP.NET Core and Blazor.
- Say: Daniel Roth, the ASP.NET Core product manager, built one customer-service app to show what's new for web developers.
- Time: about 11:23 ET. Demo: a service rep handles a USB-C docking station return as a refund or a replacement.
- Theme (verbatim): businesses need "clear API contracts... rich, interactive user experiences... protected actions."
- Next slides: unions end to end (JSON + OpenAPI 3.2), async validation in Blazor and APIs, built-in CSRF protection, and the "More in ASP.NET Core 11" grid.
- Source: 20261110-112200.txt, 20261110-112401.txt. Deep dive: Daniel Roth, 12:30 PM ET.
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
time: "11:26"
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
time: "11:28"
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
time: "11:29"
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
layout: "section"
kicker: ".NET MAUI"
---

# Mobile

<!--
- [Gerald Versluis] .NET MAUI.
- Say: Gerald Versluis from the .NET MAUI team covered mobile and desktop.
- Time: about 11:30 ET. Theme: .NET 11 is "coming full circle" - MAUI apps now run on CoreCLR.
- Next slides: the team's PR volume with Copilot, MAUI 11 runtime and platforms, the paper-cut fixes, and the open-source .NET Conf app.
- Source: 20261110-113003.txt. Deep dives: Gerald, 2:30 PM ET; Jonathan Peppers, 7:30 PM ET.
-->

---
layout: "statement"
---

1,600 PRs a month. ~80% by Copilot.

<!--
- MAUI team PR volume, about 4x what it was
- 11:30 ET
- Say: The MAUI team went agentic. A year ago they merged 400 to 500 PRs a month. Last month it was over 1,600.
- Verbatim (Gerald): "last month it was 1600 right over 1600 so that's roughly four times as much just because of the power of copilot and 80% of that were even authored by copilot" (light cleanup).
- Verbatim: "the quality is still the same."
- Why it matters: this is a real team's numbers on agentic development, not a demo.
- Source: 11:30 ET, 20261110-113003.txt.
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
- Say: MAUI apps now run on the same runtime as ASP.NET Core and Azure, and Native AOT makes Android apps start much faster.
- AOT footnote (slide): vs .NET 10 Mono; .NET Conf app, median cold start to first frame and signed APK size, Samsung Galaxy A16, .NET 11 RC2, October 2026.
- XAML source generation is on by default: XAML compiles at build time. Latest platforms: Android 17 (API 37) and Xcode 27.
- maui-labs: the maui CLI, DevFlow app automation, and device testing.
- Why it matters: one runtime across server and mobile means fewer platform-specific surprises.
- Source: 11:31 ET, 20261110-113003.txt and 20261110-113200.txt; shot 113143.jpg.
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
- Say: With Copilot, the team finally fixed small "paper cuts" they never got to before.
- Also on the grid: maps pin clustering, custom pin images, JSON styles; cancel one animation at a time; BoxView gradients; system bar colors; themed splash screens for light and dark.
- Verbatim (Gerald): "our developer satisfaction has been at an all-time high even from the Xamarin days."
- DevFlow (verbatim): "your agent can interact with it. It can inspect it. It can look at it, and it can self-iterate over your MAUI app."
- Source: 11:32-11:33 ET, 20261110-113200.txt; shot 113240.jpg.
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
- Say: The official .NET Conf app is a MAUI app, open source, built with agents, and in the app stores now.
- Live demo: the keynote showed as live in the app. Speakers, sessions, your own favorite schedule, and notifications.
- Verbatim (Gerald): "there's no magic going on here this was not prepared" (light cleanup).
- Why it matters: a real, shipping reference app you can read to see MAUI 11 features in use.
- Source: 11:34 ET, 20261110-113401.txt; shots 113401.jpg, 113446.jpg.
-->

---
layout: "section"
kicker: "Modernization + AI"
---

# AI

<!--
- [Luis Quintanilla] Modernization and AI.
- Say: Luis Quintanilla, who leads product for the .NET AI libraries, covered modernization and AI.
- Time: about 11:35 ET. Theme (verbatim): "modernization means different things" and "it's not all or nothing."
- Next slides: customer modernization results, the Windows 365 story (Aspire, then a bounded agent workflow), the .NET AI ecosystem, Llama on Windows, and what's new in .NET + AI.
- Source: 20261110-113401.txt, 20261110-113603.txt. Deep dive: "The .NET AI Stack", Luis, 2:00 PM ET.
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
- Say: Four customers, four different paths to modern .NET.
- HttpMaster: modernized the foundations of a decades-old app. Visual Studio: modernized a select number of components and kept the core intact.
- Ateleris / FHNW: a processing pipeline, "together with hardware and architecture changes" (Luis). The 155x and 8-to-1 numbers are from the slide.
- Intune (verbatim): "you don't have to do it all yourself. They were able to save weeks off a library migration" with AI assistance.
- Why it matters: modernization can be partial. Pick the component that hurts most.
- Source: 11:35-11:36 ET, 20261110-113401.txt and 20261110-113603.txt; shot 113638.jpg.
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
- Say: Eric Guo, a Principal Group Engineering Manager on Windows 365, told how they made local dev work for a big microservice system.
- Scale: over 100 microservices on ASP.NET Core and Azure Functions, over 4,000 scenario tests, used by tens of thousands of organizations.
- Old pain: to run one service you had to reproduce cross-repo dependencies, Cosmos DB, Microsoft Entra, and test data.
- Goal (verbatim): "clone the repo, press F5 for a fully configured manual testing environment." It "replaced hours or days spent recreating the system locally."
- Readiness checks replaced fixed delays: Cosmos DB counts as ready only after its partitions are available.
- Source: 11:37-11:39 ET, 20261110-113603.txt and 20261110-113801.txt; shots 113653.jpg, 113851.jpg.
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
- Say: Once the foundation was reliable, onboarding repos by hand became the bottleneck. So they gave the agent a fixed loop with C#-defined checks.
- Slide subtitle: "C# defines the checks. The agent works inside them." Check uses a C# metric engine; Plan is written before any file changes; Learn proposes pattern updates for human review.
- Verbatim (Eric Guo): agentic AI "not as a replacement for the engineering process, but as an accelerator for a process we already understood."
- Verbatim: "every pull request remains human-reviewed before it proceeds." The quote above is on the slide "Checks first. People decide."
- Why it matters: a practical pattern for agents at scale - deterministic gates first, humans approve.
- Source: 11:40 ET, 20261110-114003.txt; shots 114038.jpg, 114053.jpg.
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
- Say: The .NET team builds the shared AI foundations. The ecosystem on top of them passed 170 million package downloads.
- Slide: "170M+ package downloads | Hundreds of dependent packages." Metrics as of Nov 3, 2026.
- More on the slide: AG-UI for .NET, Blazor AI Components (experimental), GitHub Copilot SDK for .NET, Community Toolkit for .NET AI, Microsoft.Extensions.AI.Evaluation, AgentEval (community).
- Demo: Jellyfin, an open-source .NET media server, got semantic search. Verbatim (Luis): "you don't need to go and rewrite your entire application."
- Why it matters: code against one abstraction and swap model providers later.
- Source: 11:41-11:42 ET, 20261110-114003.txt and 20261110-114201.txt; shot 114148.jpg.
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
- Say: Jeff from Hugging Face announced Llama for Windows: a system-tray app to find, download, and chat with local models. It is built on .NET.
- Verbatim (Jeff): "we built Llama for Windows on .NET 10 and WinUI 3 with llama.cpp powering inference under the hood" (STT fixed: "Lama CPP" = llama.cpp).
- It exposes OpenAI-compatible APIs, so your own apps can call local models.
- Store timing: the slide said "Now available in the Microsoft Store"; Jeff said it will be in the Windows Store "later this week."
- Why it matters: free, private, local models with an OpenAI-style endpoint for dev and test.
- Source: 11:43-11:45 ET, 20261110-114201.txt and 20261110-114400.txt; shot 114351.jpg.
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
- Say: Six new items for AI in .NET. Most are experimental, so treat them as previews.
- Slide detail: MEAI integrations - "Try it | aka.ms/meai/start". Decisions API - "MEAI decision abstractions (coming soon)." MCP C# SDK - "2.0 major milestone."
- RoutingChatClient (verbatim, Luis): it "lets you define policies that match the task to the right model capabilities" (STT fixed: "writing chat client").
- Slide footer also said: "Experimental APIs may change."
- Source: 11:45 ET, 20261110-114400.txt; shot 114545.jpg.
-->

---
layout: "section"
kicker: "Agentic development"
---

# Agents

<!--
- [Wendy Breiding] Agentic development.
- Say: Wendy Breiding, a PM for agentic development experiences, showed how to use agents on .NET code.
- Time: about 11:46 ET. Demo app: a party RSVP app that overbooks when two users click at the same time.
- Next slides: the GitHub Copilot app fixes the race; dotnet/skills and the skills evaluation dashboard.
- Source: 20261110-114602.txt. Deep dive: "Beyond Autocomplete", Wendy, 5:00 PM ET.
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
- Say: Wendy wrote a file-based app to reproduce the bug, then gave the fix to the GitHub Copilot app.
- Verbatim (Wendy): "if two users happen to click at the same time, it confirms them both even if there's only one slot left."
- She used "Copilot Fusion", which picks the model for you. It chose a model she called "GPT-6 Luna" (name as heard) for "a medium complexity type of problem."
- Why it matters: file-based apps are a quick way to give an agent a repro it can run.
- Source: 11:46-11:47 ET, 20261110-114602.txt; shot 114707.jpg.
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
- Say: The .NET team publishes curated agent skills, and an evaluation dashboard that shows when a skill helps and when it does not.
- Dashboard row: csharp-expert + claude-sonnet-5: tokens 129.1k -> 75.8k, time 41.0 s -> 11.0 s, verdict "Worth installing."
- Honest results: csharp-expert + claude-haiku-4.5 showed -35% tokens and -42% time, but the verdict was "No clear result yet."
- Verbatim (Wendy): "we don't want you to take our word for it." And: "up to 50% reduction in memory usage when you're using multiple agents at once" with the new Roslyn.
- Why it matters: you can check the data before you install a skill for your team.
- Source: 11:48-11:49 ET, 20261110-114800.txt; shots 114810.jpg, 114845.jpg.
-->

---
layout: "section"
kicker: "Next-gen inner loop"
---

# Faster, by doing less

<!--
- [Drew Noakes] Next-gen inner loop. 11:50 ET.
- Copilot's RSVP race fix verified on stage
- Say: After Wendy's fix ran ("one was confirmed and the other is told it was full"), Drew Noakes took over to talk about the inner loop.
- Drew works on .NET developer tooling. Theme: tools must share the machine with agents.
- Next slides: "Your machine has company", and the C# Dev Kit 11 numbers.
- Source: 11:50-11:51 ET, 20261110-115003.txt; shot 115108.jpg. Deep dive: C# Dev Kit 11, Drew Noakes + Emanuel Fernandez Dell'Oca, 3:00 PM ET.
-->

---
layout: "statement"
---

Your machine has company.

<!--
- With agents running, dev tools can't own the whole machine
- C# Dev Kit 11 re-architected for performance
- Say: Tools were built for one person in one IDE. Now agents edit, build, and test on the same machine at the same time.
- Verbatim (Drew): "But now your machine has company."
- Verbatim: "So our tools can't act like they own the whole machine anymore. The fewer resources each one needs, the more room there is for you and your agents to work side by side."
- Why it matters: if you run agents locally, tool memory and CPU use now directly limit how much work you get done.
- Source: 11:51 ET, 20261110-115003.txt; shot 115143.jpg.
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
- Say: Drew measured on three large test solutions. The headline: a one-change incremental build on Aspire dropped from 36 seconds to 2.
- Verbatim (Drew): "you make just one change and build just that change across the whole solution, dropping from 36 seconds down to just two."
- Also: faster worktree initialization; exploring an agent-oriented mode that detects agent callers.
- Source: 11:52-11:53 ET, 20261110-115200.txt; shot 115215.jpg.
-->

---
layout: "section"
kicker: "Keynote close"
---

# 4 days. 60+ sessions.

<!--
- [Kathy Sullivan, Maddy Montaquila] 11:54 ET.
- Ask the team live: dotnetconfquestions.com
- Say: Kathy Sullivan from the .NET product team and Maddy Montaquila, the Aspire PM, closed the keynote.
- Verbatim (Kathy): "We've got three more days after today. We've got over 60 sessions for you."
- Plan: Day 1 = the team that built .NET; Day 2 = Visual Studio, Windows, Azure, and data; Days 3 and 4 = community, run with community folks.
- Next slides: Microsoft products built on .NET, and the download link.
- Source: 11:54-11:55 ET, 20261110-115402.txt; shots 115417.jpg, 115730.jpg.
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
- Say: Microsoft runs its own big products on .NET.
- Full slide list: Microsoft Copilot, Teams, Bing, Copilot Studio, Intune, Azure, Xbox, Exchange Online, Windows 365, Azure Service Fabric.
- Verbatim (Kathy): "if you're getting a Teams message on your phone, that's backed by a .NET service." Cloud PC is also .NET, "running Aspire on the back-end."
- Source: 11:55 ET, 20261110-115402.txt; shot 115537.jpg.
-->

---
layout: "shot"
image: "/shots/115635.jpg"
time: "11:56"
---

# Download .NET 11: get.dot.net

<!--
- winget and other installers "soon"
- Say: That's the keynote. .NET 11 is out now at get.dot.net.
- Verbatim (close, light cleanup): "So, get.dot.net. I said the site correctly, get.dot.net. Soon it will be in winget, dotnetup, all the other places you can install it as well" (STT fixed: "winget.net up").
- Also at the close: a 2026 developer survey (about 15 minutes) that feeds .NET 12 planning.
- Why it matters: install it today, try the features you just saw.
- Source: 11:56-11:58 ET, 20261110-115600.txt and 20261110-115802.txt; shot 115635.jpg.
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
- Say: Session 2 is Mads Torgersen and Dustin Campbell on C# 15. Most of it is unions, plus a few smaller features.
- 12:00 PM ET. Speakers: Mads Torgersen, Dustin Campbell (both work on C#)
- Version rule from the stream: C# version = .NET version + 4, so C# 15
- Theme: let the compiler know the full set of types, so switches are exhaustive
- Next slides: unions (before/after demo, how they work), `closed` classes, collection expression args (`with(...)`), labeled break/continue, extension indexers, Q&A on closed vs union
- Wrap-up also named a memory safety preview and runtime async ("not different, just faster")
- Why it matters: C# 15 gives you safe closed sets of types without a class hierarchy or a discard arm.
- Source: 12:00–12:28 ET, transcripts 20261110-120000.txt to 20261110-122802.txt
-->

---
layout: "statement"
---

Unions: 18 years in the making.

<!--
- Say: Unions shipped in C# 15. Mads said the team talked about them when he joined Microsoft, about 18 years ago.
- 12:00 ET. Mads: "we were talking about it ... like 18 years ago"
- C# version = .NET version + 4, so C# 15
- Demo: Dog, Cat, Bird, Shark from libraries you don't own
- Verbatim (light cleanup): "when I joined Microsoft, now like 18 years ago or something like that, we were kind of talking about it then."
- "A lot of designs came through, and I'm really excited about this one."
- Demo types come from other libraries: "We don't own, this isn't a hierarchy that we have built ourselves."
- Why it matters: a long-requested feature is now in the language, so plan where it replaces object or marker interfaces.
- Source: 12:00 ET, transcripts/20261110-120000.txt
-->

---
layout: "shot"
image: "/shots/120317.jpg"
time: "12:03"
---

# Before: `object`, and a switch that's never exhaustive

<!--
- Say: Before unions, the only common type for Dog, Cat, and Bird is object. So a Shark gets in, and the switch can never be exhaustive.
- List<object> accepts anything, so the switch warns CS8509
- Fix: union Pet(Dog, Cat, Bird), then List<Pet>. A Shark no longer fits.
- Verbatim: "Yeah, object, all the way to object, just like .NET 1.0, except with generics"
- The suggested fix is a discard pattern: "there is a way of doing it, but not a good way ... Because now you're just silencing everything that might come in."
- Union syntax: `union Pet(Dog, Cat, Bird)`. Dog, Cat, Bird are called "case types".
- Why it matters: object plus a discard hides bugs; a union makes the compiler check the set.
- Source: 12:02–12:04 ET, transcripts/20261110-120202.txt; shot /shots/120317.jpg
-->

---
layout: "shot"
image: "/shots/120500.jpg"
time: "12:05"
---

# After: Shark is a compile error

<!--
- Say: With List<Pet>, adding a Shark is now a compile error, and the switch over Pet is exhaustive with no discard.
- Case types convert implicitly to the union
- Remove the Shark arm: the switch is exhaustive, no discard needed
- Make a case nullable (Cat?) and you must add a null arm
- Errors seen: Shark "cannot implicitly convert to pet"; a Shark arm in the switch is not a case of the union
- Two things a union gives: implicit conversion from case type to union, and pattern matching on the case types
- Nullable Cat demo (a Schrödinger's cat joke): the warning said exactly what was missing, the null case
- Verbatim: "when the warning's gone, you know you've dealt with everything."
- Why it matters: the compiler becomes the checklist for every case you must handle.
- Source: 12:04–12:06 ET, transcripts/20261110-120405.txt and 20261110-120602.txt; shot /shots/120500.jpg
-->

---
layout: "shot"
image: "/shots/120737.jpg"
time: "12:07"
---

# Unions are real types

<!--
- Say: A union is a real type. You can add members and generics, and you can hand-write one with the [Union] attribute.
- Generic type parameters, function members (`this switch`)
- No extra state: the value inside is the state
- Case types: any type convertible to object, incl. type parameters
- Default union is a struct. Add [Union] to any class/struct to roll your own; the compiler lists what's missing (e.g. a Value property).
- Under the hood: an object? Value plus one constructor per case type. Conversion calls the constructor; pattern matching reads Value.
- Hand-write a [Union] (IUnion) to avoid boxing value types, or to adapt an existing union-like type.
- The compiler-generated union also implements IUnion (just the Value property), so code can work with unions without the exact type. "It's optional, but it's useful."
- Advanced customization is documented on Microsoft Learn ("all documented on the Learn at Microsoft")
- Why it matters: you can adapt existing union-like types and control storage to avoid boxing.
- Source: 12:06–12:13 ET, transcripts/20261110-120602.txt to 20261110-121200.txt; shot /shots/120737.jpg
-->

---
layout: "shot"
image: "/shots/121715.jpg"
time: "12:17"
---

# `closed`: only your assembly can inherit

<!--
- Say: `closed` fixes the same problem for your own class hierarchy. Only your assembly can derive from it, so the switch is exhaustive.
- Setup: public abstract Operation, another project adds EvilAdd, so no exhaustive switch
- `closed` makes the class implicitly abstract
- Subclasses in other assemblies are errors
- The switch is exhaustive again
- Demo: a calculator with abstract Operation and Number, Add, Subtract, Multiply, Divide; another project added EvilAdd and EvilSubtract
- Wrapping the five classes in a union works but is "painful": "That's not the scenario that unions were created for."
- Verbatim: "When you are a close class, only in your own assembly do you get to directly inherit from that."
- Why it matters: public data models in libraries can now be closed without constructor tricks.
- Source: 12:14–12:18 ET, transcripts/20261110-121403.txt and 20261110-121600.txt; shot /shots/121715.jpg
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
- Say: Collection expressions can now pass constructor arguments. Put `with(...)` first inside the brackets.
- 12:20 ET. with(...) passes constructor args: a comparer, a capacity
- Ctrl+. in the IDE offers the fix
- Screenshot: /shots/122000.jpg (not shown)
- Before: to pass a comparer or capacity you had to fall back to `new HashSet<string>(comparer) { ... }`
- After: `[with(StringComparer.OrdinalIgnoreCase), "one", "two"]` calls that constructor, then adds the items
- Verbatim: "use the with keyword, and then give a list of arguments that that collection type responds to" (transcript says "width", a speech-to-text error)
- Why it matters: you keep collection expression syntax even when the collection needs configuration.
- Source: 12:18–12:20 ET, transcripts/20261110-121805.txt and 20261110-122002.txt
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
- Say: C# 15 adds labeled break and continue. Label the outer loop, then break or continue to it from deep inside.
- 12:21 ET. Replaces the "am I done yet" flag variable
- Works with continue too
- IDE refactoring: "use labeled jump statement"
- Before: a "done" flag variable, set in the inner loop and checked in the outer loop
- After: `outer:` on the outer loop, then `break outer;` leaves both loops at once
- Verbatim: "bypasses everything in between"; "Easier to not make a mistake."
- "many, many languages have something like this" ... "we're late to the game, but now we're in the game"
- Why it matters: fewer flag variables and fewer mistakes when you edit nested loops.
- Source: 12:20–12:22 ET, transcripts/20261110-122002.txt and 20261110-122200.txt
-->

---
layout: "shot"
image: "/shots/122230.jpg"
time: "12:22"
---

# Extension indexers

<!--
- Say: C# 14 added extension blocks with properties. C# 15 adds extension indexers with the same syntax.
- Index into types you don't own
- Builds on C# 14 extension blocks (properties came first)
- The extension block syntax scales to new member kinds
- Wrap-up (12:24): memory safety preview lets you mark your own APIs unsafe and track it transitively; async is "not different, just faster" with runtime async
- Why it matters: you can add natural indexing to types you do not own.
- Source: 12:22–12:24 ET, transcripts/20261110-122200.txt and 20261110-122403.txt; shot /shots/122230.jpg
-->

---
layout: "statement"
---

`closed` for your hierarchy. `union` for types you don't own.

<!--
- Say: Use `closed` when you own the hierarchy. Use a union when the types are not in one hierarchy or you do not control them.
- 12:26 ET Q&A
- closed: the list is your direct descendants
- union: types not in a hierarchy, or you don't control (e.g. data over the wire)
- Generated unions are structs, so implicitly sealed
- System.Text.Json supports unions (some cases still need attributes)
- No new runtime needed: older consumers (e.g. .NET Framework 4.8) read .Value, without union pattern matching
- Why it matters: pick the right tool for closed sets; both give exhaustive switches.
- Source: 12:24–12:28 ET, transcripts/20261110-122403.txt to 20261110-122802.txt
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
time: "12:31"
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
time: "12:32"
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
time: "12:34"
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
time: "12:37"
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
time: "12:41"
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
time: "12:42"
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
time: "12:48"
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
time: "12:51"
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
time: "12:54"
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
num: 4
time: "1:00 PM"
speakers: "Chet Husk"
---

# Moving `dotnet` Ahead (of Time)!

<!--
[Session 4]
- Say: Session 4 is Chet Husk. The .NET CLI now runs many commands as Native AOT, and he showed how they did it.
- 1:00 PM ET. Speaker: Chet Husk, PM for the SDK, the .NET CLI, and core tooling
- Verbatim: "Billions and billions and billions of commands get run on the .NET CLI every month."
- "we are all in on native AOT as a technology now"
- Next slides: startup numbers, CLI-as-library architecture, what had to change, size trade-offs, the 5 MB XML lesson, ship your tools AOT
- Why it matters: faster CLI commands add up for people and agents that run commands in chains.
- Source: 13:00–13:30 ET, transcripts/20261110-130000.txt to 20261110-132803.txt
-->

---
layout: "shot"
image: "/shots/130256.jpg"
time: "13:02"
---

# `dotnet --version`: 118 ms → 33 ms

<!--
- Say: `dotnet --version` went from 118 to 33 milliseconds. That is about two-thirds less time on every call.
- Native AOT CLI vs managed, macOS arm64
- tool list --local: 121 → 32 ms; user-secrets list: 142 → 54 ms
- "Billions and billions of commands" run on the CLI every month
- Compounds (13:05 chart): 3-command SDK check 374 → 118 ms (−69%); tool list + run 297 → 110 ms (−63%)
- AOT now covers core diagnostics, solution commands, most tool management
- Next: build commands, tool install/restore, dotnet new
- Twist: the CLI is a Native AOT library; `dotnet` itself is the native muxer
- Measured on an M1 arm64 macOS laptop with release bits. Slower machines or spinning disks likely see bigger deltas.
- Verbatim: "if we can cut 20 milliseconds off of a command, at scale that matters."
- Also AOT: cached runs of file-based apps, and MTP test runs without a build
- Why it matters: agents and scripts chain many commands, so the savings compound.
- Source: 13:02–13:08 ET, transcripts/20261110-130201.txt to 20261110-130605.txt; shot /shots/130256.jpg
-->

---
layout: "shot"
image: "/shots/130903.jpg"
time: "13:09"
---

# The CLI is a library now

<!--
- Say: The CLI is not an AOT app, it is an AOT library. The native muxer loads it and runs eligible commands with no CoreCLR startup.
- Native `dotnet` muxer picks the SDK, loads the SDK's Native AOT library
- Eligible commands run native: no CoreCLR startup
- Everything else falls back in-process to the managed CLI (hostfxr starts CoreCLR)
- The muxer has two jobs: launch arbitrary .NET DLLs, and select and load an SDK. That stays the same.
- The SDK exposes a C ABI native entry point; the AOT library parses the whole command line and decides AOT or not
- Verbatim: "same commands to end users, better performance on the AOT commands, and maintained compatibility with the managed commands."
- The AOT share grows over time as more commands light up
- Why it matters: you get the speed with no change to the commands you type.
- Source: 13:06–13:10 ET, transcripts/20261110-130605.txt and 20261110-130803.txt; shot /shots/130903.jpg
-->

---
layout: "shot"
image: "/shots/131100.jpg"
time: "13:11"
---

# Going AOT: what had to change

<!--
- Say: Most of the AOT work was annotations. A few parts needed rewrites: reflection, runtime codegen, and dependencies.
- Reflection discovery → known types, generated metadata (incl. load-bearing Assembly.Location)
- Runtime codegen → static code paths
- Dynamic deps → accurate annotations, reachable-code tests
- "Sometimes this is entire rewrites, which sucks, but it's not super frequent." Mostly annotations.
- Gotcha (13:12): a Native AOT library has no meaningful base directory (it points at the host), so the SDK needed an explicit "SDK root"
- Partners (13:14): NuGet made its JSON reading/writing AOT-capable; early experiments with MSBuild evaluation in AOT. Approach: "strangler fig" the CLI.
- Why it matters: this is the checklist for your own AOT migration.
- Source: 13:10–13:16 ET, transcripts/20261110-131000.txt to 20261110-131405.txt; shot /shots/131100.jpg
-->

---
layout: "statement"
---

No free lunch: AOT trades size for speed.

<!--
- Say: AOT is not free. Every feature adds megabytes, so the team checks size on every build.
- 13:16 ET. AOT CLI first added ~5 MB to the SDK bundle
- AOT tool command resolution: +2.19 MiB (~100 ms saved)
- Build-free MTP test: +1.02 MiB
- Size delta checked on every build
- "Budget the SDK, not just the DLL" (13:18): symlink dedup cut 53 MB compressed / 140 MB extracted from the Linux x64 SDK tarball (speaker said "about 150"); AOT spent ~15–20 MB of that
- Design question (13:20): "What do we get out of this chunk of size, and can we get it another way?" PR slash command posts AOT size diffs; Chet's SizeSpy tool reads the compiler/trimmer DGML files to find "dominators" (oversized members).
- Why it matters: if you ship AOT, budget size the way you budget speed.
- Source: 13:16–13:22 ET, transcripts/20261110-131601.txt to 20261110-132000.txt
-->

---
layout: "statement"
---

XML parsing cost 5 MB: XSD → network → crypto.

<!--
- Say: One XML reader pulled in 5 MB: XSD, then network, then crypto. A small hand-written parser fixed it.
- 13:22 ET. The BCL XML reader pulled in ~5 MB of a ~15 MB AOT binary per platform
- Fix: a hand-written recursive-descent parser for one format, saved 5+ MB
- Same idea for embedded resources: localization now read from existing satellite assemblies
- Takeaway: check what your dependencies drag in
- More tips (13:24): use narrow, purpose-built APIs (a Hex1b change saved the Aspire CLI "like 300 KB"); use runtime feature switches; test through a muxer-like harness (they built one called "DN")
- Why it matters: in AOT, one convenient API can drag in a large dependency graph.
- Source: 13:22–13:26 ET, transcripts/20261110-132202.txt and 20261110-132403.txt
-->

---
layout: "statement"
---

Ship your .NET tools Native AOT. Fast and easy — you don't have to choose.

<!--
- Say: Chet's message: ship your .NET tools as Native AOT. You get speed without a rewrite in another language.
- 13:26 ET, Chet's wrap-up
- RID-specific Native AOT tools supported since .NET 10
- Parity first: when unsure, fall back to the managed implementation
- AOT payoff beyond startup: explicit, testable architecture
- Q&A (13:28): dotnetup was the team's AOT practice project; Chet made it install .NET 11 "10 minutes before this talk"
- No Rust/C++ comparison done. The win: speed without a rewrite or leaving .NET.
- Why it matters: tool authors can get native startup times and stay in .NET.
- Source: 13:26–13:30 ET, transcripts/20261110-132601.txt to 20261110-133001.txt
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
- Say: Session 5 is Klaus Löffelmann from the WinForms team. WinForms must stay compatible, but .NET 11 still changes its look and behavior a lot.
- Theme: huge WinForms history vs constant renewal; "WinForms down the road its own migration tool"
- Demo prop: a second laptop running Windows XP and Visual Studio 2005. It didn't work on stream ("it's not going to work"), so he went straight to demos.
- 1:30 PM ET. Speaker: Klaus Löffelmann, WinForms team
- Verbatim: "the necessity to renew constantly to make WinForms down the road its own migration tool."
- Next slides: classic visual styles, Net11 styles in one line, accessibility, vendor replacement, SuspendPainting, no white flash in dark mode, Copilot-friendly analyzers
- Why it matters: old WinForms apps can look modern and get more accessible without a rewrite.
- Source: 13:30–13:33 ET, transcripts/20261110-133001.txt and 20261110-133203.txt
-->

---
layout: "shot"
image: "/shots/133753.jpg"
time: "13:37"
---

# WinForms before: classic visual styles

<!--
- Say: WinForms had FlatStyle properties since the start. They were dormant after Windows XP, and .NET 11 revives them.
- Old FlatStyle-era properties, unused since Windows XP took over rendering, are revived
- Used to make styles close to today's Windows design language
- "Primarily driven by accessibility"
- Demo: a customer entry form in dark mode (VisualStylesModeDemo)
- FlatStyle has four settings: System (the OS draws), and Flat, Popup, Standard (WinForms draws)
- Visual Basic called the XP mode "Enable XP Visual Styles"
- Why it matters: existing properties get new value; no new control set to learn.
- Source: 13:34–13:38 ET, transcripts/20261110-133400.txt and 20261110-133603.txt; shot /shots/133753.jpg
-->

---
layout: "shot"
image: "/shots/133906.jpg"
time: "13:39"
---

# After: one line of code, `Net11` styles

<!--
- Say: In .NET 11 one line on Application switches the whole app to the Net11 visual style.
- New methods/properties on Application: one line changes the whole app's look
- Visual styles mode is an enum: Net11 now, Net12 and Net13 planned
- Same controls: modern Windows look, toggle switches, dark mode
- GroupBox (13:40): flat style fixes the classic low-contrast frame
- CAVEAT (13:50): new styles are "logically a lot larger"; pixel-perfect layouts won't work because control locations stay the same
- Fix coming "very soon": Copilot skills in Visual Studio that move pixel-placed controls into a TableLayoutPanel
- Verbatim: "these controls are still the same Windows controls, but they are drawn in a way that they mimic the experience."
- Why it matters: a modern look with one line, but check layouts that depend on exact pixel sizes.
- Source: 13:38–13:40 ET, transcripts/20261110-133801.txt and 20261110-134003.txt; caveat 13:50; shot /shots/133906.jpg
-->

---
layout: "statement"
---

"This is not about styling. This has all to do with accessibility."

<!--
- Say: Klaus said the new styles are about accessibility, not theming. The app follows the Windows accent color and text size live.
- Klaus Löffelmann, 13:42 ET
- Net11 styles follow the Windows accent color (demo: red → blue) and text size, live
- Classic checkbox: a 12x12 pixel "landing area"
- Verbatim (the slide drops a duplicated "not"): "this is not really not about styling. This has all to do with accessibility."
- On a 4K display the old 12x12 checkbox target is "just too small for modern monitor"
- Demo: Windows text size set to almost 120%; the running WinForms app picked it up on the fly
- Why it matters: bigger targets and system settings support help users without extra code.
- Source: 13:40–13:44 ET, transcripts/20261110-134003.txt and 20261110-134200.txt
-->

---
layout: "shot"
image: "/shots/134428.jpg"
time: "13:44"
---

# Vendor gone? Built-in styles can replace it

<!--
- Say: Many old apps depend on control vendors that are gone. Built-in styles can now give those apps a modern look.
- Cash register demo (13:44)
- Old apps often use control libraries from vendors "probably no longer in business"
- Changing the built-in style changes the whole register's look
- Cash register: "a typical line of business app that could have been ... done in WinForms like 10, 15 years ago"; "usually there's no need to migrate it"
- Verbatim: vendor libraries are "in many, many cases sort of an impediment to really bring your app over."
- Switch from Standard to Popup style: real 3D button look, but the transition was slow. That leads to SuspendPainting (next slide).
- Why it matters: you can remove a dead third-party dependency and keep the UI modern.
- Source: 13:44–13:46 ET, transcripts/20261110-134403.txt and 20261110-134606.txt; shot /shots/134428.jpg
-->

---
layout: "statement"
---

`SuspendPainting`: one `using`, any nesting depth.

<!--
- Say: SuspendPainting gives you one scope that suspends painting and layout for all nested containers.
- New WinForms .NET 11 API, 13:46 ET
- Before: SuspendLayout at every level of nested containers (TableLayoutPanel in TableLayoutPanel...), and no way to suspend painting
- Now: get a scope, wrap it in `using`; painting and layout are suspended however deep the nesting
- Exact call shape not shown on stream; check docs before quoting code
- Demo option name: "use suspending scope" on the cash register
- Why it matters: big layout changes, like a font change, no longer repaint step by step.
- Source: 13:46 ET, transcripts/20261110-134606.txt
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
- Say: Dark mode WinForms apps used to flash white at startup. Deferred reveal hides the window until it is built.
- 13:48 ET. "Pretty much all the apps that are providing dark mode have this flash."
- Deferred reveal hides intermediate startup paints. Modes: Deferred and Classic. Deferred "cloaks" the window "like a Klingon ship" until it's built.
- Effect (13:54): startup "feels like it's there instantly ... almost like it was written in C++". Demo code: planned for the .NET Conf repo.
- DemoConstants are the demo's own values; the visual styles mode is the Net11 enum
- Source: screenshot /shots/134952.jpg
- Why it matters: dark mode apps start without a white flash and feel faster.
- Source (transcripts): 13:48–13:54 ET, transcripts/20261110-134802.txt to 20261110-135400.txt
-->

---
layout: "statement"
---

Compiler errors written for Copilot to read.

<!--
- Say: The WinForms team wrote analyzer errors as instructions for Copilot, so the AI fixes designer code it breaks.
- 13:56 ET. New WinForms analyzers keep designer code sound
- Problem: Copilot puts for-loops or local functions in designer code, then the designer can't open the form
- The analyzers emit build errors phrased as commands to Copilot ("unroll that, write it step-by-step")
- Copilot compiles, reads the error, fixes it. Worked even with "the more capable local models"
- Q&A (13:58): analyzers add determinism to the AI loop. WinForms skills PR "on the way" in dotnet/skills.
- Why it matters: analyzers make AI edits to designer code safe and repeatable.
- Source: 13:56–14:00 ET, transcripts/20261110-135601.txt and 20261110-135804.txt
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
- Say: Luis Quintanilla leads product for the .NET AI libraries. His pitch: the .NET team ships shared AI contracts, and the whole ecosystem builds on them.
- Time: 2:00 PM ET slot (Luis started ~14:01). Speaker: Luis Quintanilla.
- Luis (14:01): "I could literally do a whole day just focusing and doing deep dives into each of these sections, but we're going to try to do this in 30 minutes or so."
- Layers (from title slide): Experiences, Agents, Tools, Multimodal, Context, Decisions, Models
- Foundations: Microsoft.Extensions.AI, VectorData, DataIngestion (170M+ downloads, see keynote slide)
- 14:02: Luis added semantic search to Jellyfin on his home Raspberry Pi with .NET embedding generation. Demo app next: "Media Studio" (Blazor Hybrid) — AI "goes beyond chat".
- Jellyfin detail (14:02): "it's all built entirely in .NET"; a recent release exposed APIs to bring your own search and recommendations.
- Coming up in this session: Media Studio demo (paper → video) · the stack map · one IChatClient for GPT and Claude · RoutingChatClient · DocumentExtractionClient · a chat model that draws SVG · AG-UI + Blazor AI components · the "not a chatbot" quote and Q&A.
- Why it matters: learn the contracts once, then swap providers, local or cloud, without a rewrite.
- Source: 14:00–14:04 ET, transcripts 20261110-140001.txt, 20261110-140203.txt; shot /shots/140141.jpg
-->

---
layout: "shot"
image: "/shots/140515.jpg"
time: "14:05"
---

# A research paper in, a narrated video out

<!--
- Say: Luis fed a research paper into a .NET desktop app and asked, by voice, for a beginner video. The app built a storyboard he could edit with an agent.
- "Media Studio": one .NET app (Blazor Hybrid), runs locally
- 1 Bring the paper → 2 Read it → 3 Draft with an agent (typed, cited scenes) → 4 A person fixes and saves → 5 Produce (voice, cover, motion, film)
- AI "goes beyond chat"
- The paper (14:06): a research paper on "nested learning". He attached it, then spoke the prompt: "create an introductory video for beginners" with "animations and graphics".
- Demo (14:07): ask for a video "for beginners"; storyboard appears "after a few seconds"; side pane is an event log, "not quite a chat history"
- 14:09: AG-UI + Blazor AI Components. "Scene two is too abstract, make it simpler" → agent updates the storyboard live
- Final video shown was pre-made ("Prepared from the same project you just watched"), not rendered live
- Why it matters: a real AI feature in a .NET app can be a pipeline with a human in the loop, not a chat box.
- Source: 14:04–14:11 ET, transcripts 20261110-140405.txt, 20261110-140601.txt, 20261110-140803.txt, 20261110-141000.txt; shot /shots/140515.jpg
-->

---
layout: "shot"
image: "/shots/141130.jpg"
time: "14:11"
---

# The .NET AI stack: each contract does one job

<!--
- Say: Every hop in that demo is a .NET contract. Pink boxes are new this year; the rest already shipped.
- Pink = new: AgentBoundary (hosts an agent in a Blazor page), AG-UI, DocumentExtractionClient, RoutingChatClient (picks the model per request), Decisions API (typed answer with probabilities)
- Existing: IChatClient, AIAgent, AIFunction, ITextToSpeechClient, IRealtimeClient, IImageGenerator
- Demo mixed cloud (OpenAI, Anthropic Claude, Mistral OCR, GitHub Copilot SDK) and local (PdfPig, Kokoro, Whisper.net, ONNX) providers in one app
- Shared: Microsoft.Extensions.AI, Microsoft.Extensions.DataIngestion
- Bottom layer (14:10), per Luis: Extensions AI, data ingestion, vector data, tokenizers, tensors. IChatClient is "your entry point" to models.
- 14:13 "Follow one request. PDF in, film out: every hop is a .NET contract": DocumentExtractionClient → IngestionDocument → RoutingChatClient + IDecisionClient → AIAgent → AgentBoundary (you edit) → ITextToSpeechClient / IImageGenerator → film. Alt slide: /shots/141306.jpg
- Why it matters: each piece is replaceable on its own, so you can adopt one contract without the rest.
- Source: 14:10–14:14 ET, transcripts 20261110-141000.txt, 20261110-141201.txt; shots /shots/141130.jpg, /shots/141306.jpg
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
- Say: The official OpenAI and Anthropic C# SDKs now plug straight into IChatClient. Pick the model at startup; the rest of the code does not change.
- Code, in plain words: top half builds two clients, each from its own vendor SDK, and calls AsIChatClient(model) to wrap it. Bottom half makes the identical GetResponseAsync call on either one.
- 14:14 ET. Official OpenAI and Anthropic C# SDKs now have native IChatClient adapters
- App code stays the same; only initialization changes. Sample: aka.ms/meai/start
- Luis (14:14): "outside of the initialization code ... your application code stays relatively the same" (light cleanup)
- Packages: Microsoft.Extensions.AI, Microsoft.Extensions.AI.OpenAI, Anthropic
- Code copied from the stream slide (/shots/141458.jpg), "simplified from Planning.cs + FoundryAnthropic.cs"
- Side note: the final film is stitched with plain code, "no AI at that point"
- Local models too (14:16): Luis pointed back to the keynote's Hugging Face system-tray app (Microsoft Store, Windows; built with the llama.cpp team) to discover, download, and serve local models. App name is unclear in the transcript; check it before you say it.
- Why it matters: no vendor lock-in at the call site; switching or A/B testing models is a config change.
- Source: 14:14–14:16 ET, transcripts 20261110-141403.txt, 20261110-141600.txt; shot /shots/141458.jpg
-->

---
layout: "shot"
image: "/shots/141635.jpg"
time: "14:16"
---

# `RoutingChatClient`: your policy picks the model

<!--
- Say: RoutingChatClient picks which model answers each request. You write the policy; a decision model can score the choice when plain rules get messy.
- NEW. The policy is a plain record (LocalOnly, RequireJson, AllowTools, MinimumProbability, ...)
- 1 Policy filters the pool → 2 Decisions API scores what's left → 3 not sure enough: named fallback, or stop
- The router is still just an IChatClient
- Policy defaults on the slide: MaxInputCharacters 24000, MaxOutputTokens 4096, MinimumProbability .7, MinimumMargin .2. Pool: named routes "gpt" (gpt-6.1-sol) and "claude" (claude-sonnet-5-5). "Same router plans the video and draws the cover."
- Luis (14:16): "you can just have a bunch of if statements. You can use unions." But free-text requests make rules hard to manage, so use a decision model.
- Decision models (14:17–14:18): "the OpenAI SDK today offers support for the decision API"; the code example also showed a local decision model on ONNX Runtime. MEAI abstractions for decision-style models are coming "in the next few cycles".
- Why it matters: route cheap, local, or JSON-capable requests to the right model without hard-coding one provider.
- Source: 14:16–14:19 ET, transcripts 20261110-141600.txt, 20261110-141803.txt; shot /shots/141635.jpg
-->

---
layout: "shot"
image: "/shots/141913.jpg"
time: "14:19"
---

# `DocumentExtractionClient`: swap the reader, keep your code

<!--
- Say: A new contract for reading documents. Swap a local PDF reader for cloud OCR or a vision model, and your pipeline code stays the same.
- NEW. One contract: a file in; pages, sections, tables, images out
- Three readers: PdfPig (local), Mistral OCR (cloud), any vision IChatClient
- Packages: Microsoft.Extensions.DocumentExtraction + CommunityToolkit.DocumentExtraction.{PdfPig, Mistral, VisionLanguageModel}
- Keynote caveat still applies: experimental, confirm package availability
- Luis (14:18): "everybody's using the same models, but the true value lies in your data."
- Trade-offs (14:11–14:20): some readers are weak on images or tables; choices differ in "cost, quality, latency". Mistral OCR runs on Foundry or Mistral. The vision option looks at each PDF page as an image.
- Demo numbers (slide): input a 4-page PDF excerpt (original pages 1, 30, 37, 38); output 4 pages, 14 sections, Figure 5, tables as Markdown.
- Also (14:18): MEAI "core foundations and abstractions for these decision-style models" coming
- Flow (14:21): PDF → DocumentExtractionClient → IngestionDocument → chunks. Same whether the reader is Mistral, a chat client, or Azure Document Intelligence.
- Why it matters: RAG and ingestion pipelines stop depending on one OCR vendor.
- Source: 14:18–14:22 ET, transcripts 20261110-141803.txt, 20261110-142000.txt; shot /shots/141913.jpg
-->

---
layout: "shot"
image: "/shots/142237.jpg"
time: "14:22"
---

# No image model: a chat model draws SVG

<!--
- Say: The cover images did not come from an image model. A chat model wrote SVG, the app rendered it to PNG, and that still counts as an IImageGenerator.
- Custom IImageGenerator backed by an IChatClient
- Chat model returns SVG text → app validates it → renders to PNG
- Satisfies the contract: text in, image out. A native image model can drop in later.
- Luis (14:23): "these abstractions and foundations give you the contracts, but then the implementations of what makes the most sense for your application is really sort of up to you."
- Voice (14:24): narration by Kokoro (local model); mic input transcribed locally with Whisper, or via OpenAI realtime
- Tools: a C# method exposed as a tool; MCP C# SDK is the other way. Session later covers SDK 2.0 and "serving skills over MCP".
- The tool in the demo (14:25): the "media draft" tool, a standard C# method that authors the scenes.
- Why it matters: you can implement a contract any way you like; the rest of the app does not know or care.
- Source: 14:22–14:26 ET, transcripts 20261110-142202.txt, 20261110-142400.txt; shot /shots/142237.jpg
-->

---
layout: "shot"
image: "/shots/142657.jpg"
time: "14:26"
---

# Put an agent in your UI: the agent proposes, the person decides

<!--
- Say: Two new pieces connect an agent to a real UI: the AG-UI protocol with a new C# SDK, and Blazor AI components that host the agent in your page.
- NEW: AG-UI C# SDK (just released) — agent streams typed events (run, text, tool call, state change), works with any front end
- NEW: Blazor AI components — <AgentBoundary> hosts an agent; the person edits; Save persists
- Agent Framework on any IChatClient, or the GitHub Copilot SDK
- Packages on the slide: AGUI.Server, AGUI.Client, Microsoft.AspNetCore.Components.AI. Tagline: "Agent ⇄ AG-UI events ⇄ Blazor UI: the agent proposes, the person decides."
- Luis (14:26): Agent Framework "can orchestrate across different agent types"; Blazor AI components "natively use AGUI".
- Loop (14:27): request → UI → AG-UI events → agent → tools generate scenes → changes show in the UI in real time.
- Why it matters: agent output lands as editable app state, not chat text you copy and paste.
- Source: 14:26–14:28 ET, transcript 20261110-142602.txt; shot /shots/142657.jpg
-->

---
layout: "statement"
---

"The best AI demo today, because it wasn't a chatbot."

<!--
- Say: The host read a chat comment on stream: this was the best AI demo of the day because it was not a chatbot.
- 14:29 ET. Read on stream by the session host: "Kevin said that this was the best AI demo today because it wasn't a chatbot."
- Confirm this was your post before claiming it on stage (transcript says only "Kevin")
- Host continued: "It was actually like full-fledged"; companies say "build AI in" and "we don't want a chatbot."
- Q&A (14:30), "What would your stack be?" Luis builds on the bare building blocks himself, but recommends you start with the Copilot SDK or a "batteries included" agent harness, then "drop down" when needed. (Inference: the harness heard as "map harness" is likely MAF, Microsoft Agent Framework.)
- Deploy (14:30): Aspire for observability, Container Apps, Functions, or Foundry: "at the end of the day, it's just .NET code."
- Luis's wrap-up (14:28): talk to any model, choose the model per request, bring your context, go multimodal, expose tools, and build agent UIs with AG-UI and Blazor AI components.
- Follow-ons: aka.ms/meai/start, aka.ms/openai/start; MCP C# SDK session (Stephen Halter), agentic UI with Blazor (Daniel Roth)
- Why it matters: the bar for "AI feature" is moving from chat windows to workflows.
- Source: 14:28–14:31 ET, transcripts 20261110-142805.txt, 20261110-143004.txt
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
- Say: Gerald Versluis from the MAUI team says Copilot changed how fast they ship. The big change is the move from Mono to CoreCLR.
- Time: 2:30 PM ET slot (Gerald started ~14:33). Speaker: Gerald Versluis, software engineer on the .NET MAUI team.
- 14:34: 1,600 PRs last month, "an absolute record" (keynote stat slide)
- Last year: "400, 500 PRs a month on a good month." Gerald: "I'm an engineer. I don't have to sugarcoat this." (transcript: "sugar code")
- Partners: Syncfusion (engineers fix issues in dotnet/maui + free toolkit), Uno Platform (Android API bindings, co-maintains SkiaSharp), Avalonia (MAUI on Linux)
- 14:50: native passkeys (generate + validate); `dotnet run`, `test`, `watch` now work for MAUI with an interactive platform prompt (full session at 7:30 PM)
- Not on our slides (14:46–14:50): long-press gesture recognizer; badges on tabs and toolbar items; a new C# UI (no XAML) template; Material 3 with one property; handlers now public; Maps clustering (one property, cluster click event) and custom pins via a pin image source.
- Coming up: Mono → CoreCLR · NativeAOT startup numbers · XAML source gen on by default · C# expressions in XAML · MAUI Inspector + incremental hot reload · MAUI Labs · the support-policy warning.
- Live glitch (14:38–14:40): his display dropped mid-chart; he recovered with "the charm of doing things live".
- Why it matters: MAUI 11 is a runtime change plus a long list of small fixes people asked for for years.
- Source: 14:32–14:51 ET, transcripts 20261110-143201.txt, 20261110-143405.txt, 20261110-144003.txt, 20261110-144600.txt, 20261110-144802.txt, 20261110-145004.txt; shot /shots/143420.jpg
-->

---
layout: "statement"
---

Mono → CoreCLR: "you won't really see, but you will feel."

<!--
- Say: In .NET 11, every MAUI app runs on CoreCLR instead of Mono. You will not see it in the UI, but you will feel it in speed and tooling.
- Gerald Versluis, 14:37 ET: "the biggest change to .NET MAUI"
- Full quote: "the biggest change to .NET MAUI, which unfortunately you won't really see, but you will feel"
- Same runtime as ASP.NET Core and Azure on every MAUI platform
- Platforms (14:37): Android, iOS, Mac Catalyst, Windows all run on CoreCLR with .NET 11.
- Tooling (14:41–14:42): tools like the profiler needed extra work to support Mono; on CoreCLR MAUI gets those tooling improvements, and all .NET 11 performance work "will now automatically be available for .NET MAUI".
- Demo app: David Ortinau's Barista Notes (screenshot /shots/143737.jpg)
- Avalonia backend is now an option in the .NET MAUI templates for .NET 11
- Why it matters: one runtime means one set of perf gains and one set of diagnostics tools across all your .NET apps.
- Source: 14:36–14:42 ET, transcripts 20261110-143602.txt, 20261110-144003.txt, 20261110-144200.txt; shot /shots/143737.jpg
-->

---
layout: "shot"
image: "/shots/144153.jpg"
time: "14:41"
---

# MAUI on Android, NativeAOT: 974 → 280 ms median startup

<!--
- Say: On a Pixel 5, NativeAOT cut MAUI's median cold start from about 974 ms to 280 ms. Android NativeAOT is still experimental.
- BaristaNotes, Pixel 5, Android 14, .NET 11 RC2, 30 launches per cell
- MAUI median cold start: Full R2R 973.5 ms → NativeAOT 280 ms (C# Android Views: 181 ms)
- Caveat on the chart: MAUI NativeAOT p90 is still 908 ms
- Package: 45.65 MiB (Full R2R) → 30.40 MiB (NativeAOT)
- "Android NativeAOT is experimental" (chart footnote)
- Numbers from the chart only; not spoken in the transcript
- iOS (iPhone 15 Pro, /shots/144228.jpg): MAUI median 490.3 → 321.8 ms with NativeAOT (C# UIKit 185.9); package 58.86 → 42.01 MiB
- Why RC2 (14:37): "GA is rolling out while we speak"; Gerald expects GA numbers to be very close.
- Gerald (14:38): MAUI will always be a bit slower than the platform bindings directly: "It's just a thin layer on top."
- Why it matters: startup time is the first thing mobile users feel; NativeAOT is the lever to try.
- Source: 14:37–14:42 ET, transcripts 20261110-143602.txt, 20261110-143800.txt; shots /shots/144153.jpg, /shots/144228.jpg
-->

---
layout: "statement"
---

XAML source generation on by default: Debug behaves like Release.

<!--
- Say: In .NET 11, MAUI turns XAML into C# at build time by default. Your Debug build now behaves like your Release build.
- 14:42 ET. XAML compiles to C# at build time with source generators
- Before: XAML compilation produced IL, "already better than interpreting at runtime". Now source generators produce C# you can read.
- No more "trimmed from the release build and boom, your app blows up in production"
- Gerald (14:43): faster, "no XAML parsing at runtime"; build errors "you can understand"; you can set breakpoints in the generated code.
- Also (14:44): implicit XAML namespaces cut page ceremony to one line. "I love my XAML but there's one thing that I love more than XAML: it's less XAML." (light cleanup)
- Already listed on the keynote MAUI slide; this is the "why"
- Why it matters: fewer "works in Debug, crashes in Release" bugs, and you can debug XAML like normal C#.
- Source: 14:42–14:44 ET, transcripts 20261110-144200.txt, 20261110-144403.txt
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
- Say: MAUI 11 lets you write small C# expressions right inside XAML bindings, so most value converters go away.
- Code, in plain words: before, flipping a bool needed a converter class, a resource, and a long binding. In .NET 11 you write {!IsBusy}. The last four lines show other forms: string interpolation, math, null fallback, and boolean logic.
- 14:45 ET. Inline C# replaces most value converters
- Before also needed a whole InverseBoolConverter : IValueConverter class (Convert + ConvertBack)
- Gerald (14:45): "Every project basically has this." Now: "is enabled, curly braces, not is busy, boom, that's everything that you need to do." (transcribed speech, light cleanup)
- Also possible (14:45): string interpolation, simple math, and a click handler inline.
- Code copied from the stream slide /shots/144523.jpg
- Why it matters: less boilerplate per page, and one less class to test for every trivial conversion.
- Source: 14:44–14:46 ET, transcripts 20261110-144403.txt, 20261110-144600.txt; shot /shots/144523.jpg
-->

---
layout: "shot"
image: "/shots/145306.jpg"
time: "14:53"
---

# .NET MAUI Inspector: see inside your running app

<!--
- Say: The MAUI Inspector shows the live visual tree of a running app, lets you edit properties live, and Copilot can drive it through MCP.
- Live visual tree, properties, screenshot; record, replay and assert UI flows
- Copilot drives the same session through MCP tools
- Runs in VS Code, the GitHub Copilot app, Copilot CLI, any browser
- Part of MAUI Labs: github.com/dotnet/maui-labs
- Gerald (14:52): click a node to highlight it on screen, and the other way around; a live property editor changes values "without having to stop and kind of like restart".
- Also (14:52): incremental XAML Hot Reload keeps state (no lost navigation stack or values), via dotnet watch
- Hot reload detail: works with dotnet watch now, "also coming to Visual Studio and Visual Studio Code".
- Why it matters: a faster inner loop for you, and a way for agents to see and test the real UI.
- Source: 14:52–14:54 ET, transcript 20261110-145201.txt; shot /shots/145306.jpg
-->

---
layout: "shot"
image: "/shots/145430.jpg"
time: "14:54"
---

# MAUI Labs: 10+ experiments to try

<!--
- Say: MAUI Labs is where the team ships experiments fast: a CLI, DevFlow for agent testing, on-device AI, and new Linux and WPF backends.
- github.com/dotnet/maui-labs. "Who knows, some might graduate."
- DevFlow: like Playwright, for MAUI apps and agents
- DevFlow detail (14:55): agents used to take simulator screenshots and guess click coordinates. DevFlow puts a small agent inside your app, so it can read the visual tree, click a button, or read an entry's value.
- MAUI CLI, Essentials.AI (on-device chat + embeddings), `maui ai init` (skills + MCP)
- MAUI CLI (14:57): set up and check your environment ("MAUI doctor"), drive emulators, JSON output that agents can read. Also "a couple of dozens" of agent skills.
- New backends: Linux (GTK) and WPF
- `dotnet new mauitest` for device tests
- Why it matters: agents can now build, run, and verify MAUI apps without guessing from screenshots.
- Source: 14:53–14:57 ET, transcripts 20261110-145201.txt, 20261110-145405.txt, 20261110-145602.txt; shot /shots/145430.jpg
-->

---
layout: "shot"
image: "/shots/145752.jpg"
time: "14:57"
---

# Heads up: MAUI 10 support ends May 2027

<!--
- Say: MAUI support is not the same as .NET support. Each MAUI version gets 18 months, so MAUI 10 ends May 2027 even though .NET 10 is LTS.
- Each MAUI version is patched for 18 months: support ends 6 months after the next major ships
- MAUI 10 → May 2027, even though .NET 10 itself is LTS. MAUI 11 → May 2028 (assumes .NET 12 ships Nov 2027)
- aka.ms/maui-support-policy
- Also (14:56): Essentials.AI uses on-device models (Apple Intelligence, Gemini Nano)
- Why (14:58): MAUI builds "on top of third-party tools that have different support timelines".
- Gerald (14:57): people told him their manager won't allow STS versions: "well, have I got good news for you, you need to update." (light cleanup)
- Gerald (14:58): "Every .NET MAUI version has 18 months, period. So get on .NET 11 right now."
- Q&A "best IDE for MAUI?" → "What's an IDE?" Team "has not been in an IDE for a while", building toward the CLI
- Q&A detail (14:59): the team works mostly in the GitHub Copilot app; Gerald uses VS Code on a Mac; Visual Studio is fine too.
- Why it matters: if you ship MAUI on .NET 10, plan the .NET 11 upgrade before May 2027.
- Source: 14:56–15:00 ET, transcripts 20261110-145602.txt, 20261110-145800.txt; shot /shots/145752.jpg
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
- Say: Three people from the Dev Kit team explain how one unhappy team with many agents led to a rewrite of C# Dev Kit.
- Time: 3:00 PM ET slot (started ~15:01). On stage: Drew (Noakes), Jake (not on the agenda; last name not given on stream), Emanuel (Fernandez Dell'Oca).
- Drew (15:01): "it's not really an incremental update. We've rewritten almost all of it. It's a completely new architecture, a completely new approach."
- Drew: the ideas are "more broadly applicable than even in just C# IDE"; they help when you run many copies of tools at once with agents.
- Coming up: the "VS Code is terrible" origin story · .lscache · Roslyn/Orleans/Aspire load times · BuildX · MSBuild Coordinator · `dotnet buildx` on OrchardCore · the 20–40% agent-loop stat.
- Why it matters: the fixes start in Dev Kit but move into Roslyn, MSBuild, and the SDK, so every .NET tool gets them.
- Source: 15:00–15:03 ET, transcripts 20261110-150002.txt, 20261110-150204.txt
-->

---
layout: "statement"
---

"VS Code is terrible." It was 15 agents and hundreds of MSBuild workers.

<!--
- Say: A team said VS Code was terrible. The real cause: up to 15 agents, each kicking off builds, ate all the memory on the machine.
- 15:03 ET. Dev Kit 11 origin story
- An internal team kept saying VS Code + C# Dev Kit "were terrible"; their VP escalated; "crashing on their machine"
- Timeline (15:02): "about nine months ago". Dumps and the usual diagnosis found nothing, so Jake went to sit with the team.
- Reality: "5, 10, 15" agents solving GitHub issues on Macs with 256 GB RAM, and "hundreds and hundreds of MSBuild workers"
- Jake (15:04): "there was no resources available on their machine to do VS Code, to do Teams, to do Chrome, to do anything". Later (15:10): "their screen was completely locking up".
- Why Dev Kit 11 was re-architected for many agents on one machine
- The fix (15:04): a build queue that runs the agents' builds serially. Build throughput for all agents went UP — "the oversaturation of build nodes was actually hindering throughput."
- Why it matters: with agents, your tools run many times in parallel; tool overhead becomes the bottleneck.
- Source: 15:02–15:05 ET, transcripts 20261110-150204.txt, 20261110-150401.txt, 20261110-151002.txt
-->

---
layout: "statement"
---

The trick: cache the build's project info. `.lscache`.

<!--
- Say: Builds already compute everything an IDE needs to know about a project. Dev Kit 11 saves that to a cache file and reads it back in milliseconds.
- 15:06 ET. The build's pre-compile step (evaluate + resolve inputs, globs, disk scans) is written to a .lscache file
- What is in that step (15:06): find source files from globs, resolve package references (and which target), language version, target frameworks.
- "Not really that revolutionary to write a cache file to disk"
- Cheap to write: "we've got all that information during the build anyway."
- Reading it: "a few milliseconds". Asking MSBuild: "hundreds, maybe thousands of milliseconds"
- Who needs it: the IDE (Roslyn language services, IntelliSense), dotnet watch, dotnet test. Jake (15:08): one build "can be dozens of things", scaling with project count, and tools were not sharing.
- (My inference, not stated on stream: likely a big part of the keynote's ~77% faster workspace load)
- Next (15:16): reading/writing .lscache lives in the Roslyn repo (open source) and is going into the SDK, so "every build is capable of writing these files" and all tools benefit. "From a faster Dev Kit to a faster development loop."
- Why it matters: one build can feed the IDE, tests, and agents, instead of each tool asking MSBuild again.
- Source: 15:06–15:17 ET, transcripts 20261110-150603.txt, 20261110-150800.txt, 20261110-151605.txt
-->

---
layout: "shot"
image: "/shots/150930.jpg"
time: "15:09"
---

# Opening the Roslyn repo: 89 s → 16 s

<!--
- Say: Opening the Roslyn repo in VS Code went from 89 seconds to 16. Orleans and Aspire show the same drop, about 77%.
- Dev Kit v3 → v11, warm load, lower is better
- dotnet/roslyn (398 projects): 89.0 → 15.9 s
- dotnet/orleans (155 projects): 62.0 → 17.1 s
- microsoft/aspire (407 projects): 87.9 → 19.9 s
- ~77% faster. Intel Xeon Platinum 8370C, 8 cores, Windows 11 x64
- Numbers from the stream chart
- Drew (15:09): the difference between "making a cup of tea or checking your email" and "just getting straight on with your work". Smaller solutions "will feel much closer to instant".
- Memory (15:10): "80% less memory ... you can fit five C# Dev Kits in the space of one from before"
- Drew (15:10): "one human and four agents on your machine, you're now using roughly the same resources" as one user before.
- Why it matters: big solutions open fast enough to jump between an agent session and the editor.
- Source: 15:08–15:11 ET, transcripts 20261110-150800.txt, 20261110-151002.txt; shot /shots/150930.jpg
-->

---
layout: "shot"
image: "/shots/151107.jpg"
time: "15:11"
---

# BuildX: skip, copy, or build

<!--
- Say: BuildX is a new incremental build in Dev Kit 11. It builds only what changed, skips the rest, and copies outputs without full MSBuild work.
- New build integration in Dev Kit 11
- In Dev Kit today; the team wants to bring it to the command line and other places (15:10).
- Implementation-only edit, public API unchanged: build only H, skip unchanged projects, copy outputs where needed
- How (15:12): the per-project "does this need a build?" check takes "a couple of milliseconds"; file copies happen "without having to invoke any of the machinery of MSBuild".
- Confirmed (15:12): BuildX is behind the keynote number. Aspire.slnx, 407 projects: single change 36.1 → 2.1 s (−94%), median of 5
- No-op build: 34.4 → 0.9 s (−97%); the old 34.4 s was "almost entirely overhead"
- Alt chart slide: /shots/151239.jpg
- Demo (15:14): the agent's build already wrote the cache files, so VS Code opens with tests discovered and IntelliSense ready; the test re-run uses BuildX; ".lscaches are also shared across worktrees"
- Demo setup (15:13): Emanuel started in the GitHub Copilot app on the dotnet/eShop repo.
- Why it matters: most of a typical incremental build is overhead; BuildX removes it.
- Source: 15:10–15:16 ET, transcripts 20261110-151002.txt, 20261110-151204.txt, 20261110-151401.txt; shots /shots/151107.jpg, /shots/151239.jpg, /shots/151344.jpg
-->

---
layout: "shot"
image: "/shots/151821.jpg"
time: "15:18"
---

# MSBuild Coordinator: one build budget per machine

<!--
- Say: Even lighter builds still fight for CPU when many agents run. The MSBuild Coordinator gives the whole machine one shared node budget.
- 5, 10, 20 agent builds each asking for N nodes = more than the machine has
- Coordinator: a shared node budget; some builds run, the rest queue
- "Cheaper instances help. Growing concurrency still needs a budget."
- Opt-in, not default; participating builds only
- Credits (15:18 + slide footer "Dustin & Ema"): implemented by Dustin (Campbell, from the 12:00 PM C# session with Mads); Emanuel is improving it.
- This is the product version of the origin story's build queue
- Also (15:20): "we want to prioritize the human" — the coordinator decides which builds go first. If an agent's build already produced the .lscache, the IDE can skip its own "design-time build".
- Priority idea (15:19–15:20): if you are in VS Code, "you probably care about that build over others"; the team could infer focus from "what app you're looking at". Still work in progress.
- BuildX CLI demo on OrchardCore follows
- Why it matters: agent builds should not freeze the machine you are typing on.
- Source: 15:18–15:21 ET, transcripts 20261110-151801.txt, 20261110-152004.txt; shot /shots/151821.jpg
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
- Say: From the command line, buildx confirmed 215 projects up to date in under half a second. After a core change, it built 2 projects and copied outputs for 201.
- Output, in plain words: first run, nothing changed, so buildx checks all 215 projects and stops in 388 ms. Second run, after an edit to a core abstractions project: it compiles only 2 projects, copies outputs to 201 dependents ("accelerated"), and skips 12.
- 15:22 ET. No-op build of 215 projects: 388 ms
- One change in a core project: 2 projects built, 201 "accelerated" (outputs copied), 12 skipped
- Demo (15:22): the dependents "were not built"; "we copy the binaries that abstractions produced" to them.
- Caveat: that 13.4 s run included a NuGet restore and starting the buildx server
- Q&A (15:28): buildx sits next to `dotnet build`, like `docker buildx` next to `docker build`. Starts as a separate tool, being moved into the SDK; "I do have a dream that it replaces it."
- On the "X" (15:28): "Could mean experimental, could mean extended" — "a playground for us to do new stuff".
- Output copied from the stream terminal (/shots/152232.jpg); a line with a local user path left out
- Exploring, not committed (15:24): agents are trained on `dotnet build` / `dotnet test`, so if an agent is detected those commands could use the faster paths. Optimizations that might surprise a human are fine for an agent if a log message says "this optimization has been applied" — the agent will read the docs.
- Why it matters: a change deep in the graph no longer means recompiling every dependent project.
- Source: 15:20–15:30 ET, transcripts 20261110-152004.txt, 20261110-152202.txt, 20261110-152404.txt, 20261110-152803.txt; shot /shots/152232.jpg
-->

---
layout: "statement"
---

20–40% of your agent loop is running .NET tools.

<!--
- Say: The team says 20 to 40 percent of an agent's loop is spent waiting on .NET tools. Shrink that, and the agent spends more time on the actual work.
- 15:26 ET: "in your agent loop, 20 to 40% of that time is actually running .NET tools"
- Ideas to shrink it: infer which tests actually need to run; get errors from a background LSP instead of a build
- Why rules alone fail (15:26): repo instructions for agents are "one compact away"; then the agent goes back to plain build and test. So the tools should take the agent's intent and do it the cheaper way.
- Side benefit (15:26): "Saving your battery life if you're working on a laptop."
- Worktrees: "Don't make the next person start over." A new worktree reuses the project data (and maybe binaries) an agent's build already wrote. Broader reuse is "direction", not shipped (/shots/152736.jpg)
- Scale (15:28): worktree creation now happens "dozens, potentially hundreds of times a day".
- Also floated (15:30): a "TestX" that builds with BuildX and maybe optimizes test discovery. Idea only.
- Why it matters: faster tools mean faster agent iterations and less waiting for you.
- Source: 15:26–15:31 ET, transcripts 20261110-152601.txt, 20261110-152803.txt, 20261110-153000.txt; shot /shots/152736.jpg
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
- Say: Chet Husk explains -mt: MSBuild runs its workers as threads in one process instead of many processes, and that makes builds faster.
- Time: 3:30 PM ET slot (Chet started ~15:31). Speaker: Chet Husk. Host intro: "Chatty Chet", his third appearance of the day.
- Goal (15:31): faster builds on "your machine, your CI machine, your agent's context" "while not sacrificing correctness or the extensibility".
- Test project (15:32): OrchardCore, about 100 projects, each with at least two target frameworks: "actually more like 300 configurations" for MSBuild (15:36).
- Coming up: the warm and cold numbers · the 11.0.200 default target and how -mt works · the shared current-directory problem · a task code sample, analyzer, and migration plugin.
- Why it matters: one flag, no code changes for most builds, and it is aimed to be the default soon.
- Source: 15:30–15:37 ET, transcripts 20261110-153000.txt, 20261110-153202.txt, 20261110-153601.txt; shot /shots/153105.jpg
-->

---
layout: "shot"
image: "/shots/153347.jpg"
time: "15:33"
---

# `-mt` warm incremental: −68% on Windows, −13% on Linux

<!--
- Say: On a no-change OrchardCore rebuild, -mt cut Windows build time by 68%. Linux gained 13%, because its normal build is already faster.
- OrchardCore warm incremental. Windows 54.58 → 17.36 s (−68.2%). Linux 25.47 → 22.13 s (−13.1%)
- Cold build (per notes agent, not on this chart): −23.5% Windows, −11.9% Linux
- Verified on the separate cold-build chart /shots/153242.jpg: Windows 116.05 → 88.74 s (−23.5%), Linux 96.15 → 84.74 s (−11.9%). Chet: "no other changes in .NET 11 aside from adding the -mt flag".
- Chet (15:33): warm incremental is "the truest representation of the overhead ... of the MSBuild engine". Unlike BuildX, "we're not skipping any work here."
- DIFFERENT from the keynote's −37% (28.4 → 17.9 s, "ASP.NET's shared hardware, 100 projects"). The −mt time is about the same (~17-18 s); the "Normal" baseline differs. Don't quote both as the same measurement.
- Windows gains much more than Linux: Linux's normal build is already faster
- More to come (15:52): many OrchardCore projects are web projects that pack during build; "entire swaths of the build that we have not yet enlightened and we're already seeing these numbers"
- Why it matters: the biggest win is the inner loop you run all day, not only CI.
- Source: 15:32–15:34 ET, transcripts 20261110-153202.txt, 20261110-153404.txt, 20261110-155200.txt; shots /shots/153347.jpg, /shots/153242.jpg
-->

---
layout: "statement"
---

Target: `-mt` on by default in SDK 11.0.200 — this winter.

<!--
- Say: The MSBuild team is targeting -mt as the default in SDK 11.0.200 this winter. You can turn it on today with the -mt flag.
- 15:34 ET: "We are targeting making this behavior the default in 11.0.200. So this winter's build of .NET 11." (Targeting, not promised.)
- Console and library builds are already "enlightened" (multithread-compatible); next: pack, publish, web apps
- Why faster: less duplicated engine work, fewer task handoffs, reusable server state
- Built on a new long-lived MSBuild server daemon, to be reused for future caching
- Real use (15:54): -mt has run on the .NET VMR (the monorepo that builds .NET) since .NET 10 — "upwards of 20 minutes of savings for some of our long pole builds just with this one flag"
- Pattern: narrow agent inner loops + long exhaustive validation in CI; -mt helps both
- How (15:40): "each of the worker nodes is just a thread instead of an entire process." In-process messages replace IPC; runtime and task assemblies load and JIT once.
- The catch: "Tasks today get to pretend like they are in completely separate processes that they own" (process state). Custom tasks need changes — see next slide.
- Compatibility (Q&A, 15:58): "you should just be able to turn multi-threaded on for the vast majority of builds." Some .NET Framework MSBuild features do not work with -mt, but "we do bail out with a nice message".
- Side win (15:52): an IPC fix for binlog messages, coming in the winter release, also speeds up normal (non -mt) MSBuild for some projects.
- Slow builds (Q&A, 15:58): "it's often not a single task that makes your build slow. It's something about the layout of your build" and how interconnected the projects are
- Profile it (16:00): get binlogs with `-bl` on any build command; open them in Kirill Osenkov's Structured Log Viewer or the binlog MCP the tooling team shipped in VS Code ("I believe"). Factor out bottleneck projects for more parallelism.
- Why it matters: try -mt now on your repo so problems surface before it becomes the default.
- Source: 15:34–15:59 ET, transcripts 20261110-153404.txt, 20261110-154003.txt, 20261110-155200.txt, 20261110-155403.txt, 20261110-155802.txt
-->

---
layout: "shot"
image: "/shots/154300.jpg"
time: "15:43"
---

# Task authors: resolve paths against `TaskEnvironment`

<!--
- Say: In -mt, all projects share one process, so they share one current directory. Tasks must resolve paths through TaskEnvironment, not the process.
- "One process. One current directory." Under -mt, two projects share one process CWD
- Speaker's "favorite example": Environment.CurrentDirectory — a relative "input.txt" can resolve to the wrong project
- Chet (15:42): change it once and "it changes it for all threads"; "poking at that process level state is one of the cardinal sins of any multi-threaded system".
- Fix: resolve paths against TaskEnvironment, not the process
- TaskEnvironment is the "state bundle, a context object" (15:42) that gives a task safe access to paths, environment variables, and process start.
- Compatibility (15:44): tasks marked MSBuildMultiThreadableTask run in-process. Unmarked tasks still work — they run in a short-lived "sidecar" TaskHost process with isolated process state. So old tasks keep working. (My inference: they won't get the in-process speedup.)
- Chet (15:45) on sidecars: "there is still some startup cost for builds that don't use only enlightened tasks"; the TaskHost is destroyed at the end of the build.
- Q&A (15:59): a common hurdle is tasks that do their own file I/O, for example asking for the temp path directly; that may not work consistently in -mt.
- Why it matters: if you ship custom MSBuild tasks, this is the change that keeps them correct and fast under -mt.
- Source: 15:41–15:59 ET, transcripts 20261110-154003.txt, 20261110-154200.txt, 20261110-154402.txt, 20261110-155802.txt; shot /shots/154300.jpg
-->

---
layout: "default"
codeSize: "19"
---

# Make a task `-mt`-ready: two changes

```diff
- public sealed class CountFileLines : Task
+ [MSBuildMultiThreadableTask]
+ public sealed class CountFileLines : Task, IMultiThreadableTask
  {
+     public TaskEnvironment TaskEnvironment { get; set; } =
+         TaskEnvironment.Fallback;
      public override bool Execute()
      {
-         LineCount = File.ReadLines(SourceFile).Count();
+         AbsolutePath path = TaskEnvironment.GetAbsolutePath(SourceFile);
+         LineCount = File.ReadLines(path).Count();
          return true;
      }
  }
```

<!--
- Say: Two changes make a task -mt ready: mark it as multithreadable, and resolve file paths through TaskEnvironment. The task's inputs and outputs stay the same.
- Code, in plain words: before, a plain Task reads SourceFile as-is, so a relative path resolves against the shared process directory. After, the class has the attribute and IMultiThreadableTask, gets a TaskEnvironment property, and turns SourceFile into an absolute path before it reads the file.
- 15:47 ET. Inputs/outputs stay the same
- 1) Add the marker attribute + interface. 2) Resolve relative paths through TaskEnvironment
- Chet (15:46) on the attribute: "We never do this implicitly. It has to be an explicit author decision." If the task does nothing fancy, the attribute alone can be enough; the interface is for paths, environment variables, and process start.
- Even simpler (15:48, "freshest" MSBuild bits): typed binding, e.g. ITaskItem<FileInfo>, so the engine resolves the path and the task code shrinks — "a more declarative path" for task authors
- Typed binding supports FileInfo, DirectoryInfo, and an MSBuild AbsolutePath type (15:49).
- Analyzer (15:50): Microsoft.Build.TaskAuthoring.Analyzer, ~12 Roslyn rules (some -mt specific); fixers planned. On stream: PackageReference version 18.13.0, PrivateAssets="all"; .editorconfig `msbuild_task_analyzer.run_mt_analyzers_on_all_tasks = true`
- What the analyzer flags (15:50): starting processes yourself, manual file I/O, file path traversals; it points you to the safe versions.
- The MSBuild repo also has an agent plugin the team uses to migrate the SDK's built-in tasks: dotnet/msbuild → plugins/mt-migration. Sample prompt on stream: "Migrate CountFileLines for MT execution. Trace helpers. Preserve outputs and error behavior. Run the analyzer and test distinct project environments."
- Links (15:56): learn.microsoft.com/visualstudio/msbuild/update-task-multithreaded · nuget.org/packages/Microsoft.Build.TaskAuthoring.Analyzer · github.com/dotnet/msbuild/tree/main/plugins/mt-migration · aka.ms/msbuild/performance-dashboard (PerfStar)
- Code copied from the stream slide (/shots/154714.jpg)
- Why it matters: enlightened tasks run in-process and fast; every task you migrate removes a sidecar process from the build.
- Source: 15:45–15:57 ET, transcripts 20261110-154402.txt, 20261110-154604.txt, 20261110-154801.txt, 20261110-155003.txt, 20261110-155605.txt; shot /shots/154714.jpg
-->

---
layout: "session"
num: 10
time: "4:00 PM"
speakers: "Maddy Montaquila, Damian Edwards"
---

# What's New in Aspire for .NET Developers

<!--
[Session 10]
- Opening (16:02): "The Opus Moment" pushed the team to lean into agents. "Aspire is this deterministic thing that can actually orchestrate your stack under the hood. So you can have all this magic with agents but keep it on guard rails."
- Naming: "not called dotnet aspire, it is just aspire"
-->

---
layout: "shot"
image: "/shots/160528.jpg"
time: "16:05"
---

# Aspire: ~50k → ~90k developers a month, growth from VS Code and the CLI

<!--
- Say: Aspire's monthly engaged developers nearly doubled in a year, and the growth came from VS Code and the Aspire CLI, including coding agents.
- Nov 2025 ~50k → Nov 2026 ~90k (+40k), deduplicated across tools
- "All if not more of that growth has been from both VS Code and our CLI itself"
- People "enter from Claude Code and Copilot and Codex and the CLIs and the desktop apps"; polyglot repos in VS Code
- Why it matters: Aspire is increasingly driven from terminals and agents, not only from Visual Studio.
- Source: 16:05 ET, transcript 20261110-160403, /shots/160528.jpg
-->

---
layout: "shot"
image: "/shots/160605.jpg"
time: "16:06"
---

# #1 thing orchestrated with Aspire: JavaScript

<!--
- Say: The number one integration people pull into Aspire isn't a .NET thing — it's JavaScript.
- Top 5 hosting integrations: JavaScript, SQL Server, Redis, PostgreSQL, Azure Storage
- JavaScript "includes like TypeScript, Node, Vite, a bunch of the different runtimes"
- Azure Storage is the #1 cloud integration; the community also uses Aspire with AWS, GCP, Docker Compose, Kubernetes
- AppHost: most author it in C#, "but you can also author in TypeScript and other languages coming soon"
- Why it matters: Aspire is polyglot now; it's not only for all-.NET stacks.
- Source: 16:06 ET, transcript 20261110-160600, /shots/160605.jpg
-->

---
layout: "shot"
image: "/shots/160947.jpg"
time: "16:09"
---

# Aspire this year: one-file AppHosts, AOT dashboard, `aspire deploy`

<!--
- Say: In one year Aspire got a single-file AppHost, a Native AOT dashboard, and a real deploy story.
- Shipped for .NET devs (stream slide): file-based AppHosts (a single .cs file, no project); dashboard + DCP bundled in the CLI so every machine runs one version; Native AOT dashboard (faster startup, no separate runtime); Blazor WebAssembly in the AppHost (preview); EF Core migrations from the dashboard (preview)
- Deploy (16:08): "This time last year, there really wasn't a deploy story like this." Now `aspire deploy` plus a pipeline model in the AppHost; steps run during publish, deploy, even run
- Targets: Azure, Docker Compose, vanilla Kubernetes, "deploy via SSH to a VM"; "The Amazon folks ship the AWS support"
- Agent support evolved: Copilot in the dashboard → an MCP → "replaced the MCP with skills"
- EF Core (16:10): the migrations integration "was actually contributed by the EF Core team". `aspire deploy` produces an EF bundle; locally you can run a migration or rollback from the dashboard
- Why it matters: one AppHost file now goes from local run to deployment, on many clouds.
- Source: 16:08–16:10 ET, transcript 20261110-160802, /shots/160947.jpg
-->

---
layout: "default"
codeSize: "20"
---

# A whole AppHost in one `.cs` file

```csharp
#!/usr/bin/env dotnet
#:sdk Aspire.AppHost.Sdk@13.6.4
#:package Aspire.Hosting.Azure.PostgreSQL
#:package Aspire.Hosting.Redis
#:package Aspire.Hosting.JavaScript
#:package Aspire.Hosting.Maui
#:project ./BingoBoard.Admin
#:include ./apphost/*.cs

var builder = DistributedApplication.CreateBuilder(args);
```

<!--
- Say: The AppHost doesn't need a project anymore. It's one apphost.cs file with directives at the top.
- Demo: the "Aspire Fridays" bingo app (16:12 ET)
- #:sdk picks the Aspire AppHost SDK; #:package pulls integrations; #:project references projects; #:include pulls in more .cs files (the file-based app #include from the keynote)
- Excerpt: the stream file has more #:package lines (Azure.AppContainers, Azure.Redis, Docker, Yarp, DevTunnels, Browsers, EntityFrameworkCore) and a second #:project
- On stream: the file can sit "above the projects you're orchestrating"
- Why it matters: less ceremony — no AppHost project to maintain.
- Source: 16:12 ET, transcript 20261110-161201, code copied from /shots/161241.jpg
-->

---
layout: "shot"
image: "/shots/161453.jpg"
time: "16:14"
---

# Clone, run, and the dashboard asks for the missing secrets

<!--
- Say: When someone clones your repo and runs it, Aspire's dashboard now pops up and asks for any secrets it needs.
- "Aspire Secrets": abstracts .NET User Secrets, which "has always been what we've used under the hood to keep API keys, passwords, etc. out of your source"
- Dialog "Set unresolved parameters" with a "Save to user secrets" checkbox; resources that need the value "actually wait on them"
- Same demo: "polyglot debugging" — the debugger attaches to the C# apps and the Vite app; "not just .NET and JavaScript but also Go", and Python
- Why it matters: new team members get a working app from a clone without a setup doc for secrets.
- Source: 16:14 ET, transcript 20261110-161403, /shots/161453.jpg
-->

---
layout: "statement"
---

"So we put a terminal in the dashboard."

<!--
- Say: Terminals are the thing now, so the Aspire dashboard now has a full terminal emulator in it.
- "We built maybe the most fully featured terminal emulator on the planet" — Mitch Denny's "opus moment": a terminal emulator plus a .NET library for building TUIs, and a web-based terminal host
- Demo: a "file-based app, single C# file terminal app" that "compiles down with native AOT", running inside the dashboard (AspiriFridays Producer Console)
- "Anything you see in the dashboard is CLI-able"
- Why it matters: CLI/TUI tools in your app run and get tested right next to everything else in Aspire.
- Source: 16:16 ET, transcript 20261110-161600, /shots/161630.jpg
-->

---
layout: "shot"
image: "/shots/161922.jpg"
time: "16:19"
---

# Aspire 17, next week: faster starts, easier upgrades

<!--
- Say: Aspire 17 ships next week. The AppHost becomes a plain .NET project, so upgrading is just a package bump.
- "We are shipping 17.0 next week" (the team is "already at 17.1" internally)
- A plain .NET project: AppHosts use Microsoft.NET.Sdk — upgrade is "a package bump, not an SDK pin"
- Projects by path: no project references, so the dashboard starts "without waiting on the MSBuild graph"
- Your NuGet setup as is: inherited feeds, consistent restore; attach to running apps: debug a running service in VS Code from the Aspire view
- Demo (16:20): `aspire update` offers to update all package versions and the NuGet config, running the CLI for each package; "the update was successful"
- Why the AppHost SDK goes away: "we no longer need to use this very .NET specific mechanism to deliver things that we need behind the scenes, namely the dashboard and DCP" (the CLI bundles them now)
- Migration demo (16:22): add the Aspire.Hosting.AppHost package plus a .NET hosting package; `AddProject<Projects.X>` is now flagged "obsolete, don't use this anymore" (the generated `Projects` types go away with projects-by-path). Check the Aspire 17 docs for the replacement API name.
- Why by path (16:24): Aspire can rebuild .NET projects when they change — and "a sneak peek, maybe hot reloading them" without a rebuild. "We already battle tested this with all the other languages ... Let's put .NET up to parity."
- Why it matters: fewer upgrade headaches and a faster F5 for Aspire apps.
- Source: 16:18–16:24 ET, transcripts 20261110-161802, 20261110-162000, 20261110-162202, 20261110-162401, /shots/161922.jpg
-->

---
layout: "shot"
image: "/shots/162753.jpg"
time: "16:27"
---

# Aspire 17: a redesigned dashboard

<!--
- Say: Aspire 17 also brings a redesigned dashboard — same features, new layout, plus tags and pinning.
- "All the dashboard functionality that you are obviously used to and you love is obviously still here"
- New: "tags and pinning and all types of wonderful stuff that wasn't there before"; banner on stream: "Welcome to the new Aspire dashboard!"
- Upgrading: "there's a skill too" — an update / breaking-changes skill that pulls in others, "including the very specific project resource V2 skill"
- 16:28: the overview now shows console logs inline ("my console logs are directly in the overview") and resource relationships
- By-path helps at scale: "I think I've seen 47 .NET projects orchestrated by Aspire"
- Links: aspire.dev; Discord at aka.ms/aspire-discord ("the best Discord on planet Earth. Sorry, MAUI")
- Skills Q&A (16:30): in 17, Aspire skills ship as a plugin that updates "out of band of our releases" — "you don't have to drop the skill files in your repo and check them in. You just need a reference to the plugin."
- Why it matters: let an agent do the Aspire 17 migration with the provided skills.
- Source: 16:26–16:28 ET, transcript 20261110-162603, /shots/162753.jpg
-->

---
layout: "session"
num: 11
time: "4:30 PM"
speakers: "Barry Dorrans"
---

# 2 Secure 2 Curmudgeonly

<!--
[Session 11] .NET security.
-->

---
layout: "statement"
---

.NET security reports: 84 → 2,622 in one year.

<!--
- Say: Last year .NET had 84 security reports. This year, 2,622. Real vulnerabilities went from 12 to 97.
- MSRC cases (a researcher fills in the form on the MSRC site): 2025: 84 → 2026: 2,622. CVEs: 12 → 97 (stream slide /shots/163340.jpg)
- Barry Dorrans: "this year we had lots more gray hair"
- CVSS caution: scores are based "on the worst possible scenario, which might not be the most likely scenario" — a 9.9 doesn't automatically mean "run out and fix that right now" for your app
- Why the jump (16:34): "AI is getting better at finding things, and researchers getting better at driving their AI ... So not an increase in bugs." Often in code "unloved and untouched for 15 to 20 years." "It's not that LLMs are bad at writing code."
- Bounties paid: 2025 $635,500 → 2026 $1,012,500 ("This year we broke a million"). Not every valid report gets a CVE; CVEs are issued for medium CVSS and above; Microsoft also runs "our own LLMs running over everything" (/shots/163503.jpg)
- Why it matters: expect more .NET security patches; read the advisory, not just the score.
- Source: 16:32–16:35 ET, transcripts 20261110-163200, 20261110-163403, /shots/163340.jpg
-->

---
layout: "statement"
---

AI isn't writing more bugs. It's finding the old ones.

<!--
- Say: The jump in reports isn't new bugs. AI-assisted researchers are finding bugs in code that's 15 to 20 years old.
- Barry Dorrans (16:34): "not an increase in bugs. This is just an increase in bugs that people have discovered and pointed out to us. It could be in code that's 20 years old."
- "It's not that LLMs are bad at writing code" — often it's stuff "unloved and untouched for 15 to 20 years"
- Bounties broke $1M this year ($1,012,500 vs $635,500), and Microsoft runs "our own LLMs running over everything"
- Why it matters: old code is getting a fresh security look; expect more patches and keep up with them.
- Source: 16:34–16:35 ET, transcript 20261110-163403, /shots/163503.jpg
-->

---
layout: "shot"
image: "/shots/163615.jpg"
time: "16:36"
---

# 97 CVEs: denial of service leads

<!--
- Say: Of this year's 97 .NET CVEs, denial of service was the biggest group — mostly loops and unbounded allocation.
- By type (chart): Denial of Service 31, Elevation of Privilege 23, Remote Code Execution 19, Information Disclosure 9, Security Feature Bypass 7, Spoofing 4, Tampering 4
- DoS: "an awful lot of them in weird loopings or allocating too much and not limiting stuff"
- Severity: "four criticals this year, most of them were high"
- "The fix author may not have written the vulnerable code in the first place ... don't blame fix authors for writing vulnerabilities"
- Out-of-band example (16:38): a Brotli bug from Google (copy embedded in .NET). In NPM it was remote code execution — NPM enables Brotli by default. In .NET "you would have got a denial of service", and HttpClient needed an opt-in to response decompression. It's still labeled RCE because Google classified it that way: "In theory, it can always go to remote code execution."
- Dependencies (16:40): "you need to keep an eye on your dependencies." Dependabot and other scanners "all depend on the vulnerability being described" properly, so "every now and again you should probably manually sweep all your dependencies and take a look at some of the descriptions"
- MSQuic RCE: scored 9.8, "very high", but "not so much for .NET": Windows embeds its own copy in the kernel; .NET embeds a separate copy "only for .NET uses". Same bug, different real risk.
- Why it matters: set limits on loops, input sizes and allocations in your own code — that's where most issues were.
- Source: 16:36–16:41 ET, transcripts 20261110-163600, 20261110-163803, 20261110-164004, /shots/163615.jpg
-->

---
layout: "statement"
---

Add a guard? Apply it everywhere. Parse once. Check your complexity.

<!--
- Say: Two real .NET CVEs from this year, two lessons you can use in your own code.
- CVE-2026-32203 (System.Security.Cryptography.Xml DoS): EncryptedXml.DecryptEncryptedKey() recursed on inner keys through a path that didn't increment or check the existing depth counter → unbounded recursion → StackOverflowException kills the process. Takeaway on stream: "When you add a guard make sure it applies everywhere."
- XML in general: "Encrypted XML in particular has proved great for" unbounded recursions and stack overflows
- CVE-2026-84008 (System.Security.Cryptography.Pkcs DoS): SignedCms rebuilt and reparsed every embedded certificate once per signer, "no trust required". "A 117kb message caused 160,000 certificate constructions. Fix was to parse a certificate once. Check your algorithm complexity." ("Billion laughs attacks are everywhere.")
- CVE-2026-57108 (.NET Runtime DoS, "only on Linux", 16:46): a self-issued cert with a 21-byte SAN payload; cert.GetNameInfo() goes to the OpenSSL layer and crashes the worker "before the certificate chain trust is ever evaluated" — repeatable for a persistent DoS. Takeaways: "DoS is not just resource consumption"; "You cannot know if unmanaged APIs validate their inputs. Assume not and validate before passing." (/shots/164646.jpg)
- RCEs this year (16:48) cluster in the desktop runtime (WPF/XPS), MSDIA (the debugging component that enriches exceptions), and the .NET SDK itself ("not remotely though")
- CVE-2026-50646 (System.Windows.Controls RCE): nested Frames from XPS lost the IsUnsafe marking → attacker XAML → ObjectDataProvider → Process.Start("calc.exe"). "XPS is like PDF. You can embed code and scripts in it ... It's quite undocumented." Barry: "my advice here would be stop using XPS for anything if you are using it." Stream takeaway: "Document your formats and fuzz them with purpose, not random data." (/shots/164829.jpg)
- Why it matters: most of this year's CVEs were DoS — guards that miss one code path and quadratic work on untrusted input are the pattern.
- Source: 16:42–16:49 ET, transcripts 20261110-164202, 20261110-164404, 20261110-164601, 20261110-164804, /shots/164332.jpg, /shots/164514.jpg
-->

---
layout: "shot"
image: "/shots/165146.jpg"
time: "16:51"
---

# An all-zero MAC that validated: ASP.NET Data Protection

<!--
- Say: In April there was an out-of-band patch for ASP.NET Data Protection. A payload with an all-zero MAC would validate.
- CVE-2026-40372 (Security Bypass, ASP.NET Core Identity), OOB patch April 2026
- Why: ComputeHash() allocates and returns a new byte[]; it doesn't write into an existing span. The correctHash span stayed all zeros from the stackalloc, so an all-zero MAC passed the check
- Stream takeaway: "Spans are sometimes hard to use correctly."
- Also (16:50): some SDK workloads didn't use NuGet package source mapping, so an attacker could plant files on your machine; and a fix strips headers on HTTP↔HTTPS redirects (the notes agent says Proxy-Authorization was leaking — not confirmed word-for-word in transcript)
- Why it matters: if you use ASP.NET Data Protection, make sure that April patch is in; and when you use Span APIs, check which overload actually writes into your buffer.
- Source: 16:50–16:52 ET, transcript 20261110-165001, /shots/165146.jpg
-->

---
layout: "statement"
---

"Forgiving in your input" is a giant pit of security failure.

<!--
- Say: The old rule "be strict in what you send, forgiving in what you accept" — Barry Dorrans called it "a giant pit of security failure."
- CVE-2026-70188 (Security Bypass, HPACK poisoning): Kestrel HTTP/2 request trailers and dynamic HPACK values could accept newline characters instead of rejecting malformed input → one request treated as two → auth bypass (/shots/165258.jpg)
- Stream takeaways: "Canonicalisation is hard." "You don't have to support every part of an RFC."
- Barry (16:52): "In certain cases, following the RFC just makes you vulnerable ... make choices about what parts of the RFC you want to implement."
- Why it matters: reject malformed input instead of trying to make sense of it — especially in parsers and protocol code.
- Source: 16:52–16:53 ET, transcript 20261110-165203, /shots/165258.jpg
-->

---
layout: "shot"
image: "/shots/165507.jpg"
time: "16:55"
---

# Aspire's first CVEs shipped this morning — patch it

<!--
- Say: If you use Aspire, update today. Its first four CVEs were patched this morning.
- "Those vulnerabilities were this morning." Barry: "they're not .NET ... but their security is still mine"
- CVE-2026-120006: RCE from a cookie replay bypassing authentication
- CVE-2026-120778: RCE from file planting a Directory.Build.rsp
- CVE-2026-120792: info disclosure via a symlink race in /tmp on Linux
- CVE-2026-118740: dashboard security bypass exposed the browser token and allows telemetry delete
- Stream slide: "The Aspire dev manager told me two months [ago] how pleased they were that aspire had no CVEs …" (the notes agent said "two days"; the slide says two months)
- Also (16:54): "faking Windows authentication on Linux" (Kerberos + LDAP lookups) — "Windows authentication really is for Windows hosts ... if you are using this right now please move to OAuth"
- Microsoft is "thinking about providing more details" in CVEs, not just a commit link: "the code is out there so LLMs can reverse it anyway"
- Why it matters: Aspire's dashboard and AppHost run on dev machines — patch them like anything else.
- Source: 16:54–16:56 ET, transcript 20261110-165402, /shots/165507.jpg
-->

---
layout: "shot"
image: "/shots/165610.jpg"
time: "16:56"
---

# Found a .NET vulnerability? Report it to MSRC, and get paid

<!--
- Say: Barry's ask: report security bugs to MSRC, not as GitHub issues — and there's a bounty.
- Report: msrc.microsoft.com/report/vulnerability ("not in GitHub issues")
- "If you're using AI, please check your results."
- Grounding docs for your AI agents: aka.ms/dotnet/securityfoundations
- Bounty: aka.ms/dotnet/bounty ("I may have to write you a cheque")
- Q&A, on whether AI will make code safer: "I am not a hopeful person by nature. That is why I am in this job." (Barry Dorrans)
- Why it matters: point your agents at the security grounding docs when they write .NET code.
- Source: 16:56–16:58 ET, transcript 20261110-165600, /shots/165610.jpg
-->

---
layout: "session"
num: 12
time: "5:00 PM"
speakers: "Wendy Breiding"
---

# Beyond Autocomplete: Getting the Most from GitHub Copilot for .NET

<!--
[Session 12] Agenda time 5:00 PM ET; started ~5:01.
- Keynote already covered Wendy's Copilot app demo (RSVP race fix) and dotnet/skills evals; add only new details here.
- Demo app (17:02): WinForms front end + ASP.NET Core API + Postgres, for purchase orders. Bug: "15 copies of the same purchase order in our database"
- One bug, three tools: fix UI error handling in Visual Studio → API resilience in VS Code (so it "only submits one version of the purchase order") → a report of the duplicates in the Copilot app
-->

---
layout: "shot"
image: "/shots/170443.jpg"
time: "17:04"
---

# Visual Studio picks the right .NET skills for your solution

<!--
- Say: Visual Studio now detects what your solution uses and turns on matching built-in .NET skills for Copilot.
- "It's going to detect what I [use] ... So it is automatically provided this WinForms expert skill as well as the .NET Web API skill, since my solution has both a WinForms front end and an API back end."
- With the Auto model, Copilot "picked up that WinForms expert skill, identifying that this is a front-end change"
- AI Customization → Skills shows them as Built-in (winforms-expert, dotnet-webapi, writing-mstest-tests, test-smell-detection, ...)
- Same curated skills for other agents: github.com/dotnet/skills (see the keynote eval slide)
- Result (17:08): the WinForms UI now retries "a few times, but at the end it says it failed, but you might want to confirm that it didn't actually save"; the app runs under Aspire
- VS Code too: "there were some specific skills that we shipped in box for you. We also do the same thing with C# Dev Kit."
- VS Code (17:10): "Copilot Fusion ... looks at the complexity of the task that you've given it" and picks the model — here "GPT 6.1 Sol". The agent first read the .NET Web API skill, then the "handoff doc that the last agent made for it to understand what it did" — the Visual Studio agent left notes for the next agent
- Result (17:16): after `aspire run` and one submit — "And woohoo! Only one." The duplicate purchase order bug is fixed across the WinForms UI and the API. Next: the "generate duplicate reports" button, which currently makes a text file
- dotnet plugin (17:22): configures agents to use LSP as a tool, backed by Roslyn in the new daemon mode (shared across agents). "About a 50% reduction in memory usage when you're using it in that multi-agent scenario ... when I normally have three or four agents going at one time, my system can handle it now."
- Q&A (17:28): Roslyn daemon mode "It's not a skill, it's a configuration" in the plugin; Claude Code uses a different LSP configuration than Copilot. Copilot Fusion can hand small steps (e.g. "validate this") "to one of the smaller, cheaper models" to save money
- Why it matters: you get .NET-specific guidance without writing your own instructions.
- Source: 17:04–17:11 ET, transcripts 20261110-170403, 20261110-170804, 20261110-171001, /shots/170443.jpg
-->

---
layout: "statement"
---

AI coding benchmarks had "not a lick of .NET code." So .NET built one: 170+ C# scenarios.

<!--
- Say: The public AI coding benchmarks don't test C#, so the .NET team built its own, and other Microsoft teams now use it.
- Wendy Breiding (17:12): "you see SWE bench and deep SWE and all of these different benchmarks ... there's not a lick of .NET code"
- "We've compiled a benchmark of 170 some scenarios that we run on a regular basis," based on the scenarios customers send
- "The Visual Studio team, the VS Code team, and the Copilot SDK team are all also utilizing this benchmark to ... catch any regressions"
- Caught before release: a code-search speedup that "really increased token usage by way too much"
- Reports showed "refactoring scenarios were struggling, especially with really large code bases" → that "led to the creation of the C# refactoring skill"
- How it runs (Q&A, 17:26): checks are partly "deterministic like tests", partly "LLM as a judge"; run "on a nightly basis", rotating through "our top five models that users are using"; a report "at the end of the week". On auto model choice: "models are changing so fast"
- Why it matters: Copilot's C# quality is now measured on C# scenarios, and regressions get caught before release.
- Source: 17:12–17:16 ET, transcripts 20261110-171204, 20261110-171401
-->

---
layout: "statement"
---

NuGet packages can now ship agent skills. `dotnet restore` delivers them.

<!--
- Say: Package authors can now put skills for AI agents inside their NuGet package; you get them on restore.
- Wendy (17:18): "This is new very recently that allows for package maintainers to put their expertise right in the package ... ship that all as part of the package so that the user gets that package, does a .NET restore, those skills" are there
- Demo: the Markout NuGet package ships markout, markout-build and shapes skills
- Four ways to get .NET skills so far: built into Visual Studio, shipped with C# Dev Kit, the plugin method, and now inside NuGet packages
- Read more (17:20): Rich Lander's blog post "Delivering Skills in NuGet packages" ("came out last week"), devblogs.microsoft.com/dotnet/delivering-skills-in-nuget-packages/. The `dotnet-package-skills` command copies a package's skills "in the appropriate folder so that the agents can recognize that they're there" (the blog example copies to .agents/skills)
- Demo continues in the GitHub Copilot app to turn the duplicate report into JSON (/shots/171930.jpg)
- Why it matters: if you maintain a library, you can teach agents how to use it correctly.
- Source: 17:18–17:20 ET, transcript 20261110-171800
-->

---
layout: "statement"
---

One .NET bug, four Copilot products, end to end.

<!--
- Say: Wendy fixed one real bug across Visual Studio, VS Code, the Copilot app, and the Copilot CLI — each agent picked up where the last one stopped.
- Visual Studio: WinForms UI error handling (winforms-expert skill, Auto model)
- VS Code: API resilience (dotnet-webapi skill, read the VS agent's handoff doc) → "Woohoo! Only one."
- Copilot app: duplicate report changed to JSON (Markout skills from a NuGet package)
- Copilot CLI (17:24): cleanup of the duplicates; "This one was medium complexity, so it's picked GPT-6 Luna." On-screen prompt: run the cleanup in preview first, then "execute against the disposable database only ... Do not commit or run cleanup against production." (/shots/172534.jpg)
- "We were able to go from end to end through four different Copilot products"
- Why it matters: use the tool that fits each part of the job; skills and handoff docs keep the context between them.
- Source: 17:02–17:26 ET, transcripts 20261110-170200 … 20261110-172404
-->

---
layout: "session"
num: 13
time: "5:30 PM"
speakers: "Tanner Gooding"
---

# .NET 11 Numerics

<!--
[Session 13]
-->

---
layout: "shot"
image: "/shots/173229.jpg"
time: "17:32"
---

# New in .NET 11: `Decimal32`, `Decimal64`, `Decimal128`

<!--
- Say: .NET 11 adds IEEE 754 decimal floating-point types in three sizes.
- Decimal32 / Decimal64 / Decimal128: 7 / 16 / 34 significant decimal digits; 32 / 64 / 128 bits
- "IEEE 754 semantics. Generic math. Your choice of representation." (stream slide)
- vs System.Decimal: both base 10, but decimal "is primarily oriented around currency"; "the IEEE decimal types ... are designed for scientific computing"
- Why it matters: base-10 floating point with standard IEEE behavior, usable in generic math code.
- Source: 17:32 ET, transcript 20261110-173204, /shots/173229.jpg
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
