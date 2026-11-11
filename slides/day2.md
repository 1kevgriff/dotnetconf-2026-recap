---
theme: default
title: .NET Conf 2026 Recap - Day 2
info: |
  ## .NET Conf 2026 Recap - Day 2
  Kevin Griffin - Microsoft MVP
  Day 2 highlights, captured live from the stream.
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

- Day 2 highlights
- Kevin Griffin
- Microsoft MVP

<!--
- [title]
- Say: This is a recap of .NET Conf 2026 Day 2, captured live from the stream on 2026-11-11. Day 2 is the Microsoft product team day: Visual Studio in the morning, then Blazor, MCP, WinUI, Azure, file-based apps, Foundry and EF Core.
- Every number on these slides came from a speaker or an on-screen slide. Experimental and preview items are marked as such.
- Source: dotnetconf.net/agenda (Day 2 = 2026-11-11); stream transcripts from 11:00 AM ET.
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
- Transition: I watched Day 2 live so you don't have to.
-->

---
layout: "session"
num: 1
time: "11:00 AM"
speakers: "Mads Kristensen"
---

# Keynote: Visual Studio Now and Next

<!--
- [session 01] Day 2 opens with the Visual Studio keynote. The slide title on stream was "Visual Studio Now and Next".
- Say: Day 2 is the Microsoft product team day. Mads Kristensen (Principal Product Manager) opens it, and the morning is all Visual Studio: AI in VS, what's new, git, then debugging.
- His framing, from the opening: "the role of development is changing faster than maybe it ever has. AI is becoming part of our everyday development. Our solutions are getting bigger." And developers "still need the fundamentals required to be fast, to be reliable and effortless".
- Why it matters: the keynote sets up the pitch for the day: AI features in VS, but not at the cost of IDE speed and reliability.
- Caveat for the whole morning, Mads (11:26): some presenters show things that "may not be out just yet. Maybe it's in the Insiders build ... but it's not in the stable release yet." Say "Insiders" when a feature is not in 18.12.
- Mads has been on the VS team for 16 years: "this is probably one of the most exciting years in my time".
- Questions during the day: #questions in chat, or dotnetconfquestions.com (on the stream lower third).
- Source: 11:00-11:01 ET, transcript 20261111-110002; title card shot 20261111/110122.
-->

---
layout: "statement"
---

Code is an asset, not an artifact.

<!--
- Say: Mads's positioning for Visual Studio: it targets professional developers, and professionals treat code as an asset.
- His words (11:02): "Visual Studio is a little bit unique in that it targets specifically professional developers." Professionals have "quality gates ... accessibility, security, privacy".
- On vibe coding: "you might not care about your code that much, you might not even look at it. That's fine for ... your hobby projects". But for professionals, "You want to be able to review it ... maintain it for years to come ... It's not a byproduct of the app that you're building, but it has value in itself."
- Why it matters: this is the frame for every AI feature shown today: AI in VS should give code you can review and maintain, not throwaway output.
- Mads closed the keynote on the same line (11:26), on screen as "Code is an asset - not an artifact": "Visual Studio is a tool for professionals that sees code as an asset, not an artifact. But ... it doesn't have to be for every single project". VS should support you "whatever part of the AI journey you're on", including companies that limit AI "for security reasons or privacy".
- Source: 11:02 ET, transcript 20261111-110200; slide "Visual Studio is for professional developers" (shot 20261111/110215); close at 11:26, transcript 20261111-112603 (shot 20261111/112613).
-->

---
layout: "shot"
image: "/shots/day2/110443.jpg"
time: "11:04"
---

# ~27 user bugs fixed per workday. ~2 feature requests shipped.

<!--
- Say: The VS team fixes about 27 user-reported bugs and ships about 2 feature requests every workday, and both lines still go up.
- Mads (11:04): "we're actually fixing about 27 user-reported bugs per workday. That's pretty remarkable." And: "we're implementing about two feature requests per workday."
- The chart is monthly user bug reports, Oct 25 to Sep 26 (311 to 795 a month; trend line up). Mads said the September numbers are not all in yet.
- He showed the same kind of chart at .NET Conf a year ago. He gave credit to user feedback and votes, "partly because of AI" too.
- Why it matters: if you file a bug or vote on Developer Community, it has a real chance to get fixed.
- Source: 11:04-11:05 ET, transcript 20261111-110403; shot 20261111/110443.
-->

---
layout: "shot"
image: "/shots/day2/110631.jpg"
time: "11:06"
---

# VS 18.12 shipped yesterday: faster everywhere

<!--
- Say: Visual Studio 18.12 came out yesterday (Nov 10), and the theme is performance across the IDE.
- Mads (11:06): "the one we released yesterday, version 18.12, if you haven't gotten it, go get it."
- What got faster, per Mads:
  - UI responsiveness: less work on the UI thread, more on background threads.
  - Solution Explorer and version control: updates in batches, less UI lag. Error List: batch updates too, "much snappier and less hangs".
  - Designers (WinForms and XAML): faster startup and use.
  - Add New Item templates load faster.
  - Close solution / close VS is faster.
  - Copilot: loads all sessions, or one session, faster.
  - Test Explorer: loads the test hierarchy faster.
- No numbers were given for these. Do not quote a percentage.
- Why it matters: performance is the top request about VS; this release goes after the everyday lag.
- Source: 11:06-11:07 ET, transcript 20261111-110601; slide "Faster everywhere / Smarter UI updates" (shot 20261111/110631).
-->

---
layout: "shot"
image: "/shots/day2/110839.jpg"
time: "11:08"
---

# Stop build on first failed project: 26 s → 1.5 s

<!--
- Say: A long-standing request is in: a Tools > Options switch that stops the build at the first project that fails.
- Mads (11:08): "you can now flip a switch in the tools options to have it stop the build the first project that fails."
- The problem: VS and MSBuild keep going after a project fails, and most other projects then fail too because they depend on it.
- His test: Orchard Core, "an open source .NET project or solution with hundreds of projects", with a syntax error in one project.
- Chart: 4 runs, setting off 31/27/25/21 s, setting on 2/2/1/1 s. "Average: 26.0s → 1.5s (94% faster)".
- Agent angle, his words: "whether you're the one building or if your agent building is part of a loop that you're running, you're going to see much faster inner loop."
- Same release, also said: Live Unit Testing is 25% faster with xUnit.
- Jason Chlus demoed it live at 12:06 on Orchard Core: "this does have 260 projects, so it does take maybe four or five minutes to build. And with this new feature, you will see that it will stop on the first error in around 10 seconds." He credited Mads for the feature. At 12:14 he added: "the stop on first failure is also opt in", so turn it on in settings.
- Why it matters: a failed build in a big solution now fails in seconds, for people and for agents.
- (Inference) The release is 18.12; Mads showed this right after the 18.12 performance list. Check the release notes for the exact option name.
- Source: 11:08-11:09 ET, transcript 20261111-110804; shot 20261111/110839. Live demo: 12:06 ET, transcript 20261111-120600.
-->

---
layout: "shot"
image: "/shots/day2/111009.jpg"
time: "11:10"
---

# Editor rulers from `.editorconfig`

<!--
- Say: VS now draws vertical rulers from .editorconfig. `max_line_length` gives one ruler; the proposed `rulers` property gives several.
- Mads (11:10): with max line length "We'll now insert a vertical ruler." And `rulers` is "a proposal to add a property to EditorConfig ... It is not just yet standardized, but we're adding it here."
- On screen: `[*]`, `max_line_length = 80`, `rulers = 50, 80`.
- He said it is used most for Markdown, where teams want a set column width.
- Also in this part, for code review: "we're seeing a significant increase in the time people are spending reviewing code. Because you're getting more PRs now, usually from agents". To help:
  - Solution Explorer switches between folder view and solution view, so you see files outside the solution (readme.md, GitHub Actions workflows, Dockerfiles).
  - Hover over an image reference (HTML, C#, ...) shows it rendered, with more image types supported.
- Why it matters: `rulers` is not standard yet. It can work in VS and fail in other editors.
- Source: 11:10-11:11 ET, transcript 20261111-111004; shot 20261111/111009.
-->

---
layout: "shot"
image: "/shots/day2/111341.jpg"
time: "11:13"
---

# More PRs from agents → VS navigation for review

<!--
- Say: Developers spend more time on code review, much of it on agent PRs. VS added navigation to make review faster.
- Mads (11:11): "we're seeing a significant increase in the time people are spending reviewing code. Because you're getting more PRs now, usually from agents".
- The five items on the slide:
  - Folder view in Solution Explorer: see files outside the solution (readme.md, workflows, Dockerfiles).
  - More image types in hover previews, "more modern ones like WebP".
  - HTML class names and IDs: F12 goes to the CSS, LESS or SASS rule. With several rules, you pick one.
  - Markdown links: Go To / Peek Definition to the linked file; links in the preview work; fragment URLs go to the right spot.
  - Test Explorer: easier to go to failed tests and export logs.
- On tests and agents: "when we're letting agents loose on our code base, having those guardrails that the tests provide is absolutely crucial". More Test Explorer work is on the roadmap.
- Why it matters: VS frames review, not only code writing, as the daily job in an agent workflow.
- Source: 11:11-11:13 ET, transcripts 20261111-111004 and 20261111-111201; slide "Navigation and references" (shot 20261111/111341).
-->

---
layout: "shot"
image: "/shots/day2/111555.jpg"
time: "11:15"
---

# Copilot in VS now runs on the Copilot SDK, same as CLI and VS Code

<!--
- Say: VS removed its old Copilot harness and rebuilt Copilot on the Copilot SDK, the same engine as Copilot CLI and VS Code.
- Mads (11:14): "We've ripped out the old harness ... and replaced it with the Copilot SDK. This is the same SDK that the CLI is using and VS Code as well." "for the first time, we now have a shared foundation" and "you can move things around between them".
- What comes with it (the five bullets on screen):
  - Steering: redirect a running chat "without having to hit the stop button first". Mads: steering "has always been missing in Visual Studio".
  - Skills, agents, MCP servers "and a lot more", the same customizations as the SDK.
  - BYOK: "any OpenAI compatible endpoint", cloud, open models, or "local behind your firewall, on-prem". He said "with a few caveats"; the next session covers them.
  - Autopilot, as known from the CLI and VS Code.
- Why it matters: one set of skills, agents and MCP config can work across VS, VS Code and the CLI. And BYOK with local models helps teams that cannot send code to the cloud.
- Source: 11:14-11:15 ET, transcript 20261111-111400; slide "Stronger foundation" (shot 20261111/111555).
-->

---
layout: "shot"
image: "/shots/day2/111935.jpg"
time: "11:17"
---

# Copilot checks its own fix by driving your running app (Insiders)

<!--
- Say: Copilot in VS can now run your app, go to the bug, and check that its fix works. The slide calls it "UI Automation > hands free debugging". It is in the latest VS Insiders, not stable: Harshada (13:08) said "we recently added a UI automation in our latest insiders of Visual Studio". Mads had warned that some keynote items are Insiders-only.
- Mads (11:17): "we can now have Copilot do UI automation, which means you can tell it to fix a bug, and it will automatically be able to verify the fix ... by loading and running your app and navigating to the place where this issue was". It can take screenshots and investigate dump files.
- Autopilot, from the same minute: "bigger tasks that can run for hours and hours on end, spin up sub-agents". Chat sessions are now separate from the solution, so a session keeps going "even if the solution has to be reloaded or closed".
- Mads's own use: "I've been using it for two, three months, and it's a complete game changer." And: "if you ... tried Visual Studio and Copilot in the past and thought ... it wasn't the best thing in the world, try it again."
- Why it matters: the agent closes the loop itself: fix, run, check. Mads ties it to the IDE: "what's really cool about an IDE is that it has all the tools that you need in the box."
- Source: 11:16-11:17 ET, transcript 20261111-111605; slide "Your running application" (shot 20261111/111935, all four bullets shown).
-->

---
layout: "statement"
---

"Hey, can you make my app run faster?"

<!--
- Say: In VS chat you can ask Copilot to make your app faster. The agent uses the profiler, writes benchmarks, optimizes, and runs the benchmarks again.
- Mads (11:19): "You can simply just in the chat window say, hey, can you make my app run faster? And it will figure out how to do that instrumentation, write the benchmark, run them, figure out where the slow paths are ... And then make the optimizations, run the benchmarks again". It works through sub-agents; "You don't have to select the profile[r]."
- Perf tips: when you step through code, the "elapsed" PerfTip now has a button ("Click to suggest optimizations with Copilot", on screen). Copilot and the profiler work together to explain why the call was slow.
- Dump files: the agent helps analyze a dump from the cloud or a customer machine. Mads: "Analyzing dump files is not easy and not that many people know how to do it", and he counts himself among those who are "not the best debuggers in the world".
- Status, from Harshada's session (13:24): dumps now have a "Debug with Copilot" option that opens chat with a first analysis; from a PerfTip you can run a profiler analysis with a suggested fix and apply it with Hot Reload without stopping the debug session. She called these "newer, smaller features which we introduced in our recent Insiders release". So: Insiders.
- Why it matters: profiling and dump analysis were expert-only work. Now you can ask in chat.
- Source: 11:18-11:19 ET, transcript 20261111-111805; slide "Your running application" (shot 20261111/111935). Insiders status: 13:24 ET, transcript 20261111-132405.
-->

---
layout: "shot"
image: "/shots/day2/112553.jpg"
time: "11:21"
---

# Start in the CLI, move the session into VS for the debugger (coming)

<!--
- Say: Microsoft is building a way to move a Copilot chat session from the CLI, VS Code or the Copilot app into Visual Studio, to keep going with VS tools. Say "coming", not "shipped".
- Status conflict: Mads (11:22) said "now you can. So you can actually round trip these sessions". But Rachel (11:59) said "we're definitely investing more in this area ... seamless access to all of your co-pilot sessions", and Harshada (13:17) said of the CLI-to-VS hand-off: "this particular experience is not out yet. It is coming soon." Treat it as coming.
- On screen (slide "Your workflow understood"): "Roundtrip chat sessions from CLI, VS Code, Copilot App", "Create tests – profile them – debug – fix", "Worktrees and sub modules", "Full code review and pull request flow" (next slide).
- Mads (11:20): "we know that you're not always using Visual Studio for everything and that's totally fine." If you started in the CLI and find "you need a debugger or you need a profiler", you can "take that session that you have in the Copilot CLI and simply move it into Visual Studio and continue with it there", and add "that debugger, that UI automation".
- Why roundtrip works, Mads (11:22): "all because we're using the same copilot SDK harness."
- Tests in any order: "A lot of people do tests first, like TDD". Some "write their own tests ... and then they might say, okay, agent, run loose and build the feature, but I want to control the tests." Test Explorer has new features for this.
- VS tool calls make the agent faster; his example: the stop-on-first-failed-build switch, "you get that only in Visual Studio".
- Worktrees and submodules: "We got the full support." He said users kept telling the team that agents use worktrees. With worktrees, "we can have multiple agents work in the same code base without stepping on each other's toes". With submodules, you can open, commit and send PRs across them.
- Why it matters: VS becomes one stop in a session, not the only place you work.
- Source: 11:20-11:23 ET, transcripts 20261111-112004 and 20261111-112204; slide "Your workflow understood" (shot 20261111/112553).
-->

---
layout: "statement"
---

The full PR review flow is now inside Visual Studio.

<!--
- Say: VS now has the main PR and code review features that you used to go to GitHub.com or Azure DevOps for.
- Mads (11:25): "we're now at a point where we have all the major features that you typically would rely on GitHub.com or Azure DevOps to kind of do the last mile to get the PR just over the hump. That's now all in Visual Studio".
- His reason: "when the agents are writing most of our code ... we are reading more code than we are writing it to a larger extent than ever before."
- Agent tie-in: chat sessions you already have "can now participate in the review and in the PR creation", so you reuse that context.
- He said "there's a lot more to come", and that Sebastian (the git session, 12:30 PM) "will show a whole lot there". No list of the PR features was shown in the keynote.
- Why it matters: if most code comes from agents, review is the main job, and VS wants it to happen where the code and the agent context are.
- Source: 11:24-11:25 ET, transcript 20261111-112403; bullet "Full code review and pull request flow" (shot 20261111/112553).
-->

---
layout: "session"
num: 2
time: "11:30 AM"
speakers: "Rachel Kang, Barbara Boyajian"
---

# The State of AI in Visual Studio: New Brain. More Choice.

<!--
- [session 02] Rachel Kang and Barbara Boyajian, both Microsoft. The agenda lists only Rachel; the title card shows both.
- Headline of the session, Rachel (11:30): "The new agent harness powered by the Copilot SDK is now generally available in Visual Studio."
- "New Brain" = the new agent harness on the Copilot SDK (the one Mads introduced in the keynote). (Inference) "More Choice" = more ways to pick models and agents; Rachel said only "a whole lot more choice that we now offer in Visual Studio to put your AI to work".
- Version: the slide "Introducing the new agent harness" has a badge "GA in 18.12 stable" (shot 20261111/113233). So it shipped in the release from Nov 10.
- Why it matters: the keynote's Copilot SDK rebuild is GA in the stable channel, not a preview.
- Source: 11:30 ET, transcript 20261111-113000; title card shot 20261111/113025.
-->

---
layout: "shot"
image: "/shots/day2/113328.jpg"
time: "11:33"
---

# Same model, new harness: 103 → 124 C# tasks resolved

<!--
- Say: The VS team ran the old and the new agent harness on the same C# benchmark with the same model. The new harness solved 21 more tasks.
- On screen: SWE-Bench-CSharp-General, 157 C# tasks, GPT-5.6 Sol, one run per experience. Previous 103, new 124, "+21 additional tasks resolved". "Resolved = failing tests pass without breaking previously passing tests."
- Rachel (11:33): "the new agent harness resolved up to 21 additional tasks on the same exact model".
- Her point: "oftentimes we focus on the model ... but it's only one part". An agent also needs context, memory and tools, and the harness brings them together. The harness diagram (shot 20261111/113233) shows Context, Memory, Tools, Execution around the Model, with the badge "GA in 18.12 stable".
- The Copilot SDK harness is "common across all Copilot experiences on all of your favorite platforms", so improvements in one come to VS.
- Caveat: one run per experience, Microsoft's own benchmark. Say it as their number.
- (Inference) 103/157 ≈ 66%, 124/157 ≈ 79%.
- Why it matters: the harness, not only the model, changes results. Same model, about 20% more tasks solved.
- Source: 11:32-11:33 ET, transcript 20261111-113203; slide "Same model. More tasks resolved." (shot 20261111/113328).
-->

---
layout: "statement"
---

Same prompt, same model: repro in chat in 8 s vs. manual steps in 48 s.

<!--
- Say: Side by side, same prompt, same model. The new harness reproduced the bug right in chat in 8 seconds. The old one took 48 seconds and gave a list of manual repro steps.
- The bug: long multiple-choice options cut off in a narrow Copilot Chat window (a real bug on the Copilot team).
- On-screen captions: "Provided manual steps in 48 seconds / The issue wasn't reproduced in chat" vs. "Reproduced the issue in 8 seconds / Right here in chat". The old side shows "Claude Opus 5.5" as the model.
- Rachel (11:34): "Same exact prompt, same exact model, only difference here being this new awesome harness." The new side "already reproduced the issue directly for us right in the chat in a matter of seconds".
- New agent controls: next slide.
- Screenshot not used: the demo frame shows a presenter's local user path.
- Why it matters: the harness changes what the agent does (it acts in the IDE), not only how fast it answers.
- Source: 11:34 ET, transcript 20261111-113402; shot 20261111/113452 (not in repo).
-->

---
layout: "shot"
image: "/shots/day2/113507.jpg"
time: "11:35"
---

# Six new agent controls in VS

<!--
- Say: The new harness also brings six new ways to guide and check the agent in VS.
- The six tiles on screen:
  - Steer mid-task: add instructions; cancel while pending.
  - Inspect tool results: open tool results; copy exact commands.
  - Watch subagents: see each model and its live steps.
  - Resume local chats: find chats across local solutions and folders.
  - Work beyond a solution: choose a working folder; attach folders as context.
  - Get a second opinion: critique a plan; review security risks.
- Rachel (11:34): "we can do things like steer the agent mid-task, we can follow the work that it delegates to the various sub-agents, and we can work beyond the scope of the existing solution by choosing a working folder". The other three tiles are from the slide only; she did not talk about them in this part.
- Demo (11:36), CareDesk sample clinic app: a one-click reschedule made a double booking (two patients at 10 AM with the same doctor). Rachel asked Copilot to block that and remove the suggested reply. While it worked, she changed her mind and steered it: keep a reply, but tell the patient the time is unavailable. No stop button needed.
- Why it matters: you can see what the agent did (tool results, subagents) and correct it while it runs, not only after.
- Source: 11:34-11:37 ET, transcripts 20261111-113402 and 20261111-113603; slide "What's new in the agent experience" (shot 20261111/113507).
-->

---
layout: "shot"
image: "/shots/day2/114110.jpg"
time: "11:41"
---

# Agent added 10 tests, saw 1 fail, fixed itself: 50/50 pass

<!--
- Say: The agent wrote regression tests for the double booking, ran them, saw one fail, and fixed its own code without being asked. All 50 tests pass.
- Before: 40 tests, all passing. Rachel (11:38): "we clearly don't have tests that accounted for this". She asked it to add tests, run them, then build and relaunch.
- Rachel (11:40): "We have 10 additional ones now that are automatically being run by the agent ... One of them is failing". "Back in the day ... I would have had to ask Copilot to please acknowledge that this test failed and fix it." Then: "now we're seeing that all 50 tests are passing."
- On screen: chat log "Ran 37 test(s). 36 Passed, 1 Failed", then edits to MessagingWorkflowTests.cs and SchedulingViewModel.cs; Test Explorer "50 Passed". The chat footer shows Agent, "Autopilot (Allow all)", model GPT-6.1 Sol. The agent also read a SKILL.md.
- After relaunch, the faulty reschedule action to double book was gone.
- Why it matters: this is the "tests are the guardrails" point from the keynote, done by the agent inside VS.
- Source: 11:38-11:41 ET, transcripts 20261111-113805 and 20261111-114000; shot 20261111/114110.
-->

---
layout: "shot"
image: "/shots/day2/114311.jpg"
time: "11:43"
---

# Bring your own model: local servers, gateways, proxies. GA in 18.12.

<!--
- Say: "More Choice" starts with models. Bring your own model (BYOM) is GA in 18.12 stable (badge on the slide), and it now connects to more kinds of endpoints.
- Barbara (11:42): BYOM is for "regulated industries think healthcare defense", where it "can be what enables the usage of AI coding tools", and for "air-gapped environments". It is for teams that want "their prompts and their code [to stay] within their boundaries".
- On screen, "More ways to connect your models":
  - Multiple connections: keep named connections to the same provider. Barbara: "let's say you have three OpenAI compatible custom endpoints ... you can add them all".
  - Custom endpoints: OpenAI-compatible gateways and local model servers.
  - API format: Completions, Responses, Messages.
  - Optional API keys, model settings (edit in the UI), proxy-aware connections (uses the VS proxy settings).
- Mads said in the keynote that BYOK has "a few caveats". Listen for them; this part did not name any.
- Why it matters: teams that cannot send code to a cloud model can now use the VS agent with their own approved model.
- Source: 11:42-11:43 ET, transcript 20261111-114201; slide "More ways to connect your models" (shot 20261111/114311).
-->

---
layout: "shot"
image: "/shots/day2/114426.jpg"
time: "11:44"
---

# AI in VS with no GitHub account: Foundry, OpenAI, Anthropic, Ollama

<!--
- Say: With BYOM you can use the VS agent while signed out of GitHub. You bring a provider: Microsoft Foundry, OpenAI, Anthropic, Ollama, or any OpenAI-compatible endpoint.
- On screen, "Your model. Your IDE.", badge "GA in 18.12 stable": GitHub Copilot, Microsoft Foundry, OpenAI, Anthropic, Ollama, Custom Endpoint (e.g. OpenRouter). "No GitHub account required".
- Barbara (11:44): "We support Microsoft Foundry, OpenAI, Anthropic, Olama [Ollama], and OpenAI-compatible custom endpoints ... this includes popular providers like Open Router and LM Studio." And: "if you don't have a GitHub account, that doesn't block you from using it. You can be signed out and configure your BYOM providers."
- Demo: signed out of GitHub, the first-run choice was "sign in with GitHub", "use Foundry", or "continue with an API key for another provider". She added a Foundry connection named "work"; her deployed models loaded and chat turned on.
- Demo, part 2 (11:48): she added LM Studio, running on her machine, as a custom OpenAI-compatible endpoint, with no API key ("I didn't configure it that way"). The model picker then lists the models of every provider with the provider name next to each (Microsoft Foundry, OpenAI, ...); pinned models stay on top (shot 20261111/114942, not in deck).
- Why it matters: Copilot sign-in is no longer the gate to AI in VS. Shops on Foundry or a local Ollama box can use the same agent.
- Source: 11:44-11:49 ET, transcripts 20261111-114401 and 20261111-114802; slide "Your model. Your IDE." (shot 20261111/114426).
-->

---
layout: "shot"
image: "/shots/day2/115345.jpg"
time: "11:53"
---

# Managed settings: admins can turn off Autopilot (18.13 Insiders)

<!--
- Say: Admins can now push AI controls to Visual Studio. The first control locks down Autopilot. It is a preview in 18.13 Insiders, not in stable yet.
- On screen, "Managed settings": "Admins define and distribute AI controls." Channels: GitHub server, MDM managed, file-based settings.
  - Available now: Autopilot permissions, `disableBypassPermissionsMode`, badge "Preview in 18.13 Insiders".
  - Coming soon: `allowedMcpServers`, `deniedMcpServers`, "And more controls".
- Rachel (11:53): "Admins can now define and distribute the supported controls through GitHub Server, MDM managed settings, cloud-based settings, and managed settings are available in Visual Studio Insiders today, starting with Autopilot and more on its way soon." (She said "cloud-based"; the slide says "File-based settings".)
- Demo video: one account has full Autopilot; in the other, the admin restricted it.
- Context: the mode menu on screen shows Interactive, Autopilot ("End-to-end execution without interruption"), Plan, and Tool permissions "Allow all".
- Why it matters: the answer to "can we let devs run Autopilot?" for enterprises. (Inference) The MCP server allow/deny lists that come next may matter more, because they control which tools an agent can reach.
- Source: 11:52-11:53 ET, transcript 20261111-115200; slide "Managed settings" (shot 20261111/115345).
-->

---
layout: "statement"
---

Next for AI in VS: code review, agent visibility, multi-agent workflows.

<!--
- Say: Rachel closed with where VS goes next, based on user feedback: more code review, more visibility into what agents do, and multi-agent workflows.
- On screen, "Agentic development keeps evolving / What we're hearing": "More generated code to assess", "Hard to follow the agent's work", "More agents to coordinate".
- Rachel (11:54): "there's a lot more generated code to review, more activity to follow, and more tasks for agents to coordinate ... We know that we want to focus more on code review, agent visibility, multi-agent workflows, and more."
- This matches Mads's keynote: review time is up, and the PR flow is now in VS.
- No dates or versions were given for these.
- Q&A (11:58), "Will Visual Studio expose an MCP server so that other agents can control Visual Studio?" Answer starts "That's a great question. That's definitely something that's been in ..." (cut at the chunk edge), then: "We've been playing around with that concept starting with the debugger and the specific uniquely powerful tools that make Visual Studio Visual Studio." They ask which VS tools you want exposed first. Experiment only, no commitment.
- Why it matters: the bottleneck moves from writing code to reviewing and following agent work.
- Source: 11:54-11:59 ET, transcripts 20261111-115402 and 20261111-115804; slide "Agentic development keeps evolving" (shot 20261111/115437, not in deck).
-->

---
layout: "session"
num: 3
time: "12:00 PM"
speakers: "Jason Chlus"
---

# What's new in Visual Studio

<!--
- [session 03] Jason Chlus, Product Manager, Visual Studio. A fast demo of new VS features.
- Jason (12:00): "I have roughly 25, maybe 26 features that I'm going to be showing." "Most of these features come from developer community."
- Coming: "very soon you will be able to report a problem, suggest a feature directly in Visual Studio using the chat."
- Say: this is the feature tour. I picked the ones that matter most for day-to-day work.
- Source: 12:00 ET, transcript 20261111-120004; title card shot 20261111/120104.
-->

---
layout: "shot"
image: "/shots/day2/120910.jpg"
time: "12:09"
---

# Test Explorer now diffs failed string assertions

<!--
- Say: When a string assertion fails, Test Explorer now shows Expected and Actual side by side, with the different characters marked.
- Demo: the Turkish-I bug. A `ToSnakeCase` helper used `ToLower()`. Under the tr-TR culture, "I" lowercases to a dotless "ı", so the test `ToSnakeCase_DoesNotDependOnCurrentCulture ("tr-TR")` failed: Expected "is_enabled", Actual "ıs_enabled". The fix: `ToLowerInvariant()`.
- Jason (12:08): "you will not get the dot above the i, and we are expecting that dot above the i. So we will have to add back to lower invariant." He credited the MSTest team; they have a testing session later.
- Also on screen: "Last run: 11/11/2026 9:08:34 AM" on the test detail. Jason: last run shows for groups and single tests, so you see when a result is old.
- Why it matters: the hardest string failures (one invisible character) are now visible at a glance.
- Source: 12:08-12:09 ET, transcript 20261111-120800; shot 20261111/120910.
-->

---
layout: "shot"
image: "/shots/day2/121506.jpg"
time: "12:15"
---

# Colorized Output window (ANSI colors). Opt-in.

<!--
- Say: The Output window now shows ANSI colors, so warnings and errors in a messy build stand out. It is off by default; turn it on in settings.
- Jason (12:14): "we have colorized output in VS ... especially when your builds get messy and you're looking to quickly scan find warnings infos errors". "this is not on by default so that is one of those features that you will have to opt in on". You can edit all the colors.
- On screen: Output "Show output from: Colorized Output", the 16 ANSI foreground colors (30-37 standard, 90-97 bright), and the new Fonts and Colors page in Tools > Options with search and live preview.
- Other quality-of-life items in the same tour (12:12-12:14):
  - Move tabs with the keyboard; "close all tabs to the right"; a new option for tighter tabs.
  - New keyboard shortcuts UI: search commands (e.g. Zoom Reset), "record your steps" to find a binding, pick standard schemes. Reset zoom with Ctrl+Num0.
  - New Fonts and Colors UI: search an item, edit in place, see a preview.
  - Git: from your repo view you see history and PRs; "We have the complete end-to-end in VS now. You can go from coding to code review to creating a PR." Review changes since any commit.
- Why it matters: many small DevCom requests closed at once. Two of the best (colorized output, stop on first failure) are opt-in, so tell people to turn them on.
- Source: 12:12-12:15 ET, transcripts 20261111-121201 and 20261111-121401; shot 20261111/121506.
-->

---
layout: "shot"
image: "/shots/day2/121712.jpg"
time: "12:17"
---

# Review local code as a PR, then hand your comments to Copilot

<!--
- Say: VS can show your local changes as a PR: a multi-file diff with inline comments. Then you send all your comments to Copilot chat, and it makes the changes.
- Jason (12:16): "We're going to be basically reviewing local code as a PR. So you'll see a very nice multi-file summary diff." You leave comments in the view, open files, get previews. "this is just going to be my new way of reviewing my local code".
- Hand-off to chat: "it basically hands off the file context it uses my previous build context and it will give the specific line context over to chat so it can make those changes."
- Change groups: "schema changes, version bumps, and things like that that kind of create a lot of noise. These groupings will allow you to get to the meat and the potatoes of the code much faster."
- On screen: diff of AGENTS.md ("5 changes"), an inline comment "Clean this up and recover this work" (Active, 1 of 4 total), and the Copilot chat at left.
- This is the "full code review and pull request flow" from Mads's keynote, shown live. More in the git session at 12:30 PM.
- Why it matters: review comes before the PR, in the IDE, and the agent does the fix-ups from your comments.
- Source: 12:15-12:17 ET, transcripts 20261111-121401 and 20261111-121602; shot 20261111/121712.
-->

---
layout: "statement"
---

Hot exit: close VS with unsaved changes. Reopen, nothing lost.

<!--
- Say: VS now has hot exit. Close it with unsaved changes, open it again, and the unsaved changes are still there. It works for solutions and Open Folder. It is OFF by default: turn on "Reopen unsaved documents on solution load or empty environment" in Tools > Options (from Jason's recap slide, next).
- Jason (12:22): "now we have this first class experience where you can simply just leave Visual Studio with unsaved changes. This is called the hot exit feature." "There was a lot of intricacies ... with solutions and open folder".
- His use cases: SQL queries, empty scratch files, "updating skills, agents, whatever it may be ... go grab your lunch and then come back, and you will not have lost anything."
- Demo: unsaved MarkdownFile2.md in the Orchard Core solution came back after closing and reopening VS (shot 20261111/122334, not in deck).
- SSMS: "This is also coming to SSMS ... I think that'll be in the next release." Say "planned", not "shipped".
- Teaser: Jason is "working on a PR that will allow you to export your test results" from Test Explorer. In progress, no date.
- Why it matters: you can close VS at any time, also with agent and skill files half edited, and lose nothing.
- Source: 12:22-12:23 ET, transcript 20261111-122204.
-->

---
layout: "shot"
image: "/shots/day2/122414.jpg"
time: "12:24"
---

# ~26 VS features. Three are off by default: turn them on.

<!--
- Say: Jason's recap slide lists everything he showed. The ones with a magnifier are off by default; search Tools > Options for the term shown.
- Off by default (on-screen search terms):
  - Stop build on first failure: "Stop solution build after the first project fails".
  - Colorized Output: "Enable colorized output".
  - Hot Exit: "Reopen unsaved documents on solution load or empty environment".
- Jason (12:24): "those little magnifying glasses are basically those features that are not immediately on by default. So you will need to go find those in your tools options and enable them".
- The six groups on the slide: Navigate & edit (File System View, drag files into chat, new Markdown file, drag files and images into Markdown, HTML-to-CSS navigation, CSS color preview); Copilot (customize chat defaults, new Copilot Chat experience); Build; Test Explorer (assertion string comparison, open test log, last run time); Tabs (move with keyboard, tool-window tab sizing, close tabs to the right, tab drag performance); Personalize (Fonts and Colors UI, Colorized Output, Keyboard Shortcuts UI, Zoom Reset, Hot Exit); Code review (local review, multi-file summary diff, address comments in chat, comment filters, change groups).
- Pointers: Harshada's session (1:00 PM) for debugging and profiling agents; Mika's session (4:00 PM) on the modernization agent, for moving from .NET 8 or 9 to .NET 11. Feedback: developercommunity.visualstudio.com.
- Q&A (12:26):
  - All editions: "These are all available for all SKUs of Visual Studio" (Community, Pro, Enterprise).
  - Recent: "I think 18.11 was the oldest feature that I showed." Mads: "we just released 18.12 yesterday ... We're releasing every month now." Jason: 18.13 "is even looking more jam-packed", and work on 18.14 has started.
  - HTML-to-CSS go-to-definition also works in Razor (Mads tested it) and for SASS and LESS.
  - Accessibility (12:29): a viewer must set a 17 pt minimum font again after each fresh install. Jason: "It's not as simple as you would think ... but we are looking into a few features that you can increase font size very fluidly, as well as icons and potentially even being able to customize icons." "Coming soon" was said, but no version; say "they are looking into it".
- Why it matters: this is the slide to screenshot. Three of these features need one settings change each, and they are in every VS edition.
- Source: 12:24-12:27 ET, transcripts 20261111-122404, 20261111-122603 and 20261111-123003; slide "What we saw today" (shot 20261111/122414).
-->

---
layout: "session"
num: 4
time: "12:30 PM"
speakers: "Sebastian Hernandez"
---

# Get the most out of Version Control in Visual Studio 2026

<!--
- [session 04] Sebastian Hernandez, Software Engineer. Title on the title card; the agenda calls it "Get the most out of git in Visual Studio".
- Goal, Sebastian (12:30): do "your entire developer workflow from start to finish, all within Visual Studio without having to leave the IDE."
- Agenda slide: Version Control Environment, Create a new Feature, Local Code Review, Version Control with AI, Create Pull Request, Review Pull Request.
- This is the deep dive Mads promised in the keynote ("Sebastian will show a whole lot there").
- Source: 12:30-12:31 ET, transcript 20261111-123003; title card shot 20261111/123138; agenda shot 20261111/123153.
-->

---
layout: "shot"
image: "/shots/day2/123404.jpg"
time: "12:34"
---

# Worktrees and submodules in the Git Repository window

<!--
- Say: The Git Repository window now manages worktrees and submodules. Right-click a branch to make a worktree; open it here or in a new VS window.
- Worktrees, Sebastian (12:33): right-click a branch, "you'll see that at the bottom we have those commands that allow you to create a new work tree". Name it, then open it in the current window or "perform the task in the background". Right-click a worktree to open it in the current window or a new window, or delete it.
- On screen, branch context menu: "New Worktree From...", "Open Worktree in Current Window", "Open Worktree in New Window", "Delete Worktree"; also "Add to Chat" and "New Pull Request". Demo repo: TypeScript (main).
- Agent angle: worktrees are "very popular nowadays, especially in this agentic AI world". You can "kick off multiple parallel sessions at the same time within different Visual Studios with different work trees".
- Submodules: a Submodules node in the Git Repository window. Click one to see its checked-out commit; right-click to update or delete it.
- Why it matters: one repo, several agents, each in its own worktree and VS window, with no file conflicts.
- Source: 12:33-12:35 ET, transcripts 20261111-123204 and 20261111-123404; shot 20261111/123404.
-->

---
layout: "shot"
image: "/shots/day2/124514.jpg"
time: "12:45"
---

# Merge conflicts: take all in one click, or Auto Resolve with Copilot

<!--
- Say: In a merge or rebase, you can now keep all current or take all incoming for the whole tree in one click. Or click Auto Resolve and Copilot resolves the conflicts in chat.
- Sebastian (12:44): "if you right-click on the parent node and you're totally sure that you want to take all the changes from main, you can do that now. Before, you had to do one at a time." Same for all incoming changes. "Or over here in this auto-resolve button, if you want to let AI fully resolve your merge conflicts in the chat you can do that as well."
- Works on the parent node or on a single file.
- While Copilot resolves (12:46): "you won't be able to edit the files because AI is making sure that nothing is being touched at the moment".
- On screen: Git Changes, "Rebase in progress with conflicts", Unmerged Changes (4); context menu: Merge..., Keep All Current, Take All Incoming, Auto Resolve, Stage.
- Result (12:48): Copilot resolved the conflicts, then built "the necessary or adequate projects to make sure that the merge conflicts resolutions are working properly". Build succeeded. Sebastian checked the merge editor: "what we would have done manually is it took the right hand side and then it kept the left hand side for the new property ... I'm happy with this."
- Escape hatch: "if for some reason AI totally went sideways", use the Accept Merge dropdown to "restart the resolution completely" and handle it yourself, or let AI try again. "we all know that AI is not perfect."
- He asked the audience: what do you let AI do in version control, and what not?
- Why it matters: bulk resolve removes the one-file-at-a-time step; Auto Resolve puts Copilot inside the merge flow, with the files locked while it works.
- Source: 12:44-12:49 ET, transcripts 20261111-124404, 20261111-124603 and 20261111-124803; shot 20261111/124514.
-->

---
layout: "shot"
image: "/shots/day2/125235.jpg"
time: "12:52"
---

# Full PR review in VS, for GitHub and Azure DevOps

<!--
- Say: The pull request experience is now fully in the IDE, for GitHub and Azure DevOps. Vote, complete, comment, and edit the code right in the PR diff.
- Sebastian (12:50): "this pull request experience is now fully in the IDE. It's very similar to what we have on Azure DevOps or on GitHub. It works for both."
- What you can do: publish or abandon your PR; vote on others (approve, wait for author, reject); complete or set auto-complete. The overview shows the description with images and GIFs, iterations, global comments; reply, resolve, and filter comments by status or author.
- AI grouping: "kickstart your review with AI ... Can you bucket them into similar areas so that it's easier for the reviewer to review?" ("generate group").
- Check out the PR: test your teammate's edge cases; or, as the author, "you can actually edit the files" in the PR view and respond to comments in place.
- On screen: PR #805625 "[DO NOT REVIEW] Test", Changes (7) with checkboxes to mark files reviewed, and an AI review comment ("VSEng Copilot Code Reviewer ... Maintainability", model gpt-6-luna) asking for an extra test.
- Why it matters: this is the "full code review and pull request flow" from the keynote. Review, comments and fix-ups can all stay in the IDE.
- Source: 12:50-12:53 ET, transcripts 20261111-125004 and 20261111-125205; shot 20261111/125235.
-->

---
layout: "shot"
image: "/shots/day2/125825.jpg"
time: "12:58"
---

# "When you reboot a tech, you lose half your audience ... we grew more customers."

<!--
- [surprise guest, between sessions 04 and 05] Mads Kristensen with "Mr. .NET". Mads calls him "Scott"; no lower third was shown. He said: "I was here from 2007 until last year", and Mads said he was Mads's manager "back in your ASP.NET days".
- (Inference) This is Scott Hunter. The stream never said his last name, but all the on-stream facts fit him: first name Scott, "Mr. .NET", Mads's manager in the ASP.NET days, on the team that made .NET Core / Project K, at Microsoft 2007 until last year. Confirm before you name him.
- Say: A short history break. One of the people who rebooted .NET as .NET Core looked back on it.
- Why .NET Core: "because of Windows compatibility, you basically can't change .NET Framework anymore."
- The quote (13:02): "The scary thing is most of the time when you reboot a tech, you lose half your audience ... it's amazing that we rebooted .NET. And not only did we reboot it, but we grew more customers. And we actually made a better product." He named Damian Edwards, David Fowler and Glenn Condron as part of that early team.
- Velocity: "that original .NET framework really had four versions. And we're at version 11 of the new one."
- History bits: Project Helios (ASP.NET off IIS); going "bare metal" for speed (Kestrel); project.json "had to happen to go convince the Visual Studio folks" to simplify csproj.
- Why it matters: 11 releases in, the reboot worked. That context helps people who are still on .NET Framework.
- Source: 12:58-13:05 ET, transcripts 20261111-125800, 20261111-130002, 20261111-130201, 20261111-130401; shot 20261111/125825.
-->

---
layout: "session"
num: 5
time: "1:05 PM"
speakers: "Harshada Hole"
---

# What's new in Visual Studio Diagnostics

<!--
- [session 05] Harshada Hole, Visual Studio. Title card: "What's New in Visual Studio Diagnostics", subtitle "From a visible symptom to an evidence-backed fix" (shot 20261111/130551). The agenda title is "What's New in Visual Studio Debugging and Diagnostics".
- Jason pointed here for the debugging and profiling agents: "the connected diagnostic experience ... the full experience with everything from start to finish".
- Source: dotnetconf.net/agenda, Day 2, 1:00 PM ET; started about 1:05 PM ET.
-->

---
layout: "shot"
image: "/shots/day2/130801.jpg"
time: "13:08"
---

# Debugger Agent: give it a bug URL. It reproduces, fixes, verifies.

<!--
- Say: The Debugger Agent takes a GitHub or Azure DevOps bug URL and runs an "investigation loop": reproduce, investigate, correct, verify, all in VS.
- Harshada (13:08): the Debugger Agent "not just reads your logs, but it actually has a full runtime context. It understands your breakpoint, your call stack". With the bug URL, "it will actually reproduce ... investigate it, actually correct it, even create hypotheses if needed, and then verify the fix".
- On screen, "The investigation loop / A bug fix is more than a code change": Reproduce > Investigate > Correct > Verify. Three modes: Manual investigation | Test-driven investigation | UI Automation.
  - Manual: you reproduce and verify with your own judgment.
  - Test-driven: "The agent will actually use the existing test suite, even create a new test if needed".
  - UI Automation: "recently added ... in our latest insiders", for UI and WPF bugs. Insiders only.
- Demo next: eShopOnWeb running locally, a wrong cart total for the ".NET Bot Black Sweatshirt" (name from the screen, next slide).
- Why it matters: the agent works from the runtime state, not just the source, and proves the fix.
- Source: 13:08-13:09 ET, transcript 20261111-130801; slide "The investigation loop" (shot 20261111/130801).
-->

---
layout: "shot"
image: "/shots/day2/131523.jpg"
time: "13:15"
---

# Debugger Agent found the bug under the debugger, fixed it, proved it: $58.50

<!--
- Say: Hands-free debugging demo. The agent ran eShopOnWeb, reproduced a wrong cart total through the UI, confirmed the cause under the debugger, fixed it, ran tests, and checked the UI again.
- The bug: with quantity 3, the cart total was wrong. Agent's finding on screen: "Cause: src\Web\Pages\Basket\BasketViewModel.cs:11 summed unit prices without multiplying by quantity. Runtime values were correctly 19.50 × 3, but the total expression returned 19.50."
- "Reproduced and confirmed under the debugger before editing." "With your approval, changed the total to include quantity." "Verified: build succeeded, all four targeted tests passed, and the storefront now shows 58.50 for both line cost and grand total."
- The tool log shows debugger tools: debugger_ui_tree, debugger_ui_interact, "Debugger evaluated expressions", "Removed breakpoints", debugger_continue. Chat mode: Debugger, Interactive (Manual), GPT-6.1 Sol.
- Harshada (13:14): it relaunched the app, redid the repro steps, and confirmed "the update cart total is now correct". "this feature is available in our latest Insider". Insiders only.
- Why it matters: the agent shows evidence (runtime values, tests, UI result), not just a diff. That is the subtitle of the talk: "From a visible symptom to an evidence-backed fix".
- Source: 13:10-13:15 ET, transcripts 20261111-131003, 20261111-131203, 20261111-131403; shot 20261111/131523.
-->

---
layout: "shot"
image: "/shots/day2/131728.jpg"
time: "13:17"
---

# Connected diagnostics: start in Copilot CLI, continue in VS (coming soon)

<!--
- Say: For people who like other AI clients: start a performance investigation in Copilot CLI, then connect Visual Studio and continue with its profiler. Not shipped yet.
- Harshada (13:16): "you can bring in Visual Studio along with your existing client and have that connected diagnostics experience." "I'm going to use the AHP to connect the Visual Studio to the client". (Agent Host Protocol per the stream agent; she said "AHP".)
- Demo: SharpZipLib, benchmark Adler32LargeUpdate. The CLI did a static analysis first (on screen: "measures a single checksum pass over 256 MiB", call path Update(byte[]) → Update(ArraySegment...)). Then a `launch-vs` prompt from a CLI plugin connects VS.
- Status: "this particular experience is not out yet. It is coming soon." Later (13:27): "The AHP is still internal".
- Why it matters: VS's profiler and debugger become tools any agent client can call, not only the VS chat.
- Source: 13:16-13:17 ET, transcript 20261111-131603; shot 20261111/131728.
-->

---
layout: "shot"
image: "/shots/day2/132254.jpg"
time: "13:22"
---

# Profiler agent result: Adler32 27.9% faster on .NET 6, 13.0% on .NET Framework

<!--
- Say: The connected demo ended with the VS profiler agent finding and fixing a hot loop in SharpZipLib. Same Release benchmark: 27.9% less time on .NET 6, 13.0% on .NET Framework 4.8.1.
- On screen (Copilot CLI, after VS profiling):
  - .NET 6.0.36: 159.385 ms → 114.965 ms, 27.9% time reduction.
  - .NET Framework 4.8.1, net462 target: 149.235 ms → 129.858 ms, 13.0%.
  - The change: accumulate four byte-position sums, then apply weighted arithmetic once per 3,800-byte block instead of per group. "The block limit, tail handling, and public API remain unchanged." "All four focused correctness tests passed".
- Harshada (13:21): "after the profiler agent ... we are able to see almost 27 percent of optimization for the .NET 6 and then for the other .NET framework ... 13 percent".
- Status: the CLI-to-VS connection is "not out yet"; she said "The AHP is still internal". So: demo of a coming feature.
- Why it matters: the agent changed an algorithm in a real open-source library, measured it on two runtimes, and kept the tests green.
- Source: 13:20-13:28 ET, transcripts 20261111-132003, 20261111-132204, 20261111-132600; shot 20261111/132254.
-->

---
layout: "session"
num: 6
time: "1:31 PM"
speakers: "Daniel Roth"
---

# Blazor Server in .NET 11: Fast, resilient, and scalable

<!--
- [session 06] Daniel Roth. Started about 1:31 PM ET.
- His frame: render on the server to "deliver more with less": faster loads (HTML ready to display), logic close to data, efficient requests (complete them, cache public content). Slide "Render on the server: Deliver more with less" (shot 20261111/133141).
- Blazor modes, his words: static SSR renders HTML "and then completes the HTTP request. There's no persistent connection." Interactive server keeps state in "a circuit" over "a persistent real-time connection". WebAssembly for client-side work and offline; it can be pre-rendered too.
- Source: 13:31-13:33 ET, transcripts 20261111-133001 and 20261111-133203; dotnetconf.net/agenda (1:30 PM ET).
-->

---
layout: "shot"
image: "/shots/day2/133353.jpg"
time: "13:33"
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
time: "13:49"
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
time: "13:52"
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
layout: "session"
num: 7
time: "2:00 PM"
speakers: "Stephen Halter"
---

# What's new in the MCP C# SDK

<!--
- [session 07] Stephen Halter, a developer on the .NET team who worked a lot on ASP.NET Core with Dan Roth. A demo-heavy session.
- His MCP intro (14:01): MCP is the Model Context Protocol, "essentially a way to plug in agents into your software in a reusable way." He said it became popular around the end of 2024.
- First demo: a fireworks control tool.
- Source: 14:00-14:02 ET, transcript 20261111-140003; dotnetconf.net/agenda (2:00 PM ET).
-->

---
layout: "shot"
image: "/shots/day2/140353.jpg"
time: "14:03"
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
time: "14:05"
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
time: "14:11"
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
time: "14:21"
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
time: "14:25"
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
num: 8
time: "2:31 PM"
speakers: "Niels Laute, Morten Nielsen"
---

# Building great Windows apps with WinUI and agents

<!--
- [session 08] Niels Laute and Morten Nielsen. Started about 2:31 PM ET.
- Source: 14:30-14:31 ET, transcript 20261111-143000; dotnetconf.net/agenda (2:30 PM ET).
-->

---
layout: "shot"
image: "/shots/day2/143502-crop.jpg"
time: "14:35"
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
time: "14:39"
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
time: "14:47"
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
time: "14:51"
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
num: 9
time: "3:01 PM"
speakers: "Daniel Roth"
---

# Building the future of agentic UI with Blazor

<!--
- [session 09] Daniel Roth, his second session today (after Blazor Server at 1:31 PM). Started about 3:01 PM ET.
- Source: dotnetconf.net/agenda (3:00 PM ET); stream agent session marker at 3:01 PM ET.
-->

---
layout: "shot"
image: "/shots/day2/150736.jpg"
time: "15:07"
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
time: "15:17"
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
time: "15:25"
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
time: "15:26"
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
num: 10
time: "3:31 PM"
speakers: "Manodasan Wignarajah, Sergio Pedri"
---

# CsWinRT 3.0: Modernizing the Windows Projections for .NET

<!--
- [session 10] Manodasan Wignarajah and Sergio Pedri. Started about 3:31 PM ET.
- STATUS: CsWinRT 3.0 is in PREVIEW. Sergio (15:53): "all of these is currently in preview". The NuGet and Windows SDK packages came out this week as previews; the WinUI / Windows App SDK multi-target package is "an internal package at the moment, but we're hoping to get this out very soon."
- Source: dotnetconf.net/agenda (3:30 PM ET); stream agent session marker.
-->

---
layout: "shot"
image: "/shots/day2/153441.jpg"
time: "15:34"
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
time: "15:44"
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
time: "15:48"
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
time: "15:57"
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
num: 11
time: "4:03 PM"
speakers: "Mika Dumont"
---

# GitHub Copilot modernization

<!--
- [session 11] Mika Dumont. Started about 4:03 PM ET.
- Jason pointed here this morning: "if you're a little bit worried about making the jump from one of the older versions of .NET, like .NET 8 or .NET 9, to .NET 11, you should check out Mika's section on the Modernization agent."
- Source: dotnetconf.net/agenda (4:00 PM ET); transcript 20261111-122404 for Jason's pointer.
-->

---
layout: "shot"
image: "/shots/day2/160738-crop.jpg"
time: "16:07"
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
num: 12
time: "4:30 PM"
speakers: "Gerald Versluis"
---

# Beyond Code Generation: Give AI Eyes and Hands for .NET MAUI

<!--
- [session 12] Gerald Versluis. Started about 4:30 PM ET.
- Warm-up from the host just before (16:28): he built MAUI apps "using agentic tools for Maui development" after a fitness app raised its price. A bike app "using the native maps, it's using Bluetooth, it's integrating in with my stationary bike", with a "Mario Kart mode" and a zombie-chase mode; and a breathing/mindfulness app on his phone using "MAI speech models". His point: MAUI "looks cool, but it's a little complicated. I'm telling you now, it's not." (The stream agent names the host Jon; the transcript does not say his name here.)
- Source: dotnetconf.net/agenda (4:30 PM ET); host segment transcript 20261111-162801.
-->

---
layout: "shot"
image: "/shots/day2/163719.jpg"
time: "16:37"
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
- MAUI Sherpa (16:38), not in maui-labs: a visual tool "built by Jonathan on our team" (last name not said here. (Inference) Likely Jonathan Dick (Redth), the author of Mobile Canvas, which Gerald introduced as "another cool thing by my good friend Jonathan". Not Jonathan Peppers. Confirm before you name him.) It sets up Android SDK and Xcode, checks .NET SDKs, handles certificates, builds, uploads to app stores, manages secrets: "mission control for mobile development". Not only for MAUI apps.
- Why it matters: agents read the real UI state of iOS and Android apps instead of guessing from screenshots. (Inference) It parallels winapp for WinUI from earlier today.
- Source: 16:34-16:43 ET, transcripts 20261111-163402, 20261111-163604, 20261111-163803, 20261111-164204; shots 20261111/163719 and 164314.
-->

---
layout: "shot"
image: "/shots/day2/165242.jpg"
time: "16:52"
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
