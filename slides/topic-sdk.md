---
theme: default
title: .NET Conf 2026 Recap - The SDK, build and security
info: |
  ## .NET Conf 2026 Recap - The SDK, build and security
  Kevin Griffin - Microsoft MVP
  CLI, MSBuild, file-based apps, security, post-quantum crypto: highlights from Day 1 (2026-11-10) and Day 2 (2026-11-11), captured live.
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

- The SDK, build and security
- Kevin Griffin
- Microsoft MVP

<!--
- [title]
- Say: This is a .NET Conf 2026 recap on one topic: CLI, MSBuild, file-based apps, security, post-quantum crypto. It pulls the highlights from Day 1 (2026-11-10) and Day 2 (2026-11-11), captured live from the stream.
- Sessions in this deck:
  - 01 From the keynote: a faster CLI and build (Day 1, 11:00 AM)
  - 02 Moving `dotnet` Ahead (of Time)! (Day 1, 1:00 PM)
  - 03 More Processes, More Problems: Multithreaded MSBuild (Day 1, 3:30 PM)
  - 04 2 Secure 2 Curmudgeonly (Day 1, 4:30 PM)
  - 05 Post-Quantum Cryptography with .NET 11 (Day 1, 7:00 PM)
  - 06 C# File-based apps turned up to 11! (Day 2, 6:32 PM)
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

# From the keynote: a faster CLI and build

<!--
- [Session 01 · part of the Day 1 keynote] 11:00 AM ET, 2026-11-10.
- Say: The Day 1 keynote was a one-hour tour of .NET 11. These slides are the keynote parts about CLI, MSBuild, file-based apps, security, post-quantum crypto.
- Next slides: The .NET CLI on Native AOT, and MSBuild `-mt`.
-->

---
layout: "shot"
image: "/shots/111728.jpg"
time: "Day 1 · 11:17"
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
time: "Day 1 · 11:18"
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
layout: "session"
num: 2
time: "Day 1 · 1:00 PM"
speakers: "Chet Husk"
---

# Moving `dotnet` Ahead (of Time)!

<!--
[Session 02 · Day 1]
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
time: "Day 1 · 13:02"
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
time: "Day 1 · 13:09"
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
time: "Day 1 · 13:11"
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
num: 3
time: "Day 1 · 3:30 PM"
speakers: "Chet Husk"
---

# More Processes, More Problems: Multithreaded MSBuild

<!--
[Session 03 · Day 1] Keynote already has the `-mt` slide (−37% warm incremental on OrchardCore); add only new details.
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
time: "Day 1 · 15:33"
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
time: "Day 1 · 15:43"
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
num: 4
time: "Day 1 · 4:30 PM"
speakers: "Barry Dorrans"
---

# 2 Secure 2 Curmudgeonly

<!--
[Session 04 · Day 1] .NET security.
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
time: "Day 1 · 16:36"
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
time: "Day 1 · 16:51"
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
time: "Day 1 · 16:55"
---

# Aspire's first CVEs shipped on Day 1 — patch it

<!--
- Say: If you use Aspire, update today. Its first four CVEs were patched the morning of 2026-11-10.
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
time: "Day 1 · 16:56"
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
num: 5
time: "Day 1 · 7:00 PM"
speakers: "Jeremy Barton"
---

# Post-Quantum Cryptography with .NET 11

<!--
[Session 05 · Day 1] Agenda time 7:00 PM ET; started ~7:02.
- Jeremy Barton owns the cryptography layer in .NET (joked he owns a big share of "the unsafe code in .NET" because of it)
- Why PQC (19:02): "cryptography is just math"; the worry is "asymmetric cryptography, where you have a private key" and a public key — "you don't want anyone with the public key to be able to compute the private key". "Quantum computers change what problems we consider to be hard in mathematics."
-->

---
layout: "shot"
image: "/shots/190709.jpg"
time: "Day 1 · 19:07"
---

# "Harvest Now, Decrypt Later"

<!--
- Say: The urgent problem isn't signatures — it's key establishment. Traffic recorded today can be decrypted once a quantum computer exists.
- Two asymmetric buckets (stream slide): Signing (integrity, accountability) — "No significant retroactive threat", but "Erodes trust on 'Q day'". Key establishment (confidentiality) — "Harvest Now, Decrypt Later", "Old secrets revealed"
- "In crypto land we talk about Q-Day, which is the day that there's a ... cryptographically" relevant quantum computer
- Key establishment "is so big of a problem it has a pithy name now, which is Harvest Now, Decrypt Later": anything sent with a key establishment message can be recorded now and opened later
- Why it matters: data with a long secrecy life needs post-quantum key establishment before Q-Day, not after.
- Source: 19:06–19:08 ET, transcript 20261110-190604, /shots/190709.jpg
-->

---
layout: "shot"
image: "/shots/190953.jpg"
time: "Day 1 · 19:09"
---

# New in .NET 11: Composite ML-KEM

<!--
- Say: .NET 10 already shipped post-quantum signatures and ML-KEM. .NET 11 adds Composite ML-KEM — a post-quantum key exchange paired with a traditional one.
- Composite ML-KEM (stream slide): "Uses ML-KEM along with a 'traditional' algorithm"; "Both must be compromised to reveal the secret"; "Like the TLS 1.3 Hybrid KEM, but different"
- Already in .NET 10 (19:08): three signature algorithms — ML-DSA, SLH-DSA ("which stands for something"), and Composite ML-DSA ("ML-DSA with something else") — plus ML-KEM for key establishment. TLS comes from Windows/OpenSSL/macOS: "our underlying providers that have TLS 1.3 added the TLS 1.3 hybrid KEM" — available on the platform, "but it's not a thing that we have that you can directly call"
- "In 10, we added the composite ML-DSA algorithm, and in 11 we're now adding composite ML-KEM."
- Why it matters: belt and suspenders — if either the new or the old algorithm turns out weak, the secret still holds.
- Source: 19:08–19:10 ET, transcript 20261110-190803, /shots/190953.jpg
-->

---
layout: "default"
codeSize: "18"
---

# Composite ML-KEM in code

```csharp
// 1. Import the recipient key
using (var recipientKey = CompositeMLKem.ImportEncapsulationKey(recip.Alg, recip.EncapsKeyBytes))
{
  // 2. Invoke the Key Encapsulation Mechanism
  recipientKey.Encapsulate(out ciphertext, out sharedSecret);
}

// 3. Send the ciphertext to the recipient.
Send(recip, ciphertext);

// 4. Derive a key (out of scope here)
byte[] aesKey = SomehowDeriveKey(sharedSecret);

// 5. Both sides share a key now.
using (AesGcm aesGcm = new AesGcm(aesKey, tagSizeInBytes: 16);
```

<!--
- Say: The initiator imports the recipient's encapsulation key, encapsulates to get a ciphertext and a shared secret, sends the ciphertext, and both sides derive the same AES-GCM key.
- Code copied from the stream slide "Composite ML-KEM - Initiator" (/shots/191123.jpg); `SomehowDeriveKey` is a placeholder on the slide ("out of scope here")
- Composite = an ML-KEM key plus "a thing that we call a traditional key, which will be RSA or" another classic algorithm; example algorithm "ML-KEM 1024 with RSA 4096"
- "Since it's called the key encapsulation mechanism, the public key is called the encapsulation key."
- Why composites: we don't fully trust ML-KEM yet, "but also at the same time we know that at some point we're going to completely stop trusting RSA" — "the composites are a bit of a stopgap"
- Why it matters: you can start post-quantum key establishment now without betting everything on a brand-new algorithm.
- Source: 19:10–19:12 ET, transcript 20261110-191003, /shots/191123.jpg
-->

---
layout: "shot"
image: "/shots/191402.jpg"
time: "Day 1 · 19:14"
---

# New in .NET 11: HPKE (post-quantum suites in 11.0.x)

<!--
- Say: .NET 11 also adds HPKE — Hybrid Public Key Encryption — which bundles the pieces people usually get wrong. Its post-quantum suites arrive in an 11.0.x servicing update, not in 11.0.0.
- HPKE = IRTF RFC 9180 and updates (stream slide). "Combines pieces so you don't have to": public key establishment, nonce/IV management, AE tag verification, message ordering enforcement
- Jeremy (19:14): it handles the things "that people tend to get wrong"; "nonce management, which is really important for something like GCM"; message ordering — "if you get them out of order ... it says it's been tampered with and then it fails"
- "Designed as a message stream"; "also supports 'one-shot' operations" for people who "only want to send just one message"
- Keys come together in "a thing called a suite" (the notes agent: KEM + KDF + AEAD)
- Receiver side (19:18): open the message — "If any part of it was tampered with, this will fail. If you send it back in the wrong order, this will fail. So by the time that you get it now, you know it's trustworthy."
- Also: EnvelopedCms ("we've had that for now, I want to say 21 years. It can drink.") now supports ML-KEM. You need an ML-KEM key as the subject key of a certificate (e.g. an email cert, not a CA); address it to their cert and "we'll do all the plumbing inside for you"
- ⚠ HPKE in 11.0.0 is NOT post-quantum yet (19:20): support for the PQ HPKE draft — "the PRs up for main, I didn't finish reviewing it before we went into schedule lockdown. We'll get it in servicing."
- "The Near Future — Expected in 11.0.x, x > 0" (stream slide /shots/192033.jpg): ML-KEM in HPKE and Hybrid ML-KEM + Traditional in HPKE (draft-ietf-hpke-pq); Composite ML-KEM in EnvelopedCms (draft-ietf-lamps-cms-composite-kem)
- Hybrid ML-KEM in HPKE "isn't composite ML-KEM, it's hybrid ML-KEM like with TLS 1.3" — same idea, different spec
- Why ship it this way: "make a lot of things work okay or a few things work really well. And we opted to make a few things work really well because we can fix it later."
- Further out (19:22): much of the PQ API "has the good old experimental tag on it"; if a spec changes, "it will be a breaking change". "Last Friday the composite ML-KEM spec I think finally went full RFC" — "for .NET 12 we should be able to remove a lot of the experimentals"
- Jeremy's ask (19:26): "all of these protocols need to start accepting multiple keys" (instead of more and more composite combinations)
- Q&A on composites: "it doesn't matter that somebody can break the EC Diffie-Hellman. They would need to break that piece also" — "you take the two pieces and you merge them together in a way that they're inseparable"
- Why it matters: use HPKE instead of wiring key exchange + AES-GCM + nonces by hand.
- Source: 19:14–19:16 ET, transcript 20261110-191402, /shots/191402.jpg
-->

---
layout: "session"
num: 6
time: "Day 2 · 6:32 PM"
speakers: "Damian Edwards"
---

# C# File-based apps turned up to 11!

<!--
- [Session 06 · Day 2] Damian Edwards. Started about 6:32 PM ET.
- Context: Reactor (Day 2, in the Desktop and mobile deck) already showed a whole WinUI app as one C# file run with `dotnet run`.
- Source: dotnetconf.net/agenda (6:30 PM ET); stream agent session marker.
-->

---
layout: "shot"
image: "/shots/day2/183539.jpg"
time: "Day 2 · 18:33"
---

# One C# file, no project: `dotnet hello.cs` (no `run` needed)

<!--
- Say: File-based apps let you run a single .cs file with no project. You don't even need `run`: `dotnet hello.cs` works.
- Damian (18:32): "there's no slides. We're just going to look at code today." He covers file-based apps from .NET 10, through "the feature band releases, like 10.0.300 and 10.0.400, and then some of the brand new stuff that has now landed in 11.0.100."
- On screen: hello.cs is two lines (127 bytes): `var name = args.Length == 0 ? ".NET Conf" : string.Join(" ", args);` and `Console.WriteLine($"Hello, {name}! One file. Real C#.");`. Then `dotnet run hello.cs`, `dotnet hello.cs`, and `dotnet hello.cs Damian` → "Hello, Damian! One file. Real C#." The prompt shows .NET 11.0.100.
- "you don't have to say dotnet run. You can just say dotnet hello.cs, and that also works."
- Prompt timings on screen (the prompt shows the previous command's time): `dotnet run hello.cs` 1.412 s, then `dotnet hello.cs` 131 ms. One run each; (Inference) the first includes a build and the second reuses it.
- Explicit form (18:34): `dotnet run --file hello.cs -- ".NET Conf 2026"` — "very explicitly saying, I want you to run this file ... I am telling you this is a C# file", and `--` separates app arguments. Useful in scripts.
- From stdin: `'Console.WriteLine("hello from stdin");' | dotnet run -` → "hello from stdin". "you can actually execute C# code from standard in."
- Source: 18:32-18:36 ET, transcripts 20261111-183204 and 20261111-183404; shot 20261111/183539 (shows all forms).
-->

---
layout: "shot"
image: "/shots/day2/183806.jpg"
time: "Day 2 · 18:37"
---

# Full C#, virtual project, cached build: 973 ms → 107 ms

<!--
- Say: A file-based app is real C# with a project that is just virtual, so you get IntelliSense. And the .NET SDK caches the build, so a re-run skips work it does not need.
- Damian (18:36): "It's not C# scripting. It is not C# interactive ... CSX. This is full-fat C#. It's just that the project is virtual." "Yes, I get IntelliSense here."
- Caching: "we've actually done a bunch of work in file-based apps in the .NET SDK to implement build caching." His measure-launch.ps1 script ran hello.cs in different cache states. "for an uncached build, you can actually disable the cache by passing --no-cache".
- On screen, median table (5 runs each, .NET 11.0.100): uncached build 972.9 ms; fresh output 370.6 ms; directive change 1048.4 ms; source change 353.6 ms; no changes 106.7 ms. Footer: "Same SDK and command, different source/output/cache state. Build servers are pre-warmed; packages may already be cached."
- What the modes mean (18:38): uncached = `--no-cache`, "the equivalent of a dotnet build or a dotnet run on a traditional csproj", "about a second on this machine". Fresh output = hello.cs copied to a new folder each time, which "breaks our build cache key" (a hash of the entry file path plus the SDK version, etc.). It is still fast because the file has no directives: "We actually completely skip invoking MSBuild if it's just C# ... we just run the compiler." Directive change = a #: directive changed, so MSBuild runs again.
- Say: a re-run with no changes is about 107 ms; editing plain C# about 354 ms; only directive changes pay the full ~1 s.
- Source: 18:36-18:39 ET, transcripts 20261111-183600 and 20261111-183801; shot 20261111/183806.
-->

---
layout: "shot"
image: "/shots/day2/184157.jpg"
time: "Day 2 · 18:41"
---

# `#:include`: file-based apps can now span more than one file

<!--
- Say: New since .NET 10: `#:include` pulls other C# files into a file-based app, so a "single-file" app can grow without a project file. Directives also add NuGet packages, and a shebang makes it a script.
- On screen (demos/02-tool/plan.cs, VS Code, status bar "plan (net11.0)"): line 1 `#!/usr/bin/env -S dotnet --`; line 2 `#:include SessionPlan.cs`; line 3 `#:package Spectre.Console@0.57.2 PrivateAssets=all`; then `using Spectre.Console;` and a table built from `SessionPlan.Load()`.
- Damian (18:41): features that are "newer, thanks to the work that's happened since we released .NET 10. The big one here is this include directive. Now I can now include other C# files in my file."
- Transitive (18:42): "we support transitive directive processing." plan.cs includes SessionPlan.cs, which includes helpers/DurationLabel.cs, which has its own `#:package Humanizer.Core@2.14.1` (shot 20261111/184228).
- Package versions: "I can put a star here ... That's the float syntax ... 2.14.* and that will float to the latest patch"; central package management works too.
- Includes: Dev Kit gives "completion for file paths", and "you can do globs in here. They don't have to be specific files."
- CAVEAT (18:44): a glob in `#:include` "invalidates our build cache ... We don't at the moment support expanding that glob before we pass it to MSBuild ... do note that it will disable the build caching". Use explicit file names if run speed matters.
- New in .NET 11: metadata on directives. "up until 11, we didn't support metadata on directives." Now `#:package Spectre.Console@0.57.2 PrivateAssets=all` works, as in a project file; important for some packages such as analyzers or build tools ((Inference) the examples he alluded to).
- Cache recap (18:40): a source-only change can "just do that recompilation phase"; with no changes you get down "to like 100 millisecond execution times".
- Source: 18:40-18:45 ET, transcripts 20261111-184002, 20261111-184203, 20261111-184404; shots 20261111/184157 and 184228.
-->

---
layout: "shot"
image: "/shots/day2/184850.jpg"
time: "Day 2 · 18:46"
---

# A web app in one file, plus new `#:ref` to reuse another file-based app (.NET 11)

<!--
- Say: File-based apps can be web apps. Settings and launch settings are sidecar files named after the app: web.cs reads web.settings.json (like appsettings.json) and web.run.json (like launchSettings.json).
- Damian (18:46): "You can absolutely build web applications". The settings file is "just named after your application. So if my application was called foo.cs, this would be called foo.settings.json ... That will be implicitly read by the web host". "my web.run.json file here is just my launch settings file", which in a project "would be called launchSettings.json".
- web.cs directives (on screen, shot 20261111/184850): `#!/usr/bin/env -S dotnet --`, `#:sdk Microsoft.NET.Sdk.Web`, `#:ref ../02-tool/plan.cs`, `#:project ../../projects/ConferenceBrand/ConferenceBrand.csproj`; then `WebApplication.CreateSlimBuilder(args)` and a `MapGet("/")` that prints Brand.Name, SessionPlan.Summary() and "The CLI's Main did not run. Its public types are reusable."
- `#:sdk` (18:48): "This allows you to reference an MSBuild SDK", here "Microsoft.NET.Sdk.Web". "You can also do NuGet-based SDK", e.g. a Cake build script with the Cake SDK, which brings in "implicit references that you don't have to see".
- `#:ref` is NEW IN .NET 11 (18:50): "Here is a new directive in .NET 11. This is an app-to-app reference directive ... Hash colon ref lets me reference another file-based app." plan.cs "will get imported into the virtual project"; its public types are usable, its Main does not run. `#:project` references a normal .csproj. And "I can build my own SDKs like we saw for Cake here. And then you can distribute those on NuGet".
- Earlier run (shot 20261111/184644): `dotnet web.cs` → "Using launch settings from ...web.run.json" and "Now listening on: http://webfba.dev.localhost:5111".
- Source: 18:46-18:51 ET, transcripts 20261111-184604, 20261111-184800, 20261111-185001; shots 20261111/184644 and 184850.
-->

---
layout: "shot"
image: "/shots/day2/185354.jpg"
time: "Day 2 · 18:53"
---

# .NET 11: the whole SDK CLI understands file-based apps

<!--
- Say: In .NET 10 only build, restore, run and publish really understood file-based apps. In .NET 11 the team went through the SDK commands, so things like `dotnet format` and `dotnet package list --outdated` now work on a single .cs file.
- Damian (18:51): "in .NET 11, we did a lot of work in the .NET SDK to go through all of the commands". "When we first launched our file-based apps in .NET 10 ... It was really only dotnet build, dotnet restore, dotnet run, and dotnet publish that really understood" them.
- Demo: `dotnet format` on a file-based app; `dotnet package list --file packages.cs`, then `--outdated` → "Project `packages.cs` has the following updates to its packages [net11.0]: Humanizer.Core requested 2.14.1, resolved 2.14.1, latest 3.0.10"; then `--vulnerable`.
- dotnet-outdated (18:54): "I updated dotnet outdated to support file-based apps": `dotnet outdated packages.cs`, or enable file-based apps and it "will do the entire workspace recursively". ((Inference) dotnet-outdated is a community global tool, not part of the SDK.)
- Why it matters: file-based apps get the same maintenance tools as projects: formatting, outdated and vulnerable package checks.
- Source: 18:51-18:55 ET, transcripts 20261111-185001, 20261111-185204, 20261111-185400; shot 20261111/185354.
-->

---
layout: "shot"
image: "/shots/day2/185525.jpg"
time: "Day 2 · 18:55"
---

# Shebang: a .cs file becomes a Unix command

<!--
- Say: Add `#!/usr/bin/env -S dotnet --` as the first line, mark the file executable, and on Linux or macOS the .cs file runs like any other command.
- On screen (demos/05-unix/session.cs): line 1 `#!/usr/bin/env -S dotnet --`; `--help` prints "session [name] - a C# source command on your PATH"; otherwise "Hello from Linux, {name}. This command is C# source."
- Damian (18:55): "a shebang is a shell instruction that is supported on Unix or Unix-like systems ... Mac and ... Linux", or a Linux-like shell on Windows; "if this file is marked as executable", the shell uses the `env` command to start `dotnet` with the file. Demo in WSL.
- Demo (18:56): the file was "not currently executable"; `chmod +x`, then run it directly: "I didn't have to say dotnet." An extensionless `session` file is "a symlink to session.cs ... they're both marked executable", so with that folder on PATH you type `session`. The live PATH step failed on stream ("that one's not going to work today"); say it is the intended setup, not what was shown working.
- Extensionless (18:58): "we did do the work to support extension-less files ... if you have a file and it has a shebang at the front of it, you can invoke it directly even if it doesn't end in .cs ... we will look inside of it, verify it has the shebang".
- What's next: C# Dev Kit "ships every month"; file-based apps update with SDK feature bands: "look for 11.0.200 to come out early next year, and we may be polishing this experience even further".
- Q&A: stdin mode (`dotnet run -`) "by design is fully isolated ... we don't pick up on NuGet config. We don't pick up on Directory.Build.props or Directory.Build.targets" — which normal file-based apps do support "as long as they're in ... the file system scope". (Inference) So for private feeds, use a file on disk, not stdin.
- How it works (Q&A, 19:01): for every command the SDK runs shared logic: "synthesize a virtual project", "parse the directives", "look at the build cache", "make a decision about whether I invoke MSBuild". Output goes "to a temporary location": "we create a folder under temp based on that hash" of the file path "plus a few other things ... as a cache key". Directory.Build.props/targets are included in the build cache too.
- Close (19:02): file-based apps honor the artifacts output setting ("all my projects to output to a folder at the root called artifacts"). His measure script: "I asked Copilot before we came in here to create it in C#, and it did in one shot, and that meant I could run it from Linux as well." The demo repo will be "just under my GitHub".
- Chat aside: Mattias said Cake 7.0 just came out.
- Source: 18:54-19:02 ET, transcripts 20261111-185400 to 20261111-190203; shot 20261111/185525.
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
