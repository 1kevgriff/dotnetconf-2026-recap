---
theme: default
title: .NET Conf 2026 Recap - AI and agents
info: |
  ## .NET Conf 2026 Recap - AI and agents
  Kevin Griffin - Microsoft MVP
  .NET AI, Copilot, MCP, agentic UI, Foundry: highlights from Day 1 (2026-11-10) and Day 2 (2026-11-11), captured live.
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

- AI and agents
- Kevin Griffin
- Microsoft MVP

<!--
- [title]
- Say: This is a .NET Conf 2026 recap on one topic: .NET AI, Copilot, MCP, agentic UI, Foundry. It pulls the highlights from Day 1 (2026-11-10) and Day 2 (2026-11-11), captured live from the stream.
- Sessions in this deck:
  - 01 From the keynote: AI and agents (Day 1, 11:00 AM)
  - 02 The .NET AI Stack: What's New, What's Next, and How It Fits Together (Day 1, 2:00 PM)
  - 03 Beyond Autocomplete: Getting the Most from GitHub Copilot for .NET (Day 1, 5:00 PM)
  - 04 What's new in the MCP C# SDK (Day 2, 2:00 PM)
  - 05 Building the future of agentic UI with Blazor (Day 2, 3:01 PM)
  - 06 GitHub Copilot modernization (Day 2, 4:03 PM)
  - 07 .NET + Foundry: Better Together (Day 2, 7:03 PM)
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

# From the keynote: AI and agents

<!--
- [Session 01 · part of the Day 1 keynote] 11:00 AM ET, 2026-11-10.
- Say: The Day 1 keynote was a one-hour tour of .NET 11. These slides are the keynote parts about .NET AI, Copilot, MCP, agentic UI, Foundry.
- Next slides: Modernization results, Windows 365, agents in a box, .NET AI, Llama on Windows, the Copilot app, dotnet/skills.
-->

---
layout: "shot"
image: "/shots/113638.jpg"
time: "Day 1 · 11:36"
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
time: "Day 1 · 11:38"
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
time: "Day 1 · 11:40"
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
time: "Day 1 · 11:41"
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
time: "Day 1 · 11:43"
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
time: "Day 1 · 11:45"
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
layout: "shot"
image: "/shots/114707.jpg"
time: "Day 1 · 11:47"
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
time: "Day 1 · 11:48"
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
layout: "session"
num: 2
time: "Day 1 · 2:00 PM"
speakers: "Luis Quintanilla"
---

# The .NET AI Stack: What's New, What's Next, and How It Fits Together

<!--
[Session 02 · Day 1]
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
time: "Day 1 · 14:05"
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
time: "Day 1 · 14:11"
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
time: "Day 1 · 14:16"
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
time: "Day 1 · 14:19"
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
time: "Day 1 · 14:22"
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
time: "Day 1 · 14:26"
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
num: 3
time: "Day 1 · 5:00 PM"
speakers: "Wendy Breiding"
---

# Beyond Autocomplete: Getting the Most from GitHub Copilot for .NET

<!--
[Session 03 · Day 1] Agenda time 5:00 PM ET; started ~5:01.
- Keynote already covered Wendy's Copilot app demo (RSVP race fix) and dotnet/skills evals; add only new details here.
- Demo app (17:02): WinForms front end + ASP.NET Core API + Postgres, for purchase orders. Bug: "15 copies of the same purchase order in our database"
- One bug, three tools: fix UI error handling in Visual Studio → API resilience in VS Code (so it "only submits one version of the purchase order") → a report of the duplicates in the Copilot app
-->

---
layout: "shot"
image: "/shots/170443.jpg"
time: "Day 1 · 17:04"
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
num: 4
time: "Day 2 · 2:00 PM"
speakers: "Stephen Halter"
---

# What's new in the MCP C# SDK

<!--
- [Session 04 · Day 2] Stephen Halter, a developer on the .NET team who worked a lot on ASP.NET Core with Dan Roth. A demo-heavy session.
- His MCP intro (14:01): MCP is the Model Context Protocol, "essentially a way to plug in agents into your software in a reusable way." He said it became popular around the end of 2024.
- First demo: a fireworks control tool.
- Source: 14:00-14:02 ET, transcript 20261111-140003; dotnetconf.net/agenda (2:00 PM ET).
-->

---
layout: "shot"
image: "/shots/day2/140353.jpg"
time: "Day 2 · 14:03"
---

# MCP Apps: a tool call returns live, interactive UI in the chat

<!--
- Say: MCP Apps (formerly MCP-UI) lets an MCP tool return a small interactive app that shows inline in the chat. The C# SDK supports it.
- Demo: in VS Code Copilot Chat, "launch fireworks" called the `launch_fireworks` tool of the fireworks MCP server. The reply was an inline panel "A little celebration / BUILD SOMETHING BRILLIANT" with show title, theme, intensity, finale message and a "LAUNCH SHOW" button.
- Stephen (14:03): "it shows in line this iframe, which is returned from MCP. So this is using a feature that used to be called MCP-UI, is now called MCP apps."
- The panel is tagged "MCP / SIGNALR / LIVE": the same show runs on a second screen kept in sync with SignalR.
- Why it matters: tools can return UI, not only text, so an agent chat can host small apps from your .NET server.
- Source: 14:02-14:04 ET, transcripts 20261111-140203 and 20261111-140404; shot 20261111/140353.
-->

---
layout: "shot"
image: "/shots/day2/140549.jpg"
time: "Day 2 · 14:05"
---

# An MCP server is a few lines in ASP.NET Core. Stateless is now the default.

<!--
- Say: The MCP C# SDK plugs into ASP.NET Core like any other service: AddMcpServer, then add tools, prompts, resources and MCP Apps. HTTP transport is stateless by default now.
- On screen (Program.cs, FireworksServer): `builder.Services.AddSignalR();` then `builder.Services.AddMcpServer(options => { ServerInfo ... ServerInstructions ... }).WithTools<FireworksTools>().WithPrompts<FireworksPrompts>().WithResources<FireworksResources>().WithMcpApps();`
- Stephen (14:04): the server "supports either Standard I.O. or HTTP, but by default it is using HTTP". "we're using the stateless mode, which we recently made the default. And this is useful for scalability if you don't have sticky sessions and just like general reliability so your server lasts past a restart."
- MCP Apps: the chat showed an inline iframe returned from MCP: "a feature that used to be called MCP-UI, is now called MCP apps."
- SignalR in the same app keeps a second browser tab in sync with the same fireworks show.
- Why it matters: an MCP server is just ASP.NET Core, so it gets DI, SignalR, hosting and scale-out like any web app.
- Source: 14:04-14:06 ET, transcript 20261111-140404; shot 20261111/140549.
-->

---
layout: "shot"
image: "/shots/day2/141105.jpg"
time: "Day 2 · 14:11"
---

# MCP C# SDK: 6 packages. Skills is new and experimental.

<!--
- Say: The MCP C# SDK is now six packages: three base layers, and three optional extensions for Apps, Tasks, and the new experimental Skills.
- On screen, "MCP C# SDK packages" (arrows = depends on):
  - Base: ModelContextProtocol.AspNetCore (ASP.NET Core HTTP integration) → ModelContextProtocol (hosting, DI + attribute discovery) → ModelContextProtocol.Core (client + low-level server APIs, protocol + transport primitives).
  - Optional, transport-independent: Extensions.Apps (interactive UI in compatible MCP hosts); Extensions.Tasks (long-running tool operations, status polling + input requests); Extensions.Skills (serve/consume Agent Skills, verifiable file manifests). Badge: "SKILLS: NEW / EXPERIMENTAL". "Extensions do not require AspNetCore."
- Stephen (14:10): "Right now we have six packages." For a remote MCP server "you have to use the model context protocol ASP.NET Core package". MapMcp takes route parameters: "you can host multiple MCP servers at different endpoints inside of your ASP.NET Core app."
- Also: resources give "something a bit like a file directory through the MCP interface"; prompts are "parameterized instructions". Tip: the MCP Inspector "tends to get new features first".
- Governance (14:12): MCP "was originally created by Anthropic, but they then donated it to the Linux foundation that spun off the agentic AI foundation". The C# SDK is "one of the official SDKs"; "We help maintain the C-sharp SDK here at Microsoft"; in the new tiering, "C-sharp SDK is a tier one." See modelcontextprotocol.io.
- Tools look like MVC controller methods; "This is all AOT compatible." Parameters can come from DI, e.g. IHubContext for the SignalR sync (14:14).
- Template (14:18): "You can use .NET new MCP server" (check the exact template short name). It makes a Celsius-to-Fahrenheit tool, with remote and local options. "installed if you have the latest .NET 11 SDK. Even the .NET 10 SDK has this."
- Why it matters: pick only what you need; Skills over MCP is the new piece to watch, but it is experimental.
- Source: 14:10-14:18 ET, transcripts 20261111-141000, 20261111-141200, 20261111-141400, 20261111-141800; slide shot 20261111/141105.
-->

---
layout: "shot"
image: "/shots/day2/142114.jpg"
time: "Day 2 · 14:21"
---

# Elicitation: the MCP server asks the human, not the model

<!--
- Say: With elicitation, an MCP server can stop and ask the user for input through a typed form. The model cannot fill it in. Good for release controls and approvals.
- Stephen (14:18): elicitation gives "another benefit beyond just a command line API or a skill. When you implement an MCP server, you can do requests that basically instead of taking parameters from the model or the agent, the rule is that you have to expose elicitations to the user."
- Demo, a "release-planner" MCP server: "Release controls for source.dot.net 2.0" with Target environment (production), Rollout strategy (canary), Initial rollout percentage (10), Rollback error-rate threshold (1); buttons Cancel / Decline / Accept.
- Then "a second elicitation where my server said that before we make any action, we need to approve a release plan."
- Code: the tool sets up "elicit request params" with "a request schema that took various enums" and numbers with ranges (percent 1 to 100).
- New in the latest SDK, stateless elicitation (14:22; slide "How multi-round tool requests work", label "NATIVE MRTR • 2026-07-28"): 1 Return: InputRequiredResult ends this request. 2 Ask: host gathers structured input. 3 Retry: new request with answers + state.
  - Stephen: before, it "required doing a server-to-client request. And that required sticky sessions". Now the server returns "an error which says, hey, we require more input ... Send us the input along with the entire new request." "You don't need a sticky session. If your server dies, you can restart."
  - Caveat he gave: the demo round-trips state as base64, "that's not secure. You should use data protection".
  - A "mixed mode" (from an internal Microsoft team) supports older clients too.
- Why it matters: a clean human-in-the-loop gate for risky agent actions, enforced by the server, and it now scales without sticky sessions.
- Source: 14:18-14:23 ET, transcripts 20261111-141800, 20261111-142004, 20261111-142201; shots 20261111/142114 and 142241.
-->

---
layout: "shot"
image: "/shots/day2/142500.jpg"
time: "Day 2 · 14:25"
---

# Protect an MCP server with normal ASP.NET Core auth. No tokens for the agent.

<!--
- Say: MCP auth uses the ASP.NET Core auth you know: RequireAuthorization on MapMcp, JWT bearer, and an Entra sign-in. Your tools get the user's ClaimsPrincipal, and the agent never holds a token.
- On screen (ProtectedMcpServer sample, Program.cs): `app.UseAuthentication(); app.UseAuthorization(); app.MapMcp().RequireAuthorization("McpTools")...`. The HTTP transport sets `options.SessionMode = HttpServerSessionMode.Stateless;` with a comment that stateless is the default and recommended.
- Stephen (14:24): "we're using require authorization on MapMCP. So this should be very familiar to anyone who's used ASP.NET Core authorization. And it's even using AddJwtBearer." The one special call adds MCP to the authentication builder, "which gives the client the data that it needs to authenticate."
- Flow: the client says you must sign in; a browser opens for Entra. In tool handlers "you'll have a claims principal where you can see what roles that user is in". "you don't need to put tokens inside of your environment and stuff and give access to secrets to the agent."
- The sample is in the modelcontextprotocol C# SDK repo ("protected MCP sample").
- Q&A (14:29), enterprise: third-party MCP clients usually register through "a client ID metadata document or dynamic client registration", so the enterprise can see it is "not just Stefan that's connecting. It's like Stefan through GitHub Copilot app." If you control the clients, "you can put any kind of ASP.NET Core auth handler in front of it" (bearer token, DPoP, ...).
- Why it matters: remote MCP servers can use per-user identity and roles, not shared API keys in the agent's config.
- Source: 14:24-14:30 ET, transcripts 20261111-142400 and 20261111-143000; shot 20261111/142500.
-->

---
layout: "session"
num: 5
time: "Day 2 · 3:01 PM"
speakers: "Daniel Roth"
---

# Building the future of agentic UI with Blazor

<!--
- [Session 05 · Day 2] Daniel Roth, his second session on Day 2 (after Blazor Server at 1:31 PM, in the ASP.NET Core and Blazor deck). Started about 3:01 PM ET.
- Source: dotnetconf.net/agenda (3:00 PM ET); stream agent session marker at 3:01 PM ET.
-->

---
layout: "shot"
image: "/shots/day2/150736.jpg"
time: "Day 2 · 15:07"
---

# New official AG-UI SDK for .NET: connect an agent to your app's UI

<!--
- Say: AG-UI is the protocol between an agent and the app where the user works. There is now an official .NET SDK, from the .NET team with CopilotKit: MIT, on NuGet, stable, and it plugs into IChatClient.
- Dan (15:06): "AGUI stands for the Agent-User Interaction Protocol. It's an open, event-driven protocol for agent-human interactions through an application." The app sends messages, its current state, front-end tools the agent can use, and user decisions; the agent streams text, tool activity, state updates, and requests for input.
- Where it fits: MCP is "like the agent to tools protocol"; A2A is "the agent to agent protocol"; "The AGUI protocol allows us to connect the agent to the application where the person is working."
- On screen, "Official AG-UI SDK for .NET / Open-source protocol SDK. First-class MAF integration.":
  - AGUI.Client: consume endpoints as IChatClient. AGUI.Server: expose IChatClient as AG-UI. "Stable SDK / MIT / NuGet / No MAF required".
  - Microsoft Agent Framework: "Built on the official AGUI.* packages": `builder.Services.AddAGUIServer();` `app.MapAGUIServer("/agent", agent);` "ASP.NET Core adapter / AIAgent / Preview".
  - "C# / Python / TypeScript. One interaction contract."
- Teaser demo (15:04): an agent next to a normal support UI looked into a delayed docking-station order and recommended an upgraded replacement with 12 units available.
- Why it matters: the agent can read and act on the screen the user already has, instead of living only in a chat box.
- Source: 15:04-15:07 ET, transcripts 20261111-150400 and 20261111-150601; slide shot 20261111/150736.
-->

---
layout: "shot"
image: "/shots/day2/151720.jpg"
time: "Day 2 · 15:17"
---

# Blazor AI components: the agent works in your form, you accept or discard

<!--
- Say: The experimental Blazor AI components give you chat, tool rendering, shared state and proposed changes as Razor components. In the demo the agent filled the case form, saw the user's edits, and proposed a customer reply that the user could accept or discard.
- Dan (15:08): "the experimental Blazor AI components give us building blocks for building agentic UI using familiar Razor components" (a chat page, message list, message input). Basic chat "can actually work with any IChatClient from Microsoft.Extensions.AI"; here they connect over AG-UI.
- Front-end tools: the agent calls into the UI. "it was able to make a call into the front end using a front end tool." Tool calls from front end and back end render with a block renderer you can customize.
- Under the components: "a UI agent abstraction that takes an IChatClient", and "a UI agent of T" for typed shared state. Shared state "keeps us working with the same information"; updates can be "full state snapshots" or "partial updates". Proposed state: call the "set predictive state API", then the change "can either be accepted or rejected"; the components provide rollback.
- On screen (eShop returns case): agent panel "Work the case together", buttons Investigate / Show review / Request approval; "Review reply edits ... Accepting edits does not send the reply or confirm the resolution." Discard reply edits / Accept reply edits. The reply offers a compatible upgrade dock or a full refund of $149.
- Dan apologized for some flaky "preview features" during the demo. Say "experimental".
- Why it matters: agent help lives inside the real app UI, with the human approving each change.
- Source: 15:08-15:17 ET, transcripts 20261111-150804, 20261111-151004, 20261111-151204, 20261111-151404/151605; shot 20261111/151720.
-->

---
layout: "shot"
image: "/shots/day2/152535.jpg"
time: "Day 2 · 15:25"
---

# Approval-required tools: rejected means the tool never runs

<!--
- Say: For risky actions, wrap the tool in ApprovalRequiredAIFunction. AG-UI tells the Blazor client, which shows an approval block. If the user says no, the tool is never called.
- Dan (15:24): "Instead of it just being an AI function, you make it an approval-required AI function. And so if you have one of those, then the AGUI protocol implementation will detect that and let the client know." The user accepts or rejects, "And that will actually prevent the tool from even being invoked ... It'll literally stop it from happening." Render it with "a function approval block".
- On screen (AgentHosting.cs, eShopCustomerService.AgentServer): `new ApprovalRequiredAIFunction(AIFunctionFactory.Create(tools.ConfirmResolutionAsync, "confirm_resolution", ...))` next to a plain `AIFunctionFactory.Create(tools.GetCaseContextAsync, "get_case_...")`; then `app.MapAGUIServer("/api/agents/returns/{orderId:int}", new CaseStateAgent(...)).WithMetadata(new AGUIStreamOptions().MapResult("confirm_resolution", MapWorkspaceStateSnapshot)).RequireAuthorization("CustomerService")`. Also `AllowMultipleToolCalls = false`.
- Demo: he asked the agent to request approval; the approval prompt appeared; he said yes; "the replacement confirmed with one unit allocated".
- The app: Blazor front end, Agent Framework agent server, Aspire AppHost (solution eShopCustomerService, 8 projects).
- Why it matters: human-in-the-loop is enforced at the tool, not just suggested in the prompt, and the endpoint uses normal ASP.NET Core authorization.
- Source: 15:20-15:25 ET, transcripts 20261111-152000/152200/152400; shot 20261111/152535.
-->

---
layout: "shot"
image: "/shots/day2/152620.jpg"
time: "Day 2 · 15:26"
---

# Agentic UI in .NET: AG-UI SDK + Agent Framework + Blazor AI components

<!--
- Say: Dan's summary of the stack: the AG-UI .NET SDK for the protocol, Agent Framework to expose agents over AG-UI, and Blazor AI components for the UI. Get started at aka.ms/blazor/ai-components. The components are experimental.
- On screen, "Build agentic UI with .NET / Useful agents. Shared context. People in control.": AG-UI .NET SDK ("Official .NET support for the AG-UI protocol"; messages, tool calls, shared state); Microsoft Agent Framework ("Expose your agents over AG-UI"; application tools + approval workflows); Blazor AI components ("Build agentic UI with AG-UI"; rich interaction, previews, user control).
- Dan (15:26): "You can get started today by going to aka.ms slash Blazor slash AI dash components. Again, these components are currently experimental, and some of these features are preview."
- Fun fact: the Q&A board on the stream is a Blazor app that James Montemagno built.
- Q&A (15:28-15:30):
  - Models: the demo used Microsoft Foundry, but Microsoft.Extensions.AI abstractions let you plug in other models.
  - Generative UI is a spectrum: AG-UI state deltas that update a dynamic UI ("very restrictive"); A2UI on top of AG-UI, where the app offers "a catalog of widgets and components" and the agent picks them via a JSON payload; up to "here's an iframe ... Render whatever you want." CopilotKit "authored the AG-UI spec" and has React components.
- Source: 15:26-15:31 ET, transcripts 20261111-152600, 20261111-152804, 20261111-153004; slide shot 20261111/152620.
-->

---
layout: "session"
num: 6
time: "Day 2 · 4:03 PM"
speakers: "Mika Dumont"
---

# GitHub Copilot modernization

<!--
- [Session 06 · Day 2] Mika Dumont. Started about 4:03 PM ET.
- Jason Chlus pointed here on the morning of Day 2: "if you're a little bit worried about making the jump from one of the older versions of .NET, like .NET 8 or .NET 9, to .NET 11, you should check out Mika's section on the Modernization agent."
- Source: dotnetconf.net/agenda (4:00 PM ET); transcript 20261111-122404 for Jason's pointer.
-->

---
layout: "shot"
image: "/shots/day2/160738-crop.jpg"
time: "Day 2 · 16:07"
---

# Upgrade agent: Web Forms eShop → ASP.NET Core on .NET 11, build green

<!--
- Say: Mika ran the GitHub Copilot upgrade agent on a legacy ASP.NET Web Forms eShop with the prompt "Upgrade my project to .NET 11". It assessed the app, planned, executed task by task with commits, and finished with a passing build and zero errors.
- On screen, "Upgrade Agent Dashboard / Assessment": 1 project, 0/1 TFM upgraded; 41 incidents, 29 mandatory, 41 effort points; 13 incompatible packages, 0 version drift. By category: NuGet 33, Binding 5, Project 2, Feature 1. Example issues: "NuGet package is incompatible", "Convert application initialization code from Global.asax.cs to .NET Core", "Project file needs to be converted to SDK-style".
- Modes (16:06): "automatic mode" end to end, or "guided where I pause after each stage for review"; commit strategy "after each task".
- It is "a side by side upgrade": the new ASP.NET Core app sits next to the old one. Mid-run (16:16) the dashboard showed "681 files changed, seven commits created".
- End (16:20): "there are zero errors. The upgrade is complete and the build did pass."
- Available in Visual Studio, VS Code, GitHub Copilot CLI, Copilot cloud agent, the GitHub Copilot app (today's demo), and "Modernize CLI ... for portfolio scale modernization". Get started: aka.ms/upgrade-agent, github.com/microsoft/upgrade-agent-plugins (closing slide).
- Near the end (dashboard at 16:20, shot 20261111/162000, not in deck because it shows a personal repo name): "Upgrading to .NET 11 · 93% · 1h 21m elapsed · Started 07:55 AM · 13 of 14 tasks done"; 698 files changed (+626,463 / −114), 12 commits; build status still "Failing" at that moment. Seconds later Mika said the build passed. So say "the run took about 1h20m, about 700 files, 12 commits". (Inference) The run was recorded earlier in the day and replayed on stream; that was not said.
- Image: dashboard panel only; the full frame shows a worktree path with a personal name.
- Why it matters: the hardest .NET migration (Web Forms) gets an agent that plans, commits per step, and drives to a green build.
- Source: 16:06-16:21 ET, transcripts 20261111-160603 to 20261111-162000; crop of shot 20261111/160738; closing slide via stream agent crop 20261111-upgrade-agent.
-->

---
layout: "session"
num: 7
time: "Day 2 · 7:03 PM"
speakers: "Bruno Capuano"
---

# .NET + Foundry: Better Together

<!--
- [Session 07 · Day 2] Bruno Capuano. Started about 7:03 PM ET.
- Source: dotnetconf.net/agenda (7:00 PM ET); stream agent session marker.
-->

---
layout: "shot"
image: "/shots/day2/190450.jpg"
time: "Day 2 · 19:04"
---

# Foundry from .NET: three paths, from a model call to a hosted agent

<!--
- Say: There are three ways to use Foundry from .NET: call a model with IChatClient, run your own AIAgent with Foundry models and tools, or call an agent that Foundry hosts. You do not have to move your agent runtime into Foundry.
- On screen, "Foundry supports three .NET paths / Model calls, app-owned agents and service-managed agents": Direct model call: IChatClient → Foundry model deployment. App-owned agent: AIAgent in your process → Foundry model deployment + tools. Service-managed agent: .NET client → Foundry prompt or hosted agent. "Your code can call Foundry services without moving the agent runtime into Foundry."
- Bruno (19:04): the foundation is "Microsoft Extensions for AI that allows us to interact with embeddings or with chat clients or do data ingestion"; "frameworks like the Microsoft Agent Framework to build and create agents"; "the MCP C# SDK". Foundry helps when "you are super happy with your agent working locally, and then you find, hey, I want to run this ... I want to move to production". A Foundry project (ai.azure.com) gives "deploy models, create agents, apply security, work with tools, and evals".
- Demo 1, path 1 (19:06): one Microsoft.Extensions.AI code path asks "the same question to different models" in the Foundry catalog ("Mistral, we have Anthropic, OpenAI") and reports tokens and elapsed time. "I am using managed identity, so I don't need to use an API key." On screen: gpt-6-luna, "Elapsed: 12.21 seconds", input 22, output 106, total 128 tokens; then grok-4.7 with the same prompt. Bruno: "GPT-6 Luna is kind of a small and super powerful model."
- Source: 19:04-19:08 ET, transcripts 20261111-190400 and 20261111-190602; shots 20261111/190450 and 190757.
-->

---
layout: "shot"
image: "/shots/day2/190848.jpg"
time: "Day 2 · 19:08"
---

# Same prompt, three Foundry models, one `IChatClient`: compare time and tokens

<!--
- Say: With one Microsoft.Extensions.AI code path you can send the same prompt to several Foundry models and compare speed and token use, then pick per task.
- Results on screen (same prompt): gpt-6-luna 12.21 s, 128 tokens (22 in / 106 out); grok-4.7 70 tokens total (54 out) — Bruno: "This one was faster and it used less tokens"; Kimi-K3.1-Pro 6.15 s, 499 tokens (118 in / 381 out).
- Bruno (19:08): Kimi "is kind of the big guns ... faster, but it used ... around 500 tokens. I use Kimi for planning or for deep reasoning activities". Grok can review other models' answers: "ask Grok, hey, Grok, analyze and give me your opinion". Foundry's monitor shows tokens used per model over time: "There is full traceability".
- One run each; not a benchmark. The Grok elapsed time was not captured.
- Source: 19:06-19:09 ET, transcripts 20261111-190602 and 20261111-190803; shots 20261111/190757 and 190848.
-->

---
layout: "shot"
image: "/shots/day2/191149-crop.jpg"
time: "Day 2 · 19:11"
---

# Foundry prompt agents: model + instructions + tools, versioned

<!--
- Say: A Foundry prompt agent is a model plus instructions, tools, memory and knowledge, configured in the portal. Each change can be saved as a version and one version marked active. Without tools, the agent can't answer "how is the weather in Toronto?"; add web search and it can.
- Bruno (19:10): "in what we call a prompt agent, the first step is to choose the model" (his list: GPT models, Grok, and more); "Then I can define my system instructions. I can work here with my tools ... connect this to a memory, knowledge". "Foundry also gives us the chance to support versions ... we can flag that version as the active one."
- Demo: version 2, GPT-5 mini with "no instructions, no tools" — "just a big LLM answering questions" — for "how is the weather in Toronto?". Then version 3 with the Web search tool (on screen: agent NetConf-01, "Version: 3", Tools: Web search; tabs Playground, Details, Traces, Insights (Preview), Monitor, Evaluation, Optimize; "Continue in code", "Publish").
- Traces (19:12): with web search on, "I can go back here and start to see in the traces"; a trace shows the web search tool call and "the response from the tools came back from the GPT model".
- Memory (19:13): a version "that doesn't have any memory" can't answer "what is my name?"; "the latest version who has connected a memory that I already filled" can.
- Image: cropped (the URL bar showed resource names and IDs).
- Source: 19:10-19:14 ET, transcripts 20261111-191004 and 20261111-191203; crop of shot 20261111/191149.
-->

---
layout: "shot"
image: "/shots/day2/191555.jpg"
time: "Day 2 · 19:15"
---

# From local AIAgent to Foundry hosted agent: a few lines of hosting code

<!--
- Say: Two ways to run agents in Foundry: a prompt agent (configured in the portal) or a hosted agent (your own .NET agent code, packed and deployed). To host an Agent Framework AIAgent, you wrap it in an AgentHost that speaks the Responses protocol.
- Bruno (19:14): "One way is what we've just seen, which is called a prompt agent, and the other way is to create a hosted agent." "We get an AI agent from a deployment name ... I can pack this agent and deploy it to Foundry." You can also call a prompt agent "that is already hosted in Foundry" from .NET.
- On screen: `.AsAIAgent(model: deployment, name: "BetterTogetherHello", instructions: "You are a friendly .NET assistant ...")`; "// Step 3: Replace the console RunAsync call with the Responses ..."; `var builder = AgentHost.CreateBuilder();` `builder.WebApplicationBuilder.AddFoundryResponses(agent);` `builder.RegisterProtocol("responses", endpoints => endpoints.Map...);` `var app = builder.Build(); app.Run();`.
- Memory demo result just before (19:14): the version with memory answered "Your name is Bruno".
- Source: 19:14-19:16 ET, transcript 20261111-191405; shot 20261111/191555.
-->

---
layout: "shot"
image: "/shots/day2/191757.jpg"
time: "Day 2 · 19:17"
---

# `azd ai agent run`: test a hosted agent locally with Agent Inspector

<!--
- Say: Deploy a hosted agent with azd ("azd ai agent init", deploy, provision), described in azure.yaml like a container app. To test locally, `azd ai agent run` starts the agent and opens Agent Inspector, a chat UI with tokens, events, tools and a run timeline.
- Bruno (19:16): "we can do azd ai agent init, and there are AI agent deploy or provision and more." In the azure.yaml ("if you've been working with container apps, you probably know this format") you "choose our platform, which is going to be Linux, AMD64, register a protocol, add a couple of environment variables, and we can deploy this."
- Testing: plain `dotnet run` exposes port 8088, but "I need to create literally kind of a client in another terminal or use Aspire". Instead: "azd ai agent run, which is going to start my agent, host my agents locally, and then also open ... a client interface ... where I am going to be able to chat with my agent."
- On screen: "Agent Inspector — Connected http://localhost:8088 — Responses Protocol"; tabs Overview, Tokens, Events, Tools; "Latency Waterfall", "Run Timeline 1 Run (In progress)". The browser tab is "Foundry Toolkit".
- After deploy (19:18): unlike a prompt agent, in the portal "we can't change in the agent ... not the model, not the tools. That's everything that we code." It ships as "a code asset that is going to be registered here in a container registry", so "we can set up a very nice and clean CI/CD deployment pipeline". And it still gets Foundry traces.
- Source: 19:16-19:20 ET, transcripts 20261111-191602 and 20261111-191804; shot 20261111/191757.
-->

---
layout: "shot"
image: "/shots/day2/192134-crop.jpg"
time: "Day 2 · 19:21"
---

# Guardrails on a code-hosted agent: content safety, jailbreak blocking, network rules

<!--
- Say: Even for a hosted agent whose code is fixed, Foundry lets you assign guardrails in the portal: content safety, jailbreak blocking, and network allow/deny rules. Assigning one creates a new agent version. Bruno (19:23): "remember, this is a hosted agent with my code."
- Demo (19:20): the hosted agent has blog tools that read RSS ("my personal feed, with the DevBlogs teams") to answer "show me the last blog that Bruno writes". Traces have a "conversational view".
- Guardrail: "let's reassign and let's put Microsoft Default guardrail ... There it is. We have a new version."
- On screen, "Assign guardrail": options Guardrails861, EBGuardrail, Microsoft.Default (selected), Microsoft.DefaultV2. Microsoft.Default, Content safety (4): Hate, Self-harm, Sexual, Violence — medium blocking — on user input and output, action Block.
- Jailbreak (19:22): "everything that we have here that is detected as jailbreak is going to be blocked."
- Network rules: "if the agent tries to get to my personal blog or my personal website, I am going to deny that action. And I also ... enable access to Microsoft.com because that's where the .NET blog is." On screen (shot 20261111/192335): "Rules are evaluated in order from top to bottom. The first matching rule applies. If no rules match, the previously chosen default action applies." Rule 1 *brunocapuano.wordpress... Deny; rule 2 *elbruno.com* (deny).
- Before the rules, the agent answered with posts from both the .NET blog and his personal blog.
- Result (19:24): "the agent tried to go to these blocked URLs"; in "one of the latest traces ... We can see here how it was denied a couple of actions". Traces can also go to Azure Monitor.
- Next: evals on agents from the Monitor/Evaluations area; and "Microsoft Decision 1", "a fast model, focus on decisions"; "We are working on the Microsoft Extensions for AI support for this model" (not done yet).
- Image: dialog cropped (the URL bar showed resource names and IDs).
- Source: 19:20-19:26 ET, transcripts 20261111-192004, 20261111-192205, 20261111-192400; crop of shot 20261111/192134; shot 20261111/192335.
-->

---
layout: "shot"
image: "/shots/day2/192835-crop.jpg"
time: "Day 2 · 19:28"
---

# An agent doesn't need an LLM every time. A decision model can route the ticket.

<!--
- Say: A custom .NET agent can use a fast decision model instead of an LLM for a routing step. Bruno's support agent classifies "I was charged twice" as billing, with confidence scores, and still runs hosted in Foundry with traces and guardrails.
- Bruno (19:26): "the agent doesn't need to use an LLM all the time ... If we code the agent, we can use different LLMs, or we can even use a decision model" to route to "billing, technical support, account access, and more." "I override the RunCoreAsync ... I am going to use a decision model here to do my decisions."
- Demo: "I was charged twice to my subscription" → the trace shows "a billing issue, and we have probabilities, confidence, and more." "because we are also in Foundry, we can start to take advantage of Foundry on the traces, on the monitor, guardrails".
- The Foundry agent list on screen mixes Prompt and Hosted agents (e.g. better-together-decisions: Hosted, Running).
- Voice (19:28): one toggle, "Voice mode — Switch to a voice-first experience". He said "I was charged twice for my subscription" aloud; the result: `"team": "billing", "confidence": 0.9979...` (agent episode02-support-routing, version 2, with sections Code asset, Protocols, Guardrail (Preview)). "my agent supports voice". On top of that "we can take advantage of toolboxes, memory, tracings, guardrails, identity."
- Close (19:32): "everything new is one week later came to Foundry, and hey, there it is, ready to use ... and two weeks later, we have an official SDK to use it." His after-show pre-recorded session "Beyond localhost: .NET agents in Foundry" goes "from zero to production".
- Q&A: Foundry Local was covered in a Day 1 session ("yesterday ... 30 minutes"). Bruno (19:30): "we did kind of bring your own model to Foundry Local"; it "manage[s] the download of the model, the hosting of the model, the cache of the model". "next week is going to be bigger. There are a couple of big announcements about Foundry Local" (no details). On new video models: "there are no standards about how to use video models" yet — no JSON standard for input or output.
- (Inference) The decision model is the Microsoft Decision 1 model he introduced just before (MEAI support in progress).
- Source: 19:26-19:31 ET, transcripts 20261111-192605 to 20261111-193200; crop of shot 20261111/192835 (URL bar removed).
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
