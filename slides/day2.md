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
- Questions during the day: #questions in chat, or dotnetconfquestions.com (on the stream lower third).
- Source: 11:00-11:01 ET, transcript 20261111-110002; title card shot 20261111/110122.
-->

---
layout: "statement"
---

Code is an asset, not a byproduct.

<!--
- Say: Mads's positioning for Visual Studio: it targets professional developers, and professionals treat code as an asset.
- His words (11:02): "Visual Studio is a little bit unique in that it targets specifically professional developers." Professionals have "quality gates ... accessibility, security, privacy".
- On vibe coding: "you might not care about your code that much, you might not even look at it. That's fine for ... your hobby projects". But for professionals, "You want to be able to review it ... maintain it for years to come ... It's not a byproduct of the app that you're building, but it has value in itself."
- Why it matters: this is the frame for every AI feature shown today: AI in VS should give code you can review and maintain, not throwaway output.
- Source: 11:02 ET, transcript 20261111-110200; slide "Visual Studio is for professional developers" (shot 20261111/110215).
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
- Why it matters: a failed build in a big solution now fails in seconds, for people and for agents.
- (Inference) The release is 18.12; Mads showed this right after the 18.12 performance list. Check the release notes for the exact option name.
- Source: 11:08-11:09 ET, transcript 20261111-110804; shot 20261111/110839.
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
