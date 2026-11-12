---
theme: default
title: .NET Conf 2026 Recap - Aspire, Azure and data
info: |
  ## .NET Conf 2026 Recap - Aspire, Azure and data
  Kevin Griffin - Microsoft MVP
  Aspire, Azure, EF Core 11: highlights from Day 1 (2026-11-10) and Day 2 (2026-11-11), captured live.
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

- Aspire, Azure and data
- Kevin Griffin
- Microsoft MVP

<!--
- [title]
- Say: This is a .NET Conf 2026 recap on one topic: Aspire, Azure, EF Core 11. It pulls the highlights from Day 1 (2026-11-10) and Day 2 (2026-11-11), captured live from the stream.
- Sessions in this deck:
  - 01 What's New in Aspire for .NET Developers (Day 1, 4:00 PM)
  - 02 How Aspire uses .NET to build an agent-first toolchain for any language (Day 1, 6:00 PM)
  - 03 Azure's new lineup for .NET developers (Part 1) (Day 2, 5:31 PM)
  - 04 Azure's new lineup for .NET developers (Part 2) (Day 2, 6:00 PM)
  - 05 EF Core 11: Vector Search, Smarter LINQ, and a Friendlier dotnet ef (Day 2, 7:33 PM)
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
time: "Day 1 · 4:00 PM"
speakers: "Maddy Montaquila, Damian Edwards"
---

# What's New in Aspire for .NET Developers

<!--
[Session 01 · Day 1]
- Opening (16:02): "The Opus Moment" pushed the team to lean into agents. "Aspire is this deterministic thing that can actually orchestrate your stack under the hood. So you can have all this magic with agents but keep it on guard rails."
- Naming: "not called dotnet aspire, it is just aspire"
-->

---
layout: "shot"
image: "/shots/160528.jpg"
time: "Day 1 · 16:05"
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
time: "Day 1 · 16:06"
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
time: "Day 1 · 16:09"
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
time: "Day 1 · 16:14"
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
time: "Day 1 · 16:19"
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
time: "Day 1 · 16:27"
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
num: 2
time: "Day 1 · 6:00 PM"
speakers: "Maddy Montaquila, Jose Perez Rodriguez"
---

# How Aspire uses .NET to build an agent-first toolchain for any language

<!--
[Session 02 · Day 1] Agenda time 6:00 PM ET; started ~6:01.
- Session 10 already covered Aspire 17; add only new details here.
- Framing (18:02): "a customer study for Aspire as a .NET customer" — why Aspire went polyglot
- The AppHost "CSproj" didn't land with mixed teams: "I have a JavaScript front-end team ... they don't want a CSproj". Even a single-file C# AppHost got "whoa, C# that only runs on Windows"
-->

---
layout: "shot"
image: "/shots/180518.jpg"
time: "Day 1 · 18:05"
---

# Aspire: one C# API, many languages

<!--
- Say: Aspire writes its API once in C#, then generates SDKs for other languages. TypeScript is GA; the .NET host still runs every call.
- First attempt failed on callbacks: "you couldn't generate the C# code from a TypeScript callback"
- Pipeline (stream slide): WE WRITE C# API (extension methods and types marked [AspireExport]) → .NET PROVIDES Roslyn + runtime (reads types and docs) → WE DEFINE the ATS contract ("Aspire type system": capability IDs, type mappings, handle rules) → WE GENERATE guest language SDKs ("TypeScript is GA, more languages in preview") → WE EXECUTE capability calls (the .NET host runs each C# method, called over JSON-RPC)
- Why it matters: TypeScript teams get a native-feeling Aspire SDK, while the logic stays in one C# codebase. (Inference: the same pattern could work for other .NET libraries.)
- "Idiomatic in every language" (18:12–18:13): C# AddRedis → TypeScript addRedis → Python add_redis; typed clients with IntelliSense + LSP. "We want it to be idiomatic." They "work a bunch with the TypeScript team", and do "the same when it comes to Python and Go and Rust". Example of a mismatch: TypeScript has no overloads that "work the same way that overloads work in C#" (/shots/181302.jpg)
- Language roadmap (18:14): "the next language you will see pop up as an option in the CLI is Go. It will be Preview in 17." "Python, Java, and Rust are available behind feature flags." "We've shipped two new app host languages in a year"
- Source: 18:04–18:06 ET, transcript 20261110-180403, /shots/180518.jpg
-->

---
layout: "default"
codeSize: "19"
---

# The same AppHost, in TypeScript

```ts
import { createBuilder } from './.aspire/modules/aspire.mjs';

const builder = await createBuilder();
await builder.addRedis("cache");

const worker = await builder.addExecutable("worker", "node", "../worker", ["worker.mjs"]);

await worker.withEnvironmentCallback(async (context) => {
  const environment = await context.environment();
  await environment.set("DEMO_MESSAGE", "Hello from the shared Aspire engine");
});
```

<!--
- Say: For teams that say "I don't want to install .NET, I'm a TypeScript dev", the AppHost can be TypeScript — and .NET calls back into the TS callback.
- Demo file apphost.mts (18:08–18:10); code simplified from /shots/180920.jpg (console.log lines removed, the joined string inlined; the stream builds it with ["Hello","from","the","shared","Aspire","engine"].join(" "))
- Callback round trip: .NET calls the TS function, TS asks .NET for the environment, sets DEMO_MESSAGE, .NET acknowledges — over the JSON-RPC bridge from the previous slide
- Also new: an Aspire tray app ("you probably noticed this tray icon ... the Aspire tray app, which you can run now")
- Under the hood (18:10): the TS `addRedis` "is all generated code" — "it's basically doing RPC, local RPC" into "what we call the app host server". Live log on stream: addRedis completed in 43ms; .NET called the TS callback; TS asked .NET to set DEMO_MESSAGE ("completed in 1ms"); the whole callback round trip ~0.039 s
- "Shipping in a week": Aspire 17
- And no .NET install needed (18:18): "the latest few Aspire releases, you don't have to install .NET at all if you don't want to" — see the "Aspire no longer needs .NET installed" slide
- Why it matters: mixed .NET/JS teams can share one Aspire setup, each in their own language.
- Source: 18:08–18:12 ET, transcripts 20261110-180800, 20261110-181004, /shots/180920.jpg
-->

---
layout: "shot"
image: "/shots/181759.jpg"
time: "Day 1 · 18:17"
---

# Blazor Server on Native AOT: Aspire dashboard 3x faster, 40% smaller

<!--
- Say: The Aspire dashboard is Blazor Server — and with a custom build made with the Blazor team, it now runs as Native AOT.
- Startup: Native AOT 491 ms vs JIT + .NET runtime 1,429 ms. Deployment size incl. runtime: 110 MB vs 183 MB (stream slide)
- "Custom Blazor build — built with the Blazor team to prove Blazor Server can compile with Native AOT"; source-generated JSON so trimming doesn't remove types reflection needs
- Also: the dashboard moved to Fluent UI v5 with agents; James Newton-King "was saying it would be months of work without agents"
- More: devblogs.microsoft.com/aspire/aspire-dashboard-native-aot (on the stream slide)
- Why it matters: a real Blazor Server app shipping as Native AOT — the stream slide calls it proof that "Blazor Server can compile with Native AOT".
- Source: 18:16–18:18 ET, transcript 20261110-181604, /shots/181759.jpg
-->

---
layout: "statement"
---

Aspire no longer needs .NET installed.

<!--
- Say: Recent Aspire releases ship as a self-contained bundle, so you don't need a .NET install to use them — even though Aspire is built on .NET.
- 18:18: "for a while, even though the app host was TypeScript, you still kind of had to install .NET." Now: "the latest few Aspire releases, you don't have to install .NET at all if you don't want to"
- "Now you can tell your friends to install Aspire, whoever is still anti-.NET."
- Why: Aspire "used to run on your .NET install itself"; "we were stuck on .NET 8 for a long time because we knew some of you might still be running .NET 8", and "the back compat was just getting kind of unmaintainable". So they created "what we called the bundle".
- What's in the bundle (18:22): DCP (a Go app, "always been actually a native ... executable"), the dashboard, the AppHost server (described as "of course also native AOT" — but see the correction below), the tray app, and the terminal host. Carrying these in the bundle is how "we can get rid of the Aspire SDK now"
- CORRECTION on stream (18:28, David Fowler cameo): "I think the only thing left is the app host server itself ... It's just opt-in in Aspire 17." So the Native AOT AppHost server is opt-in in Aspire 17, not the default. "You only got one half a thing wrong."
- Demo (18:24): `aspire new` with the TypeScript starter (Node.js app + Vite frontend) runs in the dashboard on a machine where running `dotnet` shows ".NET is not installed" (/shots/182550.jpg)
- Install: get.aspire.dev (or the download icon on aspire.dev) — Brew, WinGet, Nix, Mise, NuGet, npm, or the scripts
- Why it matters: Aspire's .NET version is no longer tied to what's installed on your machine.
- Source: 18:18–18:26 ET, transcripts 20261110-181804, 20261110-182203, 20261110-182400, /shots/182550.jpg
-->

---
layout: "statement"
---

Aspire is a .NET customer: Roslyn, Blazor, Native AOT.

<!--
- Say: Aspire runs any language, but it's built on .NET: Roslyn for cross-language contracts, Blazor for the live dashboard, Native AOT to ship it.
- Stream slide (18:26) "Aspire is a .NET customer — And we love it!!!": 01 Compiler infrastructure for cross-language contracts; 02 Application framework for live experiences; 03 Native compilation for distribution (/shots/182657.jpg)
- "Aspire is a .NET customer because it's the best."
- "The best language will always be the best language for Aspire" — "what he meant was, the best language on Earth, C#, obviously, is the best language for building Aspire."
- Links: aspire.dev, aka.ms/aspire-discord
- Why it matters: Roslyn, Blazor, and Native AOT doing real work inside a cross-language tool.
- Source: 18:26–18:28 ET, transcript 20261110-182602, /shots/182657.jpg
-->

---
layout: "session"
num: 3
time: "Day 2 · 5:31 PM"
speakers: "Matt Soucoup, Paul Yuknewicz"
---

# Azure's new lineup for .NET developers (Part 1)

<!--
- [Session 03 · Day 2] Matt Soucoup and Paul Yuknewicz. Part 1 of 2; Part 2 follows at 6:00 PM ET.
- Source: dotnetconf.net/agenda (5:30 PM ET); stream agent session marker 5:31 PM ET.
-->

---
layout: "shot"
image: "/shots/day2/173214.jpg"
time: "Day 2 · 17:32"
---

# Azure's cast: ACA Sandboxes, hosted skills, AI Gateway, SRE Agent

<!--
- Say: Part 1 of the Azure session is all demos of four services: Azure Container Apps Sandboxes for running risky code in a microVM, hosted skills, AI Gateway, and SRE Agent.
- On screen, "Meet the cast": ACA Sandboxes ("The stunt double. Takes the risky code, in an isolated microVM."); Hosted skills ("The specialist. Event-driven AI skills, defined in an .agent.md file."); AI Gateway ("The producer. Keeps tabs on every model and tool your app calls."); SRE Agent ("The one who answers the pager at 2 AM: triage, root cause, fix."). "Co-starring: Copilot canvases put Azure in your development workflow. Shot live on stream".
- Opening (17:32): "We have no slides, we have all demos today." SRE Agent only "if we have the time".
- ACA Sandboxes: "Think micro VMs. This is for production workloads, and you want them to run really fast, like sub-second, spin-up, but also have that Hyper-V-like protections." "It's not the little kid version of sandbox."
- Source: 17:32-17:33 ET, transcript 20261111-173204; shot 20261111/173214.
-->

---
layout: "statement"
---

The agent is the brain. Tools are the hands. Sandbox the tool, not the agent.

<!--
- Say: The ACA Sandboxes demo's main idea: an agent that reads untrusted documents is risky, so run the dangerous tool in an isolated sandbox.
- Demo setup (17:34): an agent analyzes a loan document, which has "PII, banking kind of stuff". Two risks: "getting harmed by the data, and the second is like exfil or exfiltrating, sending away my goodies."
- Speaker (17:35; (Inference) Paul Yuknewicz, the demo repo is his): "think of your agent as the brain ... the brain wants what it wants, and then we decide what the hands let the agent reach out and do." "A lot of people are like, oh, I'm going to sandbox the agent. I'm actually going to sandbox the tool. So the tool is dangerous. The tool is the hand".
- Also: "not everything has to be agents ... Agents are a little bit more dangerous, honestly."
- Sample: github.com/paulyuk/aca-sandboxes-dotnet-demo (README on screen: .NET 10 SDK, Azure CLI, Copilot CLI; model calls go through an Azure AI Gateway connection). Screenshot not used: it shows the presenter's browser bookmarks.
- How it works (Q&A, 18:26): ACA Sandboxes run on a compute substrate "called Legion ... a dispensary of VMs and micro VMs ... that it can serve sub-second to you and do the last mile of slamming your particular container image, but also your memory in your disk" — "more like a VM that it can resume with state". Uses: running "an untrusted piece of code", and document processing; "great for agents and for apps." Limits (18:28): "it's Linux only"; default disk images ("what's loaded as software by default") plus your own disks; "a number of compute sizes you can choose from".
- Live run (17:36): `dotnet restore` and run, then the tool starts "a sandbox group". "We, by the way, have great SDKs for the sandboxes, including for .NET." The speaker called the spin-up "super fast"; no time was measured on stream (sub-second is the general product claim from 17:33).
- Redaction (17:37): "part of what the tool did is it redacted the data. I don't want the model having social security numbers." On screen: `redactions: {paymentCard:0, email:1, ssn:1, phone:1}`, "Contact details and SSN were redacted", "verdict":"approved".
- Security run (17:38, `dotnet run -- security`): a document with injected instructions came back `"verdict":"rejected","reason":"untrusted-instructions"`. An egress probe to example.com got HTTP 403: "the sandbox infrastructure itself is already configured by default to reject all egress." You can allow "one and only one place you're allowed to talk to", "but it starts kind of secure by default". The sandbox log shows `"egress":"Deny"` and no host credentials inside the sandbox.
- Identity run (17:40, `dotnet run -- identity`): with the sandbox group's managed identity off, the token call got HTTP 401, tokenIssued false; with it on, HTTP 200, tokenIssued true, value shown as [REDACTED]; in both, host credentials present = 0. Speaker: the identity headers and endpoint "are present", but "the credential is actually not present ... you can't even get into trouble if you wanted to". Turning it on is "a config knob".
- On-screen sandbox start times in these runs: elapsedMs 1836, 888, 1863, 1082, 935 (demo runs; not a benchmark). So roughly 0.9-1.9 s here.
- Screenshots not used: they show the presenter's browser bookmarks and terminal prompt.
- Source: 17:34-17:41 ET, transcripts 20261111-173404 to 20261111-174004; shots 20261111/173544, 173859, 174029 (not in deck).
-->

---
layout: "statement"
---

"Container apps used to be known as slow. It's not." 100 sandboxes, bursts of 10, live.

<!--
- Say: To show scale, they started 5 .NET 10 microVM sandboxes at once, then 100 in bursts of 10, live on stream, and deleted them after.
- Speaker (17:42): "So it made five .NET 10 micro VMs, just like that, sub-second, and then it already deleted them, too." "container apps used to be known as slow ... That's not slow." "we're building a lot of our major workloads on this". Then: "let's do 100 in bursts of 10 ... We can actually do this all day long ... we want you to do this."
- What the screen showed (be precise): the 5-sandbox run (`dotnet run -- scale 5 5`) logged per-sandbox elapsedMs of 1532-2027 and a summary of 5 requested, 5 verified, 0 failed in 2832 ms total. In the 100-in-10s run (`scale 100 10`) most visible entries were about 850-970 ms (one was 2753 ms). Final summary (shot 20261111/174408): `"requested":100,"runningDotnetVerified":100,"failed":0,"elapsedMs":17802`, about 5.6 verified per second; then all deleted. So: 100 for 100, zero failures, about 18 seconds.
- After (17:44): the sample "is using our beloved Agent Framework"; the sandboxed tool is "boring code ... that can't do scary stuff", which is the point.
- Screenshots not used: they show the presenter's terminal prompt and bookmarks.
- Why it matters: (Inference) isolated microVMs start fast enough to use one per risky agent tool call. No cost numbers were given.
- Source: 17:42-17:45 ET, transcripts 20261111-174204 and 20261111-174403; shots 20261111/174249, 174349, 174408 (not in deck).
-->

---
layout: "statement"
---

LLMs take the soft, squishy input. Deterministic code enforces the hard rules.

<!--
- Say: The design rule behind the sandbox demo: let the model handle the messy input, then hand it to plain, deterministic code where you write the hard rules.
- Speaker (17:45; (Inference) Paul Yuknewicz): "the agents, the LLM stuff, is what I like to think of as the soft, squishy stuff. It takes your inputs, the soft stuff that is hard to handle in deterministic code ... it turns it over to your deterministic code, which is good at handling what makes it deterministic, and then we can write our hard rules against it." Earlier: "boring code that can't do scary stuff ... paired with deterministic safe code, that is the key."
- Next (17:46): Matt Soucoup switched to the GitHub Copilot app and opened "the Azure Functions Hosted Skills Canvas" to build "an Azure Function Hosted Skill" (Functions as "an event-driven programming model"). Details on the next slide.
- Source: 17:44-17:47 ET, transcripts 20261111-174403 and 20261111-174603.
-->

---
layout: "shot"
image: "/shots/day2/174643-clean.jpg"
time: "Day 2 · 17:46"
---

# Azure Functions Hosted Skills: AI skills as `.agent.md` in a Function App (concept)

<!--
- Say: Hosted Skills put AI skills, defined in .agent.md files, inside an Azure Function App, so they run on Functions triggers. Matt demoed it from a canvas in the GitHub Copilot app. The canvas is labeled "INITIAL CONCEPT".
- On screen (Azure Functions Hosted Skills canvas): "Build and run Hosted Skills in a local Function App, or select an existing Azure Function App to invoke remotely." "Open an existing local Function App only when it contains host.json and at least one valid .agent.md Hosted Skill". Model endpoint: existing gpt-6-sol. Buttons: Open in VS Code, Refresh, Stop local function, Deploy to Azure. TRIGGER: Timer, HTTP, Queue; Blob, Connector, Cosmos DB marked "NYI" (not yet implemented). Badges: "INITIAL CONCEPT", Target: Local, Trigger: HTTP.
- Matt (17:46): "this is the Azure Functions Hosted Skills Canvas ... we're going to build an Azure Function Hosted Skill." Functions is "an event-driven programming model".
- What a hosted skill is, Matt (17:48): it "adds that squishy, squishy layer" to an event-driven function: "what we can do now is not have to write any code to it, but rather we can just kind of give it a LLM prompt. So that's what a hosted skill is."
- The canvas: "Paul, you made this canvas, I believe, and it's really, really good for testing and debugging. It's going through the Azure Function hosted skills lifecycle as you develop. So you don't have to leave your GitHub Copilot app". Paul: "It's literally my daily driver ... Canvases are worth the price of admission to the Copilot app."
- Status: initial concept; say so. Blob/Connector/Cosmos triggers are not implemented yet.
- Image: a copy of frame 174643 with a local user path blanked out by the stream agent; nothing else changed.
- Source: 17:46-17:49 ET, transcripts 20261111-174603 and 20261111-174800; frame 20261111/174643 (cleaned copy).
-->

---
layout: "shot"
image: "/shots/day2/175029.jpg"
time: "Day 2 · 17:50"
---

# A hosted skill is a `.agent.md` file: front matter = trigger, body = English

<!--
- Say: A hosted skill is just a markdown file. The front matter names it and sets the trigger and route; the body is a plain-English prompt. Several .agent.md files give you several routes in one Function App.
- On screen (damage-check/hello-world.agent.md): front matter `name: Package damage check hello world`, `description: simple hello world`, `trigger: type: http_trigger, args: route: hello-world`; body: "say hello Paul 👋". The project also has abstract-check.agent.md, damage-check.agent.md, host.json, mcp.json, and a function_app.py (so this sample's host project is Python).
- Matt (17:50): "it's just a name.agent.md file ... We're going to say it's an HTTP trigger. We're going to give it a route. And then our prompt." Paul: "that top metadata, front matter stuff, that's the trigger?" "And below is just English." "you can have multiples in the same one to find multiple routes".
- Run (17:52): the HTTP call returned "Hello, Paul". Then he changed the prompt in the canvas to "tell me the current weather in Redmond" and ran it again.
- Tools: "mcp.json, put this into your function. It's just ... you're defining it the same way you would do it in a Copilot or whatever else. It's that same JSON file you see everywhere". With that, "now we have tools involved".
- Status: initial concept (canvas label).
- Source: 17:50-17:54 ET, transcripts 20261111-175004 and 20261111-175204; shot 20261111/175029.
-->

---
layout: "shot"
image: "/shots/day2/175449.jpg"
time: "Day 2 · 17:54"
---

# The skill's "hands": a C# MCP tool the model can call

<!--
- Say: The prompt is the brain; the hands are trusted C# code exposed as an MCP tool. Here an `analyze_photo` tool reads a package photo from Blob storage and asks a vision model for a damage verdict.
- On screen (src/PackageTools/PhotoInspectionTool.cs): `[McpServerToolType] public sealed class PhotoInspectionTool(PhotoAnalysisService analysis, ILogger<PhotoInspectionTool> logger)`; `[McpServerTool(Name = "analyze_photo")]` with `[Description("Read one JPEG or PNG package photo from the package-photos Blob container and ask the vision model to ...")]`; `Task<PhotoVerdict> AnalyzePhotoAsync(string blobName, string inspectionInstructions, CancellationToken ...)`; parameter description: "The inspection rules from the hosted skill's Markdown". On timeout it throws `McpException("Photo analysis timed out. No damage verdict is available.")`.
- Speaker (17:54): "These are my hands, essentially." "we're giving the tool name, we're giving it a description, so the model can say, oh, I think I might need this ... your hands do it". "these are our hands essentially that's well written, we trust it." It is handed to the function "because it's an MCP server now".
- (Inference) The [McpServerTool] attributes are from the MCP C# SDK (Day 2 session, in the AI and agents deck).
- Source: 17:54-17:55 ET, transcript 20261111-175404; shot 20261111/175449.
-->

---
layout: "code"
---

# The whole skill is this prompt. "Never guess a verdict."

```text
You check delivery photos for package damage.
The request has a `photo` field. It is the name of a photo in Blob Storage.
1. Call `analyze_photo` with the photo name and these instructions:
   > Look at the package in the photo. Dents, tears, or crushed corners
   > mean `damaged`. An intact box means `not_damaged`. Tape seams and
   > shadows are not damage. Give one short sentence about what you see.
2. Call `send_result` with the photo name, the verdict, and the reason.
3. Reply with the photo name, the verdict, and the reason.
If `analyze_photo` fails, call `send_result` with the verdict `error` and
say what went wrong. Never guess a verdict.
```

<!--
- Say: The whole damage-check skill is this English prompt in damage-check.agent.md. It calls the C# analyze_photo tool, then send_result. Result: photo-01 not damaged, photo-02 "damaged. The box has a torn, crushed corner."
- Prompt text is from the canvas "SKILL INSTRUCTIONS" (Package damage check · damage-check.agent.md), stream agent crop 20261111-hosted-skill-damage-check (escape characters in the original removed here).
- Result on the canvas, "Agent digest · Manual http · Local function": "photo-02.jpg — damaged. The box has a torn, crushed corner."
- Matt (17:57): "Photo 1, not damaged, must have been delivered to Paul. And if we go to the one that got delivered to me, Photo 02, invoke the trigger ... it is damaged".
- Looser version (17:58; (Inference) likely abstract-check.agent.md from the file list): "now we're going to start relying on the metadata that the MCP" tools expose, and ask for "result, response, and photo in JSON. So we're really loosening it up." Paul: "how would I have known this kind of interesting long tail of cases would come in." "that's exactly the squishy part that I was talking about."
- Closing advice (18:24): "you got to add value beyond what the AI gives you ... Don't let the AI replace you. We still have a job there".
- Wrap (18:00): "a skill should contextualize and orchestrate other tools. It's not good when it's just a recipe ... let's wing it and let's build a server that does all these things. It's going to get it wrong. It's going to take forever. It's going to be expensive." Instead: "you're hosting in the cloud as an MCP, others can call it ... you're making little building blocks". "We can take our existing code and kind of supercharge it in the agentic world". The photo tool sends the blob to Azure (AI) Foundry for the vision analysis.
- Next in the session: Durable Functions.
- Why it matters: the rules live in plain English; the trusted actions live in C# tools; and the prompt tells the model to report an error instead of guessing.
- Source: 17:56-18:01 ET, transcripts 20261111-175602, 20261111-175804, 20261111-180000; canvas text from the stream agent's crop of the frame (path removed).
-->

---
layout: "session"
num: 4
time: "Day 2 · 6:00 PM"
speakers: "Matt Soucoup, Paul Yuknewicz"
---

# Azure's new lineup for .NET developers (Part 2)

<!--
- [Session 04 · Day 2] Same speakers; the stream ran straight on from Part 1 with no break or announcement. This divider sits at the agenda time (6:00 PM ET), just before the Durable Task Scheduler part.
- Part 2 topics so far: Durable Task Scheduler running a hosted-skill plan, the claims desk result, and AI Gateway.
- Source: dotnetconf.net/agenda (6:00 PM ET); no "Part 2" marker in transcripts 20261111-175804 to 20261111-181005.
-->

---
layout: "shot"
image: "/shots/day2/180251.jpg"
time: "Day 2 · 18:02"
---

# AI writes the plan once; Durable Task Scheduler runs it durably

<!--
- Say: For a batch, the AI reads the Markdown skill once and writes a plan; the Durable Task Scheduler (DTS) then runs that plan, retrying failed steps and resuming after a restart. Here: 20 photos, 10 at a time, each routed by verdict.
- On screen, "How DTS Runs the Image Batch": POST /api/batch-check → "AI reads the Markdown skill / Writes the plan once" → "Durable Task Scheduler (DTS) / Runs the plan durably" ("Retries failed steps • Resumes after restart") → list_photos (20 images) → analyze_photo × 20, "10 at a time" ("Each photo uses the vision model through the .NET Claims API") → sort_results → damaged → file_claim; ok → tag_photo; unclear → request_retake → write_summary → "Claims desk + DTS dashboard".
- Matt (18:02): "what durable functions are is they're durable"; "DTS, the Durable Task Scheduler, is going to come through and say, all right, we're going to take all these photos and then make a plan off of them." "That's the durable part."
- How you turn it on (18:05, batch-check/batch-check.agent.md, shot 20261111/180542): front matter `name: Package batch check`, `trigger: type: http_trigger, args: route: batch-check`, plus `workflows: enabled: true`. Matt: "It's an HTTP trigger, but we're going to say you're using workflows now." The body has "## Inspection rules" (adds holes, water stains; `unclear` for blurry, dark or partly visible) and "## Routes".
- Claims API (18:04): "what we have in the claims API is .NET again"; tag → tags the blob; adjuster notices → "I think that probably ... updates the queue ... Azure storage queue, and also updates the database" (his hedge). "I love the minimal ASP.NET".
- Live run (18:06): 20 photos in the local blob store (Azurite); the DTS dashboard waits for the orchestration. Some live setup trouble; one speaker joked, "This is a failed usability study."
- Why it matters: the model plans; the durable engine executes with retries and restarts, so a long agent job does not start over when something fails.
- Status: (Inference) part of the same "initial concept" hosted-skills sample (the diagram is in its assets folder).
- Q&A (18:24), "any news on durable functions for long running or multi-step tool calls?": "if you like Agent Framework ... there's a durable integration built in with that. I believe it just went GA." "durable is always very good at long running. You could even wait literally forever ... because it's journaling what happens." (He hedged on GA: "I believe".)
- Source: 18:02-18:06 ET, transcripts 20261111-180201 and 20261111-180402; shots 20261111/180251 and 180542.
-->

---
layout: "shot"
image: "/shots/day2/180829.jpg"
time: "Day 2 · 18:08"
---

# 20 photos → 6 claims filed, 9 tagged OK, 5 retakes requested

<!--
- Say: The durable batch finished: 20 delivery photos analyzed 10 at a time, then routed: 6 damaged → claims filed and adjuster notified, 9 tagged OK, 5 sent back for a retake (blurry, dark, or partly visible).
- On screen (Claims desk, a local web page at localhost:5180): "Claims filed 6" (CLM-1001..., each "tagged" + "adjuster"), "Tagged ok 9", "Retake requested 5" (the blurry and dark photos).
- Matt (18:08): "it has doing 10 at a time, doing 10 more at a time, got the results back, and then it's finally a claim for the bad ones. And then notifies the adjuster, tags the damage evidence." "These tags weren't there before, they're there now."
- DTS hosting: "You can use it with AKS. You can use it with a web app." (not only Functions).
- Why it matters: an agentic batch job with real side effects (claims, tags, notices), planned by the model and executed by a durable engine.
- Source: 18:08-18:09 ET, transcript 20261111-180804; shot 20261111/180829.
-->

---
layout: "shot"
image: "/shots/day2/181105-crop.jpg"
time: "Day 2 · 18:11"
---

# The pattern: agent loop + sandboxed tools + AI Gateway for models and MCP

<!--
- Say: The full pattern from Part 1: triggers start an agent; the agent calls models through AI Gateway and sends risky tool calls to ACA Sandboxes. The gateway governs models and MCP tools in one place.
- On screen, "Sandbox & AI Gateway Pattern: Tool Isolation" (README of github.com/paulyuk/aca-sandboxes-dotnet-demo): Triggers (HTTP REST, Timer, Connectors events) → "Interchangeable agent host" (FHA / ACA / App Service / Functions) with an agent control loop ("Call models through gateway · Dispatch tools to isolation · Check results; continue or stop"). Tool isolation: ACA Sandboxes ("Ephemeral microVM · egress-default: Deny", create → exec → delete), "Default deny · explicit egress policy", "Check result contract + policy". Shared model and tool access: AI Gateway (Model Routing, MCP, Policies, Enforcement) → Remote model. "Host choice is independent of tool isolation."
- Speaker (18:11; (Inference) Paul, whose sample it is): "this sample also is going to use AI Gateway so that I can govern my models and my tools the same way". With many agents and teams: "capacity ... token budgets ... safety ... I don't want every team kind of figuring that out on their own." And teams "can't possibly know the noisy neighbors".
- Also mentioned (18:09): a colleague, Nick Greenfield, uses a hosted skill for dead-letter handling: messages "we just don't know how to handle ... throw that at the hosted skill, and it can start to classify".
- Image: diagram cropped from the browser (bookmarks bar removed).
- Source: 18:09-18:12 ET, transcripts 20261111-180804 and 20261111-181005; crop of shot 20261111/181105.
-->

---
layout: "shot"
image: "/shots/day2/181321-crop.jpg"
time: "Day 2 · 18:13"
---

# AI Gateway: one endpoint, model aliases, budgets and policies without redeploys

<!--
- Say: Put an AI Gateway between your apps and your models and tools. Apps call one endpoint and an alias like gpt-latest; the gateway routes to models (with fallback) and applies budgets and safety policies, with no app redeploys.
- On screen (AI Gateway portal, aigw-quickstart-12421): alias `gpt-latest`, "GPT-6.1 Sol primary; mini fallback." Backend models: GPT-6.1 Sol (Foundry Sol, priority 0, weight 100) and gpt-5.4-mini (Foundry, priority 1, weight 100). Left menu: Models, MCP servers, Policies, Monitoring, Access, Managed identities, Networking.
- Paul (18:12): a gateway is "like an alias. You put an alias in between your model and your tools. And now, just by doing that, I can turn on features. I can turn on token budgets. I can turn on monetary budgets. I can turn on safety policies ... And I'll never redeploy my back ends or my front ends to do it." "It's just an endpoint. It's a well-known HTTP endpoint ... It's like DNS". "I'm going to lead with the highest priority to give people 6.1 Sol ... if we run out, I've got a backup." "this is model routing ... models from multiple vendors". Developers "are just thinking about that endpoint and that alias".
- Image: cropped; the browser URL bar showed a subscription ID and bookmarks.
- Source: 18:12-18:14 ET, transcript 20261111-181201; crop of shot 20261111/181321.
-->

---
layout: "shot"
image: "/shots/day2/181401-policies-crop.jpg"
time: "Day 2 · 18:14"
---

# Gateway policies per caller: cost caps, token limits, content safety

<!--
- Say: Policies apply per caller identity, not to the whole pool: a monthly cost cap, token-per-minute limits, and content-safety filtering on models and even on an MCP server.
- On screen, "Policies / Manage policies for models, tools, and agents": Balanced filtering (Content safety, scope Gateway); Balanced filtering (Content safety, Models GPT-6.1 Sol and gpt-5.4-mini, MCP server "GitHub repository digest"); "$10.00 / month per caller identity" (Cost limit, both models); "10,000 tokens / minute per caller identity" (Token rate limit, Gateway); "200,000 tokens / minute per caller identity" (Token rate limit, both models).
- Paul (18:14): "it's not just a budget of like the whole pool. It's a budget for each client ... I can reallocate later." How the gateway knows the client: "We do it in an identity-based way ... a managed identity, an agent identity", or "you could do it with keys ... between your agent and the gateway". "those are at least two ways".
- Agent hooks (18:16): "there's agent hooks ... pre and post hooks, and you would call Azure Functions with those." "People even use it for telemetry ... but guardrails, that's the number one ... That's kind of how you run guardrails outside of the reach of the agent." Routing changes: "you're not redeploying your agents. They're just getting that experience at runtime."
- Image: the stream agent's crop of the portal (no URL bar).
- Source: 18:14-18:17 ET, transcripts 20261111-181401 and 20261111-181603; cropped portal frame.
-->

---
layout: "shot"
image: "/shots/day2/181954.jpg"
time: "Day 2 · 18:19"
---

# Azure SRE Agent: do something reliable at 2 AM, before you join the bridge

<!--
- Say: Azure SRE Agent handles incidents for you. Paul's team built it (around 2024) to cut their own ops hours. The goal: at 2 AM it does something reliable, so by the time you join the bridge it has added value or even mitigated the issue.
- Paul (18:18): "we're spending way too many hours ... we set out to build an SRE agent. I think that was about 2024." "the point of a great SRE agent, I think, is it's going to, at 2 a.m., do something reliable that you trust ... by the time you get in front of your incident or you get on a bridge, it will have added value, maybe even mitigated an issue." Safety: "if this has access to the control plane of Azure, it can be turning things off, it can reconfigure, it can mess with data. So you have to really be thoughtful."
- Canvas in the GitHub Copilot app (he built it): "the chat is where I'm doing dynamic things, but the canvas is where I'm doing more deterministic things ... It's like it's an app." On canvases in general (18:29): they cover "specific portions of Azure, so you're just not overwhelming"; "we can try things in the dev tooling ... and then when you tell us you love it, then it can kind of elevate to a portal also." A canvas runs as "you in your local context and has access to everything your agent has". You can build your own: "we actually have a canvas toolkit that ships with it" (18:30).
- On screen (Azure SRE Agent / demo1-dt-snow): tabs Threads, Approvals, Connectors, Incidents, Automation; Operations Hub, Live Reports, Releases, S360 marked NYI. Incidents: Active 0, Mitigated 3; agent status: Pending user input 2, In progress 0, Completed 21; "23 of 23 incidents loaded". Example: INC0007001 "Employee payroll application server is down" (priority 1, new, pending).
- How it works (18:20): "It's literally hooked up to ServiceNow. And there's like PagerDuty". An alert becomes an incident; the agent picks "workflows or plans or runbooks"; "is it the app or is it the infrastructure?" If infra can fix it quickly ("a little bit more capacity"), "it can do those mitigations very fast, and then in parallel ... start ... diagnosing the problem."
- "we use this ourselves inside of Azure." Advice: check "what did it query to come to that triage decision? And it's good to look at those queries and second guess the agent ... that's how you kind of get your learning loop."
- Transparency (18:22): "I can actually see the runbook that it went through, and I can see the actual Kusto queries that it ran". "it runs its own Kusto queries. You don't have to touch a Kusto query."
- Scale: "you're using this today for real work production. For literally hundreds of thousands of incidents." "We used it ourselves before we productized it." (Recap said by the other speaker, (Inference) Matt, and confirmed.)
- Source: 18:18-18:23 ET, transcripts 20261111-181804, 20261111-182000, 20261111-182201; shot 20261111/181954. Frame 182221 not used (it shows a subscription ID).
-->

---
layout: "session"
num: 5
time: "Day 2 · 7:33 PM"
speakers: "Jiri Cincura"
---

# EF Core 11: Vector Search, Smarter LINQ, and a Friendlier dotnet ef

<!--
- [Session 05 · Day 2] Jiri Cincura. The last Day 2 session; started about 7:33 PM ET.
- Source: dotnetconf.net/agenda (7:30 PM ET); stream agent session marker.
-->

---
layout: "shot"
image: "/shots/day2/193526.jpg"
time: "Day 2 · 19:35"
---

# EF Core 11: vector search with DiskANN, full-text search, smarter SQL

<!--
- Say: EF Core 11 ships with .NET 11 (and targets .NET 11). The focus was vector search, AI and search in general, plus the usual LINQ-to-SQL improvements for faster, lighter queries.
- Jiri (19:34): "EF Core 11 ships with .NET 11 as expected, and also targets .NET 11. The main areas of focus for us were obviously vector search, AI, and search in general." Also "improved the LINQ translation and SQL translations to hopefully provide better queries that will be faster and less resource hungry", plus runtime, migrations, tooling and modeling, and "a lot of community contributions".
- Vector search: "able to do searches in databases that do support vector search, both the kind of brute force and also the indexed usage, which is usually using something like DiskANN."
- On screen, "LINQ and SQL improvements": vector search and DiskANN; full-text search; translation for FullJoin, MaxBy, MinBy, List<T>.Exists; unnecessary joins pruned; EF.Functions.JsonContains; simpler CASE; SqlVector properties not loaded by default; ValueTuple/Tuple member access through constructor-bound projections; GroupBy aggregates over reference navigations lifted into a single join; "And a lot more...".
- Source: 19:34-19:36 ET, transcript 20261111-193401; shot 20261111/193526.
-->

---
layout: "code"
---

# EF Core 11 vector search in LINQ: exact, approximate (index), and hybrid

```csharp
var question = new SqlVector<float>(new float[] { 0.12f, -0.40f, 0.91f });

// Exact (kNN): checks every distance
db.Posts.VectorSearch(p => p.Embedding, question, "cosine")
    .OrderBy(r => r.Distance).Take(5);

// Approximate (ANN): uses the vector index (e.g. DiskANN)
db.Posts.VectorSearch(p => p.Embedding, question, "cosine")
    .OrderBy(r => r.Distance).Take(5)
    .WithApproximate();

// Hybrid: vector similarity + normal filters
db.Posts.VectorSearch(p => p.Embedding, question, "cosine")
    .Where(r => r.Value.PublishedOn >= new DateTime(2026, 1, 1))
    .OrderBy(r => r.Distance)
    .Select(r => new { r.Value.Title, r.Distance })
    .Take(5).WithApproximate();
```

<!--
- Say: Vector search is plain LINQ in EF Core 11. VectorSearch gives exact k-nearest-neighbor; add WithApproximate() and the database uses its vector index; and you can combine it with normal Where filters.
- Code is from the demo (VectorSearch.cs, 19:37, shot 20261111/193742); `.ToQueryString()` calls removed for space.
- Jiri (19:36): the Embedding property "is configured as a vector index". Without approximate, it is "checking every single distance, not using the index". "The next one has this special clause with approximate ... And now this will use the index on the database side." Then "what we would call a hybrid search or combined search, where I'm combining my vector search, my similarity search, and filtering on columns ... here I'm filtering on the published on."
- Why it matters: RAG-style similarity search with no hand-written SQL.
- Source: 19:36-19:38 ET, transcript 20261111-193602; shot 20261111/193742.
-->

---
layout: "shot"
image: "/shots/day2/193828.jpg"
time: "Day 2 · 19:38"
---

# Generated SQL: `VECTOR_SEARCH`, and a warning when you forget the index

<!--
- Say: The LINQ becomes SQL Server's VECTOR_SEARCH. With WithApproximate() it adds WITH APPROXIMATE so the index is used. If you leave it off, EF Core 11 warns you that the query is an exact brute-force search.
- On screen (generated SQL): exact = `SELECT TOP(@p1) ... FROM VECTOR_SEARCH(TABLE = [Posts] AS [p], COLUMN = [Embedding], SIMILAR_TO = @p, METRIC = 'cosine') AS [v] ORDER BY [v].[Distance]`; approximate = `SELECT TOP(@p1) WITH APPROXIMATE ...` with the same VECTOR_SEARCH.
- The warning (on screen): "The query uses 'VectorSearch' on property 'Embedding' of entity type 'Post', but 'WithApproximate()' was not specified. The query will perform an exact brute-force search instead of using a vector index. Call 'WithApproximate()' after 'Take()' to use the vector index for better performance." To find the code: `ConfigureWarnings(w => w.Throw(SqlServerEventId.VectorSearchWithoutApproximateIndexWarning))`.
- Jiri (19:38): "It might be what you want, probably not because it's not using an index ... you can make this warning an error or you can hide it in case you know what you are doing."
- Full-text search (next demo): with a full-text catalog and index on Title and Content, the LINQ query is "translated nicely into the calls for the SQL Server. So there's a FREETEXTTABLE, and here is my CONTAINSTABLE". You join "using the key" and order "by the rank". Before, "you definitely could use this ... but it was like a stored procedure or something like that. Now you can do it directly from your LINQ statement."
- Source: 19:38-19:41 ET, transcripts 20261111-193803 and 20261111-194004; shot 20261111/193828.
-->

---
layout: "shot"
image: "/shots/day2/194054.jpg"
time: "Day 2 · 19:40"
---

# .NET's new LINQ operators now translate: `FullJoin` → FULL OUTER JOIN, `MaxBy`, `MinBy`

<!--
- Say: LINQ recently got LeftJoin, RightJoin and FullJoin, plus MaxBy and MinBy. EF Core 11 translates them to SQL, so the same query works in memory and against the database.
- On screen (FullJoin.cs): `db.Invoices.FullJoin(db.Payments, i => i.Reference, p => p.Reference, (i, p) => new { Reference = ..., Invoiced = ..., Paid = ..., Status = i == null ? "Unexpected payment" : p == null ? "Unpaid" : i.Amount == p.Amount ? "OK" : "Amount mismatch" })`, printed as "FullJoin => FULL OUTER JOIN".
- Jiri (19:40): "recently, in last versions, the left join, right join, and now full join were introduced. Also the MaxBy and MinBy functions and a few others. And we do support those now. So if you are using these, for example, LINQ to objects and you want to switch into the database and you want to have the same query, you can". Before, "you need to do a little bit of dance with a bunch of calls".
- Also new: JSON functions on EF.Functions: JsonContains and JsonPathExists.
- Source: 19:40-19:41 ET, transcript 20261111-194004; shot 20261111/194054.
-->

---
layout: "shot"
image: "/shots/day2/194259.jpg"
time: "Day 2 · 19:42"
---

# JSON in SQL Server: `.Contains()` on JSON collections becomes `JSON_CONTAINS`

<!--
- Say: EF Core 11 adds EF.Functions.JsonContains and JsonPathExists, and on SQL Server compatibility level 170 a plain `.Contains()` on a JSON-stored list becomes JSON_CONTAINS instead of expanding the JSON into a table.
- On screen (generated SQL): `WHERE JSON_CONTAINS([p].[Details], 5, N'$.Rating') = 1` (EF.Functions.JsonContains); `WHERE JSON_PATH_EXISTS([p].[Details], N'$.Editor') = 1` (JsonPathExists); and for LINQ `p.Tags.Contains("efcore") && p.CategoryIds.Contains(categoryId)`: `WHERE JSON_CONTAINS([p].[Tags], N'efcore') = 1 AND JSON_CONTAINS([p].[CategoryIds], @categoryId) = 1`.
- Jiri (19:42): "if I set my compatibility level to high enough value, in my case, 170 for the SQL Server, and when I am using these contains calls on my collections that are stored as complex properties or primitive arrays ... [it translates] into this, let's say, better way instead of expanding into a table and filtering in a table". "I just use .Contains and we use the JSON_CONTAINS function on the proper column".
- Source: 19:41-19:43 ET, transcripts 20261111-194004 and 20261111-194204; shot 20261111/194259.
-->

---
layout: "shot"
image: "/shots/day2/194550-crop.jpg"
time: "Day 2 · 19:45"
---

# Join pruning: unused joins are dropped from the SQL

<!--
- Say: If a query has joins but the projection only uses columns from the main table, EF Core 11 removes the joins it doesn't need. In EF Core 10 both joins stayed in the SQL.
- On screen: "Full report: both joins are needed" → `SELECT [o].[Id], [o].[Total], [c].[Name], [c0].[Code] FROM [Orders] AS [o] INNER JOIN [Customers] AS [c] ... LEFT JOIN [Coupons] AS [c0] ...`. "Narrowed: no joins left" → `SELECT [o].[Id], [o].[Total] FROM [Orders] AS [o]`.
- Jiri (19:44): orders, customers and coupons; "when I use just order ... I don't need customer, I don't need coupon ... So it could be removed. In previous EF version, both of those queries ... contain the joins". Before, unused joins meant "the database needs to do extra work for nothing. If you're lucky, the database optimizer will figure it out ... You are relying on the optimizer", and with real-world complexity it may still do the join. In EF Core 11, "we don't need the inner join and left join".
- (Inference) This helps when you reuse one base query and project different columns from it.
- Image: crop of the console output; the full frame showed a local user path.
- Source: 19:44-19:46 ET, transcript 20261111-194400; crop of frame 20261111/194550.
-->

---
layout: "shot"
image: "/shots/day2/194710.jpg"
time: "Day 2 · 19:47"
---

# EF Core 11 modeling: complex types in TPC/TPT, temporal CLR properties, unconstrained FKs

<!--
- Say: Modeling gaps closed in EF Core 11: complex types and JSON columns work with TPC and TPT inheritance; temporal period columns can map to normal CLR properties; complex properties can have indexes; and you can declare a foreign key that is not enforced in the database.
- On screen, "Modeling": Complex types and JSON columns supported for TPC and TPT; Temporal period properties can be mapped to CLR properties; Indexes in complex properties; IsConstrained(false).
- Jiri (19:47): "complex types and JSON columns are now supported for TPC and TPT hierarchies"; with temporal tables "you can use these temporal properties" as CLR properties; "You can now introduce indexes on complex properties." "we can also define that some ... foreign key between entities is not constrained. So it's there, but it's not constrained on the database side."
- Also (19:46): SqlVector properties are no longer loaded by default — "rarely you need the SQL vector to be fetched onto the client side. It's purely for the vector search ... on the server side." And join pruning is a specific case: "Obviously, there are queries ... where it is needed."
- Source: 19:46-19:48 ET, transcript 20261111-194600; shot 20261111/194710.
-->

---
layout: "code"
---

# Indexes into complex properties, and `CREATE JSON INDEX` from a model

```csharp
modelBuilder.Entity<Customer>(customer =>
{
    customer.ComplexProperty(c => c.Address);
    customer.ComplexProperty(c => c.Contact);

    // New: indexes and keys can reach into complex properties
    customer.HasIndex(c => new { c.Address.Country, c.Address.ZipCode });
    customer.HasAlternateKey(c => c.Contact.Email);
});

modelBuilder.Entity<Vehicle>(vehicle =>
{
    // New: complex types (and JSON columns) on TPT/TPC hierarchies
    vehicle.UseTptMappingStrategy();
    vehicle.ComplexProperty(v => v.Registration, r => r.ToJson());

    // New: an index on a property inside a JSON column => CREATE JSON INDEX
    vehicle.HasIndex(v => v.Registration.Plate);
});
```

<!--
- Say: Complex properties now work like first-class columns for indexes and keys, complex types work with TPT/TPC, and an index on a property inside a JSON column generates SQL Server's CREATE JSON INDEX.
- Code is from the demo (Modeling/Program.cs, OnModelCreating, 19:48, shot 20261111/194840), with its own comments. The context also sets `UseCompatibilityLevel(170)`.
- Jiri (19:48): "I'm saying, hey, use the TPT mapping strategy. And what I can now define is an index. So first of all, I can index into a complex property ... But also, I can have a JSON index, because my complex property for registration ... is mapped into a JSON". "HasIndex and kind of dot into my complex property, in this case, registration and plate." The generated DDL then has the normal index and "the JSON index, where we correctly index" the JSON path.
- IsConstrained(false) (19:50): for data like "orders and customers imported" where you are "yet to synchronize customers", the relationship is "not enforced, but you still" want EF to know it: "I'm just saying, hey, IsConstrained(false)". "We can even exclude it from migrations using exclude foreign key from migrations". EF still uses it "to give you all the good joins ... or dropping the joins" (join pruning still applies).
- Source: 19:48-19:52 ET, transcripts 20261111-194805 and 20261111-195000; shot 20261111/194840. Frame 194955 not used (console shows a local user path).
-->

---
layout: "shot"
image: "/shots/day2/195241.jpg"
time: "Day 2 · 19:52"
---

# Migrations and `dotnet ef`: smaller fixes, file-based apps, `.config/dotnet-ef.json`

<!--
- Say: EF Core 11 migrations got many smaller fixes, and `dotnet ef` now reads a `.config/dotnet-ef.json` file and works with file-based apps.
- On screen, "Migrations": Migrations in one step; ExcludeForeignKeyFromMigrations(true); Skip ALTER COLUMN when only CLR type changes; -NoBuild for PMC; Migration bundles work with Central Package Management; Migrate and EnsureCreated now retry via the execution strategy.
- Jiri (19:52): Package Manager Console gets "a no-build switch similar to what we have for dotnet ef". If only the CLR type changes and the database type is the same, "We are not doing the ALTER COLUMN, because the ALTER COLUMN was kind of useless." Migrate and EnsureCreated now use "the retry execution strategy, the normal one that you configure, for example, for your SaveChanges".
- `dotnet ef` (slide "dotnet ef", shot 20261111/195629): "New support for .config/dotnet-ef.json", "Support for file-based apps" with `--file` and `--startup-file`. Jiri: "new support for a specific file in .config dotnet-ef.json and support for file-based apps. So even if you are using file-based apps ... you can generate migrations, apply them, and so on."
- dotnet-ef.json demo (19:54): without it, `dotnet ef` says "no project found" when data and web are separate projects; you must type `--project src/Blog.Data` and `--startup-project` "every time", "kind of boring ... or more people in your team need to type it every time". Now: "go into .config, create a dotnet-ef.json file" with `{ "project": "src/Blog.Data", "startupProject": "src/Blog.Web" }` (on screen), and plain `dotnet ef` commands work.
- Unconstrained FKs recap: the inner join with customers stays when needed, "even though there is no foreign key".
- Source: 19:52-19:56 ET, transcripts 20261111-195201 and 20261111-195403; shots 20261111/195241 and 195543.
-->

---
layout: "shot"
image: "/shots/day2/195704.jpg"
time: "Day 2 · 19:57"
---

# EF Core 11 on SQL Server: default compatibility level 160 (SQL Server 2022). Older server? Set it lower.

<!--
- Say: Check this before you upgrade: the SQL Server provider now assumes compatibility level 160, which means SQL Server 2022. On an older SQL Server, set a lower level; on SQL Server 2025, set 170 to get the new features (like JSON_CONTAINS and vector search shown earlier).
- Jiri (19:56): "in SQL Server, the new compatibility level is now 160, which means SQL Server 2022. If you are using SQL Server that's before 2022, you need to or you should change this to a compatibility level" that matches. "And if you are using SQL Server 2025, for example, then definitely set it to 170 so you can use all the new features in 2025."
- Also: the provider now uses Microsoft.Data.SqlClient version 7. More SQL translations, "a lot of those translations were contributed by community", e.g. int.Parse in a query now translates.
- How (from the demos): `sql => sql.UseCompatibilityLevel(170)` in the provider options.
- On screen, "SQL Server": Default compatibility level is now 160 (SQL Server 2022); Microsoft.Data.SqlClient moves to 7.0; More SQL translations (int.Parse, etc.).
- Source: 19:56-19:58 ET, transcript 20261111-195604; shot 20261111/195704.
-->

---
layout: "shot"
image: "/shots/day2/195815.jpg"
time: "Day 2 · 19:58"
---

# EF Core 11 Cosmos DB: transactional batches, bulk, System.Text.Json

<!--
- Say: The Cosmos DB provider gets transactional batches, bulk execution and session token management, and it moves from Newtonsoft.Json to System.Text.Json. Watch out: the __jObject backing property is gone.
- On screen, "CosmosDB": Support for transactional batches; Support for bulk execution; Support for session token management; Materialization now uses Utf8JsonReader (Newtonsoft.Json replaced by System.Text.Json); __jObject backing property is gone.
- Jiri (19:58): "transactional batches, bulk execution, and a new session token management. On the inner side ... We rewrote the materialization using the UTF-8 JSON reader that allowed us to switch from Newtonsoft JSON into System.Text.Json. And finally, also the __jObject backing property is now gone."
- Demo: a transfer of 100 units from a checking account to a savings account as a transactional batch, "Obviously, you want this to be transactionally consistent."
- SQLite provider (20:03, slide "SQLite"): "Added support for Half CLR type"; "No longer targets .NET Standard 2.0, only .NET 10+". Jiri: "That does not mean you cannot use the previous versions ... if you are on older versions of .NET or you need .NET Standard."
- (Inference) If your code read __jObject (raw JSON of a Cosmos document), that is a breaking change; check the EF Core 11 breaking-changes doc.
- Source: 19:58-20:00 ET, transcript 20261111-195805; shot 20261111/195815.
-->

---
layout: "shot"
image: "/shots/day2/200130-crop.jpg"
time: "Day 2 · 20:01"
---

# Cosmos `AutoTransactionBehavior`: EF 10's behavior could lose 100 in a race

<!--
- Say: The Cosmos demo shows why transactional batches matter. With the old behavior (Never: one request per document, what EF Core 10 did), a concurrent interest job caused an ETag conflict on savings after checking was already written, and 100 "vanished". WhenNeeded uses one transactional batch per partition and detects it; Always forces one transaction and fails across partitions.
- On screen: "1. Never: one request per document (what EF Core 10 did)". "Alice moves 100 from checking to savings. Meanwhile, the interest job credits 1 to savings, so the copy of savings we loaded is stale (ETag mismatch)." Result: "Conflict on savings, but checking had already been written: checking 900, savings 1, total 901 — should be 1,001: 100 has vanished". The code sets `app.Database.AutoTransactionBehavior = behavior;`.
- Jiri (20:00): three modes: "never, which is exactly what the EF10 executed it before. Then I will do when needed. Basically, it will be one transaction per partition." When documents "are in different partitions ... with when needed, it will be two operations. If I do always ... [it can't be done in a] consistent way because it's between different partitions." On Never: "the job that was running the interest kind of won, and the other one was lost because there was an ETag mismatch". With the new mode "we still have the mismatch, but at least I detected" it.
- WhenNeeded result (20:02): "the change was rolled back" — "The transfer between checking and savings account did not happen, but I detected it", then a retry: "now I have 900 and 101, which together is correct." Always: fails "because it's on different partitions" (Alice and Bob).
- Image: console cropped (the window title showed a local user path).
- Source: 19:59-20:03 ET, transcripts 20261111-195805, 20261111-200005, 20261111-200200; crop of shot 20261111/200130.
-->

---
layout: "shot"
image: "/shots/day2/200410.jpg"
time: "Day 2 · 20:04"
---

# New EF analyzers, and "check the breaking changes document"

<!--
- Say: EF Core 11 adds analyzer checks, so you may see new warnings after you upgrade. And read the What's New and Breaking Changes docs before you ship; "nothing super critical", but test first.
- On screen, "Analyzers": "EF1003 now catches string.Format/string.Concat in queries in raw SQL APIs"; "EF1004 warns about ToAsyncEnumerable (replace with AsAsyncEnumerable)".
- Jiri (20:04): "we detect more abuse in raw SQL APIs. We also catch some incorrect usage around async enumerables ... So you might see some new warnings and new fixes ... So don't be surprised." Docs: "what's new in EF Core 11 ... in greater details", and "some breaking changes in EF Core 11, some small, some slightly bigger. We don't have anything super critical, but still check our breaking changes document ... Test your application before deploying into production."
- (Inference) EF1003 matters for SQL injection: string.Format/Concat in FromSqlRaw-style APIs is the classic hole.
- After this, the host closed the live studio sessions for Day 2; an after-show of pre-recorded sessions followed (more Bruno, more Gerald, testing with AI).
- Source: 20:04-20:05 ET, transcript 20261111-200400; shot 20261111/200410.
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
