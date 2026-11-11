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

# Copilot checks its own fix by driving your running app

<!--
- Say: Copilot in VS can now run your app, go to the bug, and check that its fix works. The slide calls it "UI Automation > hands free debugging".
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
- Why it matters: profiling and dump analysis were expert-only work. Now you can ask in chat.
- Source: 11:18-11:19 ET, transcript 20261111-111805; slide "Your running application" (shot 20261111/111935).
-->

---
layout: "shot"
image: "/shots/day2/112553.jpg"
time: "11:21"
---

# Start in the CLI, move the session into VS for the debugger

<!--
- Say: You can move a Copilot chat session from the CLI, VS Code or the Copilot app into Visual Studio, and keep going with VS tools.
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
- He asked the audience: what do you let AI do in version control, and what not?
- Why it matters: bulk resolve fixes a long-time pain; Auto Resolve is the first AI step inside the merge flow.
- Source: 12:44-12:46 ET, transcripts 20261111-124404 and 20261111-124603; shot 20261111/124514.
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
