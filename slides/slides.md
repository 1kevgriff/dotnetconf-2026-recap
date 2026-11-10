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
layout: "section"
kicker: "Keynote"
---

# .NET 11 ships

<!--
[Keynote] Scott Hanselman, Damian Edwards, Chet Husk, Daniel Roth.
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
