---
theme: default
title: .NET Conf 2026 Recap - Desktop and mobile
info: |
  ## .NET Conf 2026 Recap - Desktop and mobile
  Kevin Griffin - Microsoft MVP
  .NET MAUI, WinForms, WinUI, CsWinRT, Reactor: highlights from Day 1 (2026-11-10) and Day 2 (2026-11-11), captured live.
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

- Desktop and mobile
- Kevin Griffin
- Microsoft MVP

<!--
- [title]
- Say: This is a .NET Conf 2026 recap on one topic: .NET MAUI, WinForms, WinUI, CsWinRT, Reactor. It pulls the highlights from Day 1 (2026-11-10) and Day 2 (2026-11-11), captured live from the stream.
- Sessions in this deck:
  - 01 From the keynote: Mobile (Day 1, 11:00 AM)
  - 02 Why WinForms must not change — yet reinvented itself with .NET 11 (Day 1, 1:30 PM)
  - 03 What's New in .NET MAUI in .NET 11 (Day 1, 2:30 PM)
  - 04 Bringing `dotnet run`, `test`, and `watch` to .NET MAUI (Day 1, 7:30 PM)
  - 05 Building great Windows apps with WinUI and agents (Day 2, 2:31 PM)
  - 06 CsWinRT 3.0: Modernizing the Windows Projections for .NET (Day 2, 3:31 PM)
  - 07 Beyond Code Generation: Give AI Eyes and Hands for .NET MAUI (Day 2, 4:30 PM)
  - 08 No XAML Required: Native Windows Apps in Pure C# (Day 2, 5:01 PM)
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

# From the keynote: Mobile

<!--
- [Session 01 · part of the Day 1 keynote] 11:00 AM ET, 2026-11-10.
- Say: The Day 1 keynote was a one-hour tour of .NET 11. These slides are the keynote parts about .NET MAUI, WinForms, WinUI, CsWinRT, Reactor.
- Next slides: MAUI team PR volume, MAUI 11, paper cuts fixed, the .NET Conf app.
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
time: "Day 1 · 11:31"
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
time: "Day 1 · 11:32"
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
time: "Day 1 · 11:34"
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
layout: "session"
num: 2
time: "Day 1 · 1:30 PM"
speakers: "Klaus Löffelmann"
---

# Why WinForms must not change — yet reinvented itself with .NET 11

<!--
[Session 02 · Day 1]
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
time: "Day 1 · 13:37"
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
time: "Day 1 · 13:39"
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
time: "Day 1 · 13:44"
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
num: 3
time: "Day 1 · 2:30 PM"
speakers: "Gerald Versluis"
---

# What's New in .NET MAUI in .NET 11

<!--
[Session 03 · Day 1]
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
time: "Day 1 · 14:41"
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
time: "Day 1 · 14:53"
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
time: "Day 1 · 14:54"
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
time: "Day 1 · 14:57"
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
num: 4
time: "Day 1 · 7:30 PM"
speakers: "Jonathan Peppers"
---

# Bringing `dotnet run`, `test`, and `watch` to .NET MAUI

<!--
[Session 04 · Day 1] Last session of Day 1.
- Session 7 (MAUI) already mentioned this: `dotnet run`, `test`, `watch` work for MAUI with an interactive platform prompt; add only new details here.
- Why (19:30): "MAUI released in, like, May 2022, and the CLI wasn't really a focus back then" — you "would hit F5 in an IDE like Visual Studio". Now VS Code ("a small editor that is on top of terminal commands") and "AI agents writing code for us ... need to make sure their code works in some way"
-->

---
layout: "shot"
image: "/shots/193514.jpg"
time: "Day 1 · 19:35"
---

# `dotnet run` for MAUI: pick a framework, then a device

<!--
- Say: In .NET 11, `dotnet run` on a MAUI app asks you which framework and which device — or you pass them on the command line for scripts and agents.
- New "selecting" phase in .NET 11's run pipeline: "You might need to pick a target framework. You might need to pick a device. Then, of course, it builds, deploys, gets the run arguments." The iOS and Android workloads plug into it
- Interactive: "an interactive prompt using a library called Spectre Console", choose with the up and down arrows
- Scripts (stream slide): `-f net11.0-android` · `--list-devices` · `--device <id>` — "Interactive: choose. Non-interactive: supply enough information."
- Live demo (19:48–19:50): `dotnet run` shows the framework picker (you can type "Windows" to filter), then the device. Jonathan: "I actually have four Android devices connected for my AI agents to use."
- On a Pixel 10 (19:50): "this is what Android Logcat output looks like. So you get your console write line messages right here in the terminal. And so I can Ctrl+C and the app stops." `dotnet watch` then launched the same way; a C# hot reload edit misbehaved ("I have nightly builds from before today"), so he showed a XAML change instead
- Result (19:52): XAML change went through — "hello .NET Conf" on the phone — and the C# change "worked that time" on a retry
- `dotnet watch` (19:38) "sits on top of .NET Run" to make "an interactive hot reload session". Editor doesn't matter — "It could be Notepad." A file watcher sees the change; "dotnet watch is a server and your app is the client"; it compiles and "send[s] the diff over to your app, which will reload the change"
- Why it matters: agents and scripts can build, deploy and run a MAUI app on a chosen device without an IDE.
- Source: 19:34–19:40 ET, transcripts 20261110-193404, 20261110-193803, /shots/193514.jpg
-->

---
layout: "shot"
image: "/shots/194348.jpg"
time: "Day 1 · 19:43"
---

# `dotnet test` on a device reuses the run pipeline

<!--
- Say: `dotnet test` for MAUI reuses everything `dotnet run` does — select, build, deploy, launch — then runs the tests on the device and collects the results.
- Pipeline (stream slide): Select → Build → Deploy → Run test application → Collect results, on Microsoft.Testing.Platform (MTP). "The test project must run tests on the device."
- "The main difference is at the end, you want some kind of test results to happen." (19:43)
- How watch talks to the app (19:42): over WebSockets — a project capability named "Hot Reload WebSockets"; on Android it uses ADB (Android Debug Bridge) to reach the device
- New templates (19:46): `dotnet new androidtest -n MyAndroidTests`, `dotnet new iostest -n MyiOSTests` ("We actually have tvOS and Mac Catalyst test" too). Each makes an executable test app using the platform's startup model (Android instrumentation → MTP; iOS UIKit scene lifecycle → MTP)
- Coming from dotnet/maui-labs (experimental/prerelease): `dotnet new mauitest -n MyApp.Tests` (/shots/194729.jpg)
- Test frameworks (19:52): the template "configures MTP for you and sets up an instrumentation class ... we've configured MSTest. You could switch that to NUnit or whatever test framework you would like." (The notes agent also listed xUnit and TUnit — not named on stream in what I checked.)
- Demo on the Pixel 10: `dotnet test` ran; "Nothing actually appears on the screen because this is an instrumentation project that doesn't have an app icon"
- Why it matters: device tests become a plain CLI command that CI and agents can run.
- Source: 19:42–19:54 ET, transcripts 20261110-194203, 20261110-194604, 20261110-195204, /shots/194348.jpg, /shots/194729.jpg
-->

---
layout: "statement"
---

"If your agent can run tests on Android, imagine the bugs that it can fix."

<!--
- Say: The point of run, watch and test for MAUI: mobile gets the same CLI as everything else, so agents can drive it.
- Jonathan Peppers (19:54), after the device demo ("three tests passed"): "really our focus here is to get parity for mobile ... And AI agents can call these commands"
- The three commands: `dotnet run` (pick framework + device, logs in the terminal), `dotnet watch` (hot reload to the device), `dotnet test` (on-device tests via MTP)
- Why it matters: mobile no longer needs an IDE in the loop — humans, CI and agents use the same commands.
- Source: 19:54–19:56 ET, transcript 20261110-195404
-->

---
layout: "session"
num: 5
time: "Day 2 · 2:31 PM"
speakers: "Niels Laute, Morten Nielsen"
---

# Building great Windows apps with WinUI and agents

<!--
- [Session 05 · Day 2] Niels Laute and Morten Nielsen. Started about 2:31 PM ET.
- Source: 14:30-14:31 ET, transcript 20261111-143000; dotnetconf.net/agenda (2:30 PM ET).
-->

---
layout: "shot"
image: "/shots/day2/143502-crop.jpg"
time: "Day 2 · 14:35"
---

# WinUI: open source on GitHub, new Chart, TableView and Ink controls

<!--
- Say: WinUI now works in the open on GitHub, adds charting, a table view and ink, and ships monthly as part of the Windows App SDK.
- On screen, "What's new in WinUI": Open source ("GitHub is now the source of truth"); New controls (Chart, TableView, Ink); Performance ("Faster and more responsive"); Fundamentals (new windowing APIs, GameInput support, ThemeResources in code, and an item cut off as "aml compiler", likely the XAML compiler); Developer experience (dotnet new templates, WinApp CLI, Windows agent skills).
- Niels (14:34): "GitHub is now our source of truth and we're working in the open ... We're not quite ready yet to accept community pull requests, but that is something we're looking at". New controls: "different charting controls, a new table view control, and pen and ink support."
- Context: WinUI ships in the Windows App SDK, so "we can ship both stable and experimental releases on a monthly basis." Microsoft uses it in Paint, Notepad, Photos, Widgets, the new Windows Search and the new Run dialog.
- Image: a crop of the stream slide (the raw frame's camera inset shows a wall note, so it is cropped out).
- Why it matters: a native Windows UI stack that you can follow on GitHub, with the controls people asked for.
- Source: 14:32-14:35 ET, transcripts 20261111-143202 and 20261111-143402; slide crop from shot 20261111/143502.
-->

---
layout: "shot"
image: "/shots/day2/143928-crop.jpg"
time: "Day 2 · 14:39"
---

# WinUI for agents: WinApp CLI gives hands, the WinUI plugin gives knowledge

<!--
- Say: WinUI wants agents to build Windows apps well. The WinApp CLI lets an agent create, run, inspect and package an app; the WinUI Copilot plugin gives it a WinUI agent and skills grounded in the docs. Three installs.
- On screen, "Installing the required tools":
  - `dotnet new install Microsoft.WindowsAppSDK.WinUI.CSharp.Templates`
  - `winget install Microsoft.winappcli`
  - `copilot plugin install winui@awesome-copilot`
- Niels (14:36): the WinApp CLI (introduced "a few months ago") lets you "create and build and run and debug" apps from the command line, also for other frameworks such as Electron. A new WinApp VS Code extension (on the Marketplace) runs and debugs WinUI apps in VS Code: "This was not possible before". Visual Studio: improved project templates shipped "about an hour ago"; a new XAML previewer is an experiment.
- Agents (14:38): the CLI "gives agents the hands they need to interact with Windows apps"; "with Windows Sandbox support, you can even do this in the background. So your app and agent run in their own container." The WinUI plugin gives "a dedicated WinUI agent and a collection of skills ... grounded in the right documentation".
- Image: the stream slide, cropped to remove the speaker camera frames (a wall note was visible behind one speaker).
- Why it matters: an agent can build, run and check a Windows desktop app from the command line, with WinUI-specific guidance.
- Source: 14:36-14:39 ET, transcripts 20261111-143603 and 20261111-143803; crop of shot 20261111/143928.
-->

---
layout: "shot"
image: "/shots/day2/144748.jpg"
time: "Day 2 · 14:47"
---

# Leave a comment on your running app. Copilot reads it, builds it, checks its own UI.

<!--
- Say: Live demo: Morten left a comment on the running WinUI app's UI. Copilot CLI read it, changed the heading, built a GitHub issues page, launched the app, and inspected the UI to check its own work.
- How it works (14:42): `winapp run` launches the app with "dev tools on". From the in-app dev tools you can switch to dark mode, inspect elements and "tweak with them", and "actually add comments to my UI". The comments are stored in the app project "as a little JSON file ... persisted until they're like resolved".
- Prompt (14:44): find the comment, add an issues page with "the last seven days of closed issues on GitHub", then launch the app.
- On screen: Copilot: "Your comment asks for the Home heading to read 'Welcome to .NET Conf!' ... add an Issues page that filters by closure date, excludes pull requests, and handles pagination." The app shows "Recently closed issues / Microsoft/microsoft-ui-xaml - Past 7 days / 25 issues closed in the past 7 days". The CLI runs `winapp ui ...` commands; model GPT-6.1 Sol.
- Self-check (14:46): "it's actually using the inspects now, so it can actually inspect these and say, oh, I didn't find this, and I don't see the navigation, so that didn't work. So it's actually able to check itself".
- Skills: the WinUI skill "pulls in our documentation, but also things like the WinUI gallery", so the agent grounds controls in sample code. You can also run the app in Windows Sandbox and keep working.
- Live demo, not a recording: it was slow and had a few failed edits on screen before it worked.
- Why it matters: UI feedback goes straight from the app to the agent, and the agent checks the result itself.
- Source: 14:42-14:48 ET, transcripts 20261111-144200, 20261111-144403, 20261111-144603; shot 20261111/144748.
-->

---
layout: "shot"
image: "/shots/day2/145135.jpg"
time: "Day 2 · 14:51"
---

# `winapp perf`: the agent profiled startup and found the UI-thread waste

<!--
- Say: The WinApp CLI just added performance recordings. Morten told the agent "it takes a long time to display things". It ran `winapp perf`, and found that most of a slow startup frame was his own load/save code, not rendering.
- Morten (14:50): "one of the things we just added to the WinApp CLI is the ability to do performance recordings and also query those performance recordings. And then if you give that to the agent, it becomes quite powerful". The app took "about two seconds" to start.
- On screen: "The main delay is cached-data processing on the UI thread, including a redundant reload, not XAML rendering. `winapp perf` recorded a 1.53-second startup frame; layout/rendering accounted for only ~0.34 seconds." Timings: load cached account then save it 816 ms; fetch GitHub user 335 ms; reload and save the same account again 772 ms; initial refresh 1.80 s; AI availability check 158 ms. Cause: "SQLite's async calls execute synchronously, keeping this work on the UI thread." Fix: avoid saving unchanged data, move cache processing off the UI thread.
- The agent noted: "Timings are approximate because debugger attachment adds overhead". Morten had run this before the session ("I kind of pre-did this already").
- Follow-up: the recording stays on the machine, so you can ask more questions, e.g. the most expensive UI elements, with a WinUI performance-analysis skill.
- The app itself (14:48): Morten's GitHub issues app uses "the Windows AI APIs that ship within the Windows App SDK" to summarize the latest unread comments locally, "running on your NPU ... on your Copilot+ PC". It also uses "the new table view that's currently experimental".
- Why it matters: profiling a desktop app becomes a chat question, with evidence the agent can show.
- Source: 14:48-14:52 ET, transcripts 20261111-144804 and 20261111-145000; shot 20261111/145135.
-->

---
layout: "statement"
---

WinUI: monthly releases in the open, modern .NET workflow, ready for agents.

<!--
- Say: Niels's three takeaways: WinUI ships every month on GitHub, it now works like modern .NET (dotnet new, dotnet run, any editor), and it is ready for agents. Get started: aka.ms/winui.
- Niels (14:54): "we're investing in WinUI and we're shipping new releases every month. And we're doing that open on GitHub." The WinUI Gallery in the Microsoft Store now ships with the latest experimental SDK, to try new controls. "building WinUI apps now feels much more like modern .NET development ... .NET new or .NET run ... the CLI ... VS Code, or Visual Studio." "WinUI is ready for agents": WinApp CLI = tools, WinUI plugin = knowledge.
- On the closing slide: "A new Experimental + Stable release [each month], built in the open on GitHub"; "Get started: aka.ms/winui" (slide not in deck: a presenter menu and a camera frame cover it).
- New VS templates (14:52): a unit test app on the new MTP (Microsoft.Testing.Platform) "which allows you to run your tests with AOT, and you can do async UI tests"; a packaged/unpackaged choice in the templates, which the community asked for. The new XAML previewer (resize, dark mode) is experimental; they want feedback.
- Next Windows session today: CsWinRT 3.0 (3:30 PM ET).
- Source: 14:52-14:55 ET, transcripts 20261111-145203 and 20261111-145403; closing slide shot 20261111/145533.
-->

---
layout: "session"
num: 6
time: "Day 2 · 3:31 PM"
speakers: "Manodasan Wignarajah, Sergio Pedri"
---

# CsWinRT 3.0: Modernizing the Windows Projections for .NET

<!--
- [Session 06 · Day 2] Manodasan Wignarajah and Sergio Pedri. Started about 3:31 PM ET.
- STATUS: CsWinRT 3.0 is in PREVIEW. Sergio (15:53): "all of these is currently in preview". The NuGet and Windows SDK packages came out this week as previews; the WinUI / Windows App SDK multi-target package is "an internal package at the moment, but we're hoping to get this out very soon."
- Source: dotnetconf.net/agenda (3:30 PM ET); stream agent session marker.
-->

---
layout: "shot"
image: "/shots/day2/153441.jpg"
time: "Day 2 · 15:34"
---

# CsWinRT 3.0: Microsoft Store app 16.6% smaller, generator 12.8x faster

<!--
- Say: Just moving the Microsoft Store client from CsWinRT 2 to CsWinRT 3 cut its Native AOT binary by about 22 MB (16.6%). The interop generator is 12.8x faster on a clean build and no longer runs in the IDE loop.
- On screen, "Smaller AOT apps": Microsoft Store 129.34 MB → 107.86 MB (−16.61%); Contoso Camera 5.61 MB → 5.08 MB (−9.45%).
- Sergio (Store client team, 15:34): the Store numbers are "on .NET 10 and Native AOT" both before and after; "This is just from updating from CSP2 to CSP3 [CsWinRT 2 to 3]". "this, again, is a production ready thing. And we're actually rolling it out to Windows Insiders experimental users right now." Note: that is the Store app's own build; the public CsWinRT 3.0 packages are still preview (15:53). The size win "scales with" app complexity.
- Next slide, "Faster IntelliSense builds / Microsoft Store: CsWinRT 3.0 generator vs 2.x": clean build (generator only) 115 s → 9 s, 12.8x; incremental build (generator only) 24 s → 4 s, 6x.
- Why it's faster: CsWinRT 2 used source generators that analyze all your code for marshalling stubs, "very, very expensive". CsWinRT 3 "completely removed all of these generators" and moved to "a single native AOT compiled interop generator, which runs just when you actually are ready to deploy your app ... this is not part of the IDE loop."
- Why it matters: smaller Windows apps, and VS loads and builds big WinRT projects faster.
- Source: 15:33-15:36 ET, transcript 20261111-153401; shot 20261111/153441 (size slide); generator numbers from the next stream slide (stream agent crop 20261111-cswinrt3-numbers).
-->

---
layout: "shot"
image: "/shots/day2/154425.jpg"
time: "Day 2 · 15:44"
---

# CsWinRT 3.0: no more `partial`, attributes or casts just for AOT

<!--
- Say: With CsWinRT 2, AOT-safe WinRT code needed odd changes: make the class partial, add [DynamicWindowsRuntimeCast], add explicit casts on collection expressions. With CsWinRT 3, the first version you would naturally write just works. And apps no longer wait for every dependency to update CsWinRT.
- On screen, "Why 3.0? Pain point: AOT friction": `public partial class TaggedButton : Button` with `[DynamicWindowsRuntimeCast(typeof(FrameworkElement))]` on a method and `return (object[])[Tag, .. tags];`.
- Sergio (15:43): partial "because we need our generators to be able to inject marshaling code"; the attribute so "trimming doesn't remove types that we actually might be relying on"; the cast because a collection expression "might result in a compiler-generated type that we cannot see". "So the whole thing in general is just not really developer-friendly."
- CsWinRT 3: "no need to mark anything as partial, no need to add attributes anywhere, no need to add casts anywhere. The code is just working as is".
- Versioning pain fixed (15:42): before, packages built against an older CsWinRT kept old bugs, so "you would have to wait for all of your dependencies to actually go and update". Now "You can just reference the latest version of CsWinRT in your app, and then you get all the bug fixes and all the improvements".
- Root cause: CsWinRT started in .NET 5, before trimming and AOT support, so AOT was added later without breaking changes.
- Also new (15:50): arrays in WinRT APIs project as `ReadOnlySpan<T>` (pass arrays) and `Span<T>` (fill arrays). Still source compatible thanks to the C# 14 "first class span" feature (arrays and strings convert automatically), with fewer allocations.
- Why it matters: WinUI and Windows App SDK apps can go Native AOT with ordinary C#. CsWinRT 3.0 is preview today.
- Source: 15:42-15:45 ET, transcripts 20261111-154200 and 20261111-154400; shot 20261111/154425.
-->

---
layout: "shot"
image: "/shots/day2/154850.jpg"
time: "Day 2 · 15:48"
---

# Opt in to CsWinRT 3.0 (preview) with the TFM: `.0` = 2.x, `.1` = 3.0

<!--
- Say: CsWinRT 3.0 is in preview and is a breaking change, so you opt in. The last number of the Windows OS version in your target framework picks it: .0 keeps CsWinRT 2.x, .1 moves to 3.0. Libraries can multi-target and use #if CSWINRT3_0.
- Manu (15:47): "the last bit in the OS version, in the TFM, typically has always been zero. And that will continue to mean that you're using CsWinRT 2.x or earlier projection. But if you change that to .1, that will mean that you're moving to CsWinRT 3.0 projections." They worked with the .NET SDK and NuGet teams on this.
- Libraries: "you're able to multi-target" with 2.x projections in one folder and 3.0 projections in the .1 TFM folder, so consumers move "at their own pace". The define CSWINRT3_0 lets you branch code.
- On screen, "Multi-target with CSWINRT3_0": `#if CSWINRT3_0` → `System.EventHandler<Watcher, Info> h = OnAdded;` `#else` → `Windows.Foundation.TypedEventHandler<Watcher, Info> h = OnAdded;`. "TargetFramework picks CsWinRT 2.x (.0) or 3.0 (.1)".
- Example of an API change: TypedEventHandler becomes System.EventHandler in 3.0 projections.
- Full TFM, from the build output on the "Application build" slide (15:46): `net11.0-windows10.0.26100.1`.
- How 3.0 works (15:46, shot 20261111/154635): libraries ship "reference projections ... assemblies that are reference DLLs". When the app builds, CsWinRT gathers all WinMD files into one merged `WinRT.Projection.dll` (demo: 26 .winmd references) and scans modules to generate `WinRT.Interop.dll` (demo: 407 modules). So the app, not each library, decides the CsWinRT version.
- Why it matters: you control when you take the breaking change, and package authors can support both.
- Source: 15:46-15:49 ET, transcripts 20261111-154600 and 20261111-154800; shots 20261111/154635 and 154850.
-->

---
layout: "shot"
image: "/shots/day2/155722.jpg"
time: "Day 2 · 15:57"
---

# CsWinRT 3.0 preview: try it now with the `.1` TFM

<!--
- Say: CsWinRT 3.0 is in preview (3.0.0-preview.261104.1). If your app uses only the Windows SDK projections, you can try it today with the .1 TFM. Windows App SDK multi-target previews come next; stable after feedback.
- On screen, "What's next / From preview to stable": "Moving CsWinRT 3.0 from preview to stable"; "Try it out with the .1 TFM and provide feedback"; partner projections: "WinAppSDK will multi-target their projections for CsWinRT 2.x and 3.0". Links: github.com/microsoft/CsWinRT/releases/tag/3.0.0-preview.261104.1 and nuget.org/packages/Microsoft.Windows.CsWinRT/3.0.0-preview.261104.1.
- Manu (15:56): "If you don't now have any dependencies today and just using the Windows SDK projections itself, you can go try it out right now with the .1 TFM." Then try the Windows App SDK previews when they ship. "Based on the feedback that we get, we'll be looking at moving CsWinRT 3.0 from preview to stable."
- Migration (15:54): "In general, it's all like mechanical changes". The Store code base had "almost a thousand" [DynamicWindowsRuntimeCast] attributes, now not needed. Point, Rect and Size are now float, not double, to match the WinRT ABI ("more efficient", no implicit conversions).
- Q&A (15:59): WinRT components can be written in any language, including C# published as Native AOT. "In fact, that's also how we're now shipping several components within Windows. They're just implemented in C Sharp, shipped as native AOT, and then they're just exposed through WinRT." No component names were given.
- Demo (15:52): the Contoso Camera app moved to 3.0 by changing the TFM to .1 and updating the preview Windows SDK package.
- Source: 15:52-16:00 ET, transcripts 20261111-155201, 20261111-155401, 20261111-155602, 20261111-155802; shot 20261111/155722.
-->

---
layout: "session"
num: 7
time: "Day 2 · 4:30 PM"
speakers: "Gerald Versluis"
---

# Beyond Code Generation: Give AI Eyes and Hands for .NET MAUI

<!--
- [Session 07 · Day 2] Gerald Versluis. Started about 4:30 PM ET.
- Warm-up from the host just before (16:28): he built MAUI apps "using agentic tools for Maui development" after a fitness app raised its price. A bike app "using the native maps, it's using Bluetooth, it's integrating in with my stationary bike", with a "Mario Kart mode" and a zombie-chase mode; and a breathing/mindfulness app on his phone using "MAI speech models". His point: MAUI "looks cool, but it's a little complicated. I'm telling you now, it's not." (The stream agent names the host Jon; the transcript does not say his name here.)
- Source: dotnetconf.net/agenda (4:30 PM ET); host segment transcript 20261111-162801.
-->

---
layout: "shot"
image: "/shots/day2/163719.jpg"
time: "Day 2 · 16:37"
---

# maui-labs: CLI, AI skills, DevFlow and Inspector give agents eyes and hands (pre-release)

<!--
- Say: The MAUI team's maui-labs repo has four tools so an AI agent can set up, see and drive a MAUI app: the MAUI CLI, AI skills, DevFlow ("Playwright for your mobile applications") and the Inspector. All pre-release.
- On screen, "Four tools from maui-labs":
  - MAUI CLI (`maui doctor`): finds and fixes environment issues; installs Android SDK, JDK and emulators; manages Xcode, simulators and runtimes; `--json` output for CI.
  - AI skills (`maui ai init`): installs MAUI and DevFlow skills; adds Copilot agents and MCP config; targets VS Code, Copilot CLI and Claude; `--dry-run` previews every change.
  - DevFlow (`maui devflow`): visual tree, taps and screenshots via an in-app agent; network monitoring and profiling; Blazor WebViews over Chrome DevTools; an MCP server lets AI agents test your app.
  - Inspector (Browser · VS Code · Copilot): live screenshot, visual tree of every control, properties, layout and bindings, logs, network and diagnostics.
- Gerald (16:34): the repo is github.com/dotnet/maui-labs; it "is set up as a marketplace", so you point your agent at it for the skills, or get them through the CLI.
- DevFlow (16:36): the agent asks for the visual tree, "it doesn't have to guess based on a screenshot ... including things that might be invisible ... Or have a zero width." "this will save you tokens". "You can see this as Playwright for your mobile applications".
- Status: "everything in MAUI Labs is a pre-release right now".
- Also in maui-labs (README "At a glance", 16:43, shot 20261111/164314): Comet ("Experimental MVU UI framework for .NET MAUI with C# fluent UI, signals, and reactive state"), Go (single-file Comet app server), AI Extensions (source-generated Microsoft.Extensions.AI tool bindings), a macOS AppKit backend ("running MAUI apps as macOS apps without Mac Catalyst"), a WPF backend, Essentials.AI (on-device chat, embeddings, tool calling), AppProjectReference, MAUI Testing (MTP-based device tests). Gerald also said "we have a Linux backend in here".
- MAUI Sherpa (16:38), not in maui-labs: a visual tool "built by Jonathan on our team" (Gerald's "Get started" slide confirms: "MAUI Sherpa and Mobile Canvas, by Redth", i.e. Jonathan Dick. Not Jonathan Peppers.) It sets up Android SDK and Xcode, checks .NET SDKs, handles certificates, builds, uploads to app stores, manages secrets: "mission control for mobile development". Not only for MAUI apps.
- Why it matters: agents read the real UI state of iOS and Android apps instead of guessing from screenshots. (Inference) It parallels winapp for WinUI from the Day 2 WinUI session (earlier in this deck).
- Source: 16:34-16:43 ET, transcripts 20261111-163402, 20261111-163604, 20261111-163803, 20261111-164204; shots 20261111/163719 and 164314.
-->

---
layout: "shot"
image: "/shots/day2/165242.jpg"
time: "Day 2 · 16:52"
---

# Mobile Canvas: you and Copilot drive the same simulator, inside the editor

<!--
- Say: Mobile Canvas mirrors the iOS simulator or Android emulator inside your editor or the GitHub Copilot app, so you watch Copilot drive the same device you use. It reads the accessibility tree, not just pixels. It is a community tool.
- On screen: "A live simulator or emulator inside your editor. You and Copilot drive the same device. Reads the accessibility tree, not just pixels." VS Code: Mobile Canvas extension; `/plugin install mobile-canvas`; github.com/Redth/mobile-canvas-ghcp; "Community tool by Redth (Jonathan Dick)".
- Gerald (16:52): "if you're working with the GitHub Copilot app like I am daily, then you can now bring up these canvases on the right side". "It's just a mirror of the iOS simulator or the Android emulator, and it will show you in live, real time, what is going on with your application".
- Inspector (16:50): runs as a web app in VS Code, in Copilot CLI, or as a GitHub Copilot app canvas; live property inspector: "you can change every property on that control it will show up live in your application".
- DevFlow point (slide "The visual tree beats a screenshot", 16:45): screenshot only "Guesses coordinates from pixels ... Breaks when the layout shifts"; DevFlow visual tree "Taps controls by name ... Knows properties and state".
- Name note: the stream agent called the canvas author Jonathan Peppers; the slide says Redth (Jonathan Dick). Use the slide.
- Source: 16:45-16:53 ET, transcripts 20261111-164405, 20261111-165002, 20261111-165202; shots 20261111/164505 and 165242.
-->

---
layout: "shot"
image: "/shots/day2/165542.jpg"
time: "Day 2 · 16:55"
---

# "Ask for proof": three commands to give your agent eyes on a MAUI app

<!--
- Say: To start: install the MAUI CLI, run `maui ai init`, then add DevFlow and open the Inspector. Gerald's main tip: ask the agent for proof at runtime, not just code.
- On screen, "Get started": `dotnet tool install -g Microsoft.Maui.Cli --prerelease`; `maui ai init --env VsCode --yes`; "Ask your agent to add DevFlow, then open the Inspector": `maui devflow broker start`, http://localhost:19223/inspector/; docs: github.com/dotnet/maui-labs; "MAUI Sherpa and Mobile Canvas, by Redth": github.com/Redth. (This confirms Sherpa is by Redth / Jonathan Dick.)
- Gerald's tips (16:54): "start from a running app, ask for proof ... with DevFlow it can even do screenshots and screen recordings". "The code is less important for me now ... but that it runs at runtime, absolutely still important". "commit the MAUI AI ... setup ... so that everyone has the same skills". "Keep DevFlow only for your debug builds and always, it hasn't changed with AI, always test it on actual real devices."
- Viewer comment (16:56): DevFlow "as part of a PR review. After the review, the agent used it to confirm the bug it found, write the fix, and confirm it was done."
- Q&A: for WPF, "look for something that's called Aloha, A-I-loha" — "an experiment that we didn't really promote enough yet", the same idea for WPF, Windows "but also for other frameworks".
- Source: 16:54-16:57 ET, transcripts 20261111-165402 and 20261111-165602; shot 20261111/165542.
-->

---
layout: "session"
num: 8
time: "Day 2 · 5:01 PM"
speakers: "Alexandre Zollinger Chohfi"
---

# No XAML Required: Native Windows Apps in Pure C#

<!--
- [Session 08 · Day 2] Alexandre Zollinger Chohfi. Started about 5:01 PM ET.
- Source: dotnetconf.net/agenda (5:00 PM ET); transcript 20261111-170019.
-->

---
layout: "shot"
image: "/shots/day2/170204.jpg"
time: "Day 2 · 17:02"
---

# Microsoft.UI.Reactor: a WinUI app in one C# file, no XAML (experimental)

<!--
- Say: Microsoft.UI.Reactor is an experimental MVU framework for WinUI. No XAML, no code-behind, no view models; a whole app can be one C# file you run with `dotnet run`. It uses real WinUI controls.
- On screen, "Microsoft.UI.Reactor / An experimental C# framework for WinUI": MVU for WinUI ("your UI is a function of your state. The counterpart to MVVM, on the same platform"); Real WinUI controls ("No new renderer, no fork. Button is a real WinUI Button, with the same theming and tools"); An open experiment ("MIT and built in the open. No API guarantees yet, so your feedback still changes the design").
- Alexandre (17:00): "an experimental way to build native Windows applications ... There are no XAML files. There are no code behind. There's no view models. And I mean experimental as an invitation." "What if a complete application could be just a single C-sharp file? No project file, no app.xaml, no code behind ... And if you run that file with a plain dotnet run, it just runs your full UI."
- Say "experimental": no API guarantees yet.
- Why it matters: a native Windows UI with no XAML, written and run like a script. (Inference) It parallels the Comet MVU experiment in maui-labs.
- Source: 17:00-17:02 ET, transcript 20261111-170019; shot 20261111/170204.
-->

---
layout: "code"
---

# Reactor `UseReducer`: state and actions are records, the update is a pure function

```csharp
record Cell(bool IsMine, bool IsRevealed, bool IsFlagged, int AdjacentMines);

abstract record GameAction;
record Reveal(int X, int Y) : GameAction;
record ToggleFlag(int X, int Y) : GameAction;
record NewGame : GameAction;

var (state, dispatch) =
    UseReducer<GameState, GameAction>(
        GameReducer.Reduce,
        GameState.New(16, 16, 40));

Button(label, () => dispatch(new Reveal(x, y)))
```

<!--
- Say: For bigger state, Reactor has UseReducer: one state record, every move is a record, and the reducer is a pure C# function (state, action) → next state. You can unit test it with no window.
- Code is from the stream slide "UseReducer" (17:12, shot 20261111/171258): a Minesweeper game. Slide text: "One state record. Every move in one place. Each one is a record. A pure function you can unit test, with no window."
- Alexandre (17:12): "From MVVM the biggest difference is there is no INotifyPropertyChanged. There's no binding". For simple values, use UseState; for more complex state, "we provide another method called the useReducer". "The state is a record and every move is also a record." "the use reducer method gives us the current state and a dispatch function". "state and action in" and the next state out.
- Headless testing (17:14): the reducer has "no controls no dispatcher no UI types", so "you can unit test this whole application with literally every single move in a headless ... test project without any windows".
- The one rule (slide "The one rule", shot 20261111/171439): "Hooks are tracked by call order. Never call one conditionally: no ifs, loops or early returns. The analyzer catches it as you type: REACTOR_HOOKS_001." Wrong: UseState inside `if (isLoggedIn)`; right: call UseState every time, then branch on the value. Alexandre: "That's basically the same rule that you have with React and for exactly the same reason."
- Experimental: no API guarantees yet.
- Source: 17:12-17:15 ET, transcripts 20261111-171203 and 20261111-171404; shots 20261111/171258 and 171439.
-->

---
layout: "shot"
image: "/shots/day2/171729.jpg"
time: "Day 2 · 17:17"
---

# Reactor keys: insert one row, update one control, not five

<!--
- Say: In Reactor, give list items a key with `.WithKey(item.Id)`. Without keys the diff matches by position and rewrites every row after an insert; with keys it creates one and keeps the rest.
- On screen, "Why keys matter / Insert X at the top of A, B, C, D": without keys ("matched by position") → "4 rewritten, 1 created"; with keys `.WithKey(item.Id)` → "1 created, 4 kept".
- Alexandre (17:16): the Minesweeper board is "256 interactive buttons, and every cell gets a key ... the key gives each cell a stable identity". "Without the keys, the diff can only compare by position ... With keys, Reactor matches the rows by the identity."
- (Inference) Same idea as keys in React and other virtual-DOM UIs; it matters for lists and grids.
- Source: 17:16-17:17 ET, transcript 20261111-171604; shot 20261111/171729.
-->

---
layout: "shot"
image: "/shots/day2/171829.jpg"
time: "Day 2 · 17:18"
---

# Reactor ships 60+ Roslyn analyzers that catch UI bugs as you type

<!--
- Say: Because Reactor UI is just C#, it ships Roslyn analyzers that catch UI bugs before you build: conditional hooks, missing keys, hard-coded colors, missing accessible names, typos, UI calls from background threads.
- On screen, "60+ analyzers catch UI bugs as you type": REACTOR_HOOKS_001 (a hook called conditionally); REACTOR_DSL_001 (a list item missing .WithKey); REACTOR_THEME_001 (a hard-coded color, not a theme token); REACTOR_A11Y_001 (an icon-only button with no accessible name); REACTOR_DYM_003 ("Buton(...)? Did you mean Button?"); REACTOR_THREAD_001 (a UI-thread call from a background thread).
- Alexandre (17:18): "We have more than 60 of them, I think 62." A hard-coded color "looks fine in light mode and breaks in dark mode"; an icon-only button "a screen reader can only announce as a button"; a UI update from a background thread "you normally only find when the app actually crashes".
- "because these are just Roslyn analyzers, it shows up in Visual Studio, it shows up in VS Code, and even in just a build output from a simple .NET build from the CLI."
- Why it matters: with no XAML, the compiler and analyzers see the whole UI, so accessibility and theming bugs show up as squiggles. (Inference) Agents that build and read diagnostics get the same feedback.
- Source: 17:18-17:19 ET, transcript 20261111-171804; shot 20261111/171829.
-->

---
layout: "shot"
image: "/shots/day2/172138.jpg"
time: "Day 2 · 17:21"
---

# XAML isn't going away. Don't migrate; add Reactor to one new screen.

<!--
- Say: Reactor does not replace XAML. XAML stays first-class, the two interop both ways in one visual tree, and the advice is: don't migrate, try Reactor on one small new screen.
- On screen, "XAML isn't going away": "XAML is first-class and still getting active investment. Interop runs both ways, in one process and one visual tree. Don't migrate. Pick one small, new screen and add Reactor there." Code: `<reactor:ReactorHostControl ComponentType="local:Dashboard" />` (Reactor inside a XAML page) and `VStack(XamlPage(typeof(SettingsPage)), XamlHost(() => new SignaturePad()))` (XAML inside a Reactor component).
- Alexandre (17:21): "XAML is a first-class way of building WinUI applications and it is not deprecated."
- Lessons from building it (17:20): keys "matter more than we originally first thought"; when something felt slow, "everyone's instinct was just to say that the diff itself was slow, which almost never was the case. The profiler kept pointing at allocations" from fluent modifier chains; "implementing docking took way more design time than the reconciler did".
- Version (17:22): hosting Reactor in a XAML page "is new in Reactor Preview.17 that we shipped last week". "if you are on WinForms, there is also an interop package for that too".
- Next demo: Reactor DevTools via `winapp run --watch`; "--watch" is "not shipped publicly yet" (winapp run is). Hot reload demo (17:24): he changed a font factor "from 0.55 to 0.95", saved, and only that one number grew; "my flags are still there, my bombs are still there ... This is just hot reloading a live app", inside a packaged app. "this is in preview, this is not in the stable version 0.8 that we shipped of the WinApp CLI."
- Why it matters: this is an experiment you can try in an existing XAML app, not a migration.
- Source: 17:20-17:23 ET, transcripts 20261111-172003, 20261111-172204, 20261111-172404; shot 20261111/172138.
-->

---
layout: "shot"
image: "/shots/day2/172728.jpg"
time: "Day 2 · 17:27"
---

# Agents see what DevTools sees: component tree with C# file and line

<!--
- Say: Everything Reactor shows in its DevTools is also a CLI an agent can call: the component tree with the C# file and line for each node, and every hook's state, which it can also set. Passwords are redacted.
- On screen, "What DevTools sees": `winapp devtools inspect -a RxE2E` → `<App> root Program.cs:7`, `<Counter> Program.cs:17`, `Button #incrementButton Program.cs:33`. `winapp devtools get-state "<Counter>" -a RxE2E` → Hooks: `[0] count state int = 0 settable`, `[1] password state string = <redacted>`.
- Alexandre (17:26): "all the capabilities that are exposed by Reactor to the DevTools are also exposed ... from a command line tool that an LLM can call." "it also gives you the C-sharp file and the line for every node. So the agent will actually have that context and know which line of code actually matches". get-state shows "each hook with its name, the types, the values, and we also have a set state that lets you change it. Passwords are redacted".
- Status: (Inference) preview, like the --watch demo just before; this chunk did not restate it.
- Why it matters: the agent can jump from what it sees on screen straight to the exact line of C# that made it.
- Source: 17:26-17:28 ET, transcript 20261111-172603; shot 20261111/172728.
-->

---
layout: "shot"
image: "/shots/day2/172829.jpg"
time: "Day 2 · 17:28"
---

# Built with Reactor: OpenClaw ships it; Uno takes it cross-platform

<!--
- Say: Reactor is already used outside Microsoft: OpenClaw's Windows companion ships its chat window with Reactor in production, and Uno Platform ported Reactor to macOS, Linux, WebAssembly, Android and iOS. Try it with three commands.
- On screen, "Built with Reactor / MIT licensed, built in the open": samples Reactor IDE, Monaco Editor, Chat. OpenClaw: "In production: its Windows companion app ships Reactor chat, on by default." Uno Platform: "Out now: Reactor on macOS, Linux, WebAssembly, Android and iOS." Prefer Rust?: "windows-reactor runs the same experiment in windows-rs."
- Alexandre (17:28): OpenClaw "recently announced their Windows Companion app, and they are using Reactor in production for the chat window. It is all open source". Uno's port: "The same components, the same hooks, running also on macOS, Linux, WebAssembly, Android, and iOS. And it's, again, also experimental, just like Reactor."
- Try it (17:29): "Install the WinApp CLI with WinGet. Run WinApp new with the new Reactor templates", then run it; "there are five" templates.
- Wrap (17:30): they are bringing "the new functionalities from C# 15 into Reactor". Repo: github.com/microsoft/microsoft-ui-reactor; guide: microsoft.github.io/microsoft-ui-reactor (closing slide, shot 20261111/173018). Q&A: the Reactor WinUI Gallery code listings are MIT: "just copy and paste".
- Why it matters: an experiment with real users already, and a path off Windows via Uno.
- Source: 17:28-17:31 ET, transcripts 20261111-172804 and 20261111-173003; shots 20261111/172829 and 173018.
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
