# .NET Conf 2026 Recap

Two [Slidev](https://sli.dev) decks of highlights from .NET Conf 2026,
by Kevin Griffin: Day 1 (`slides/slides.md`, 2026-11-10) and Day 2
(`slides/day2.md`, 2026-11-11). It was built live while the stream ran.
Each session from the agenda has its own part, with short headlines on the
slides and the details in the presenter notes.

## Run it

Needs Node.js 22.12 or later.

```bash
cd slides
npm install
npm run dev      # http://localhost:3030, opens a browser
npm run build    # static SPA in slides/dist
npm run export   # PDF, needs playwright-chromium

npm run dev:day2     # Day 2 deck, http://localhost:3031
npm run build:day2   # static SPA in slides/dist/day2
npm run export:day2  # Day 2 PDF
```

For `npm run export`, approve the Playwright install script first:

```bash
npm install-scripts approve playwright-chromium
```

### Solo

`solo.yml` defines five commands: `Slidev` and `Slidev Day 2` (dev
servers, auto-start), `Build`, `Build Day 2`, and `Export PDF`. Trust them in the Solo UI before the first run.

## What is in the deck

| # | Session | Speakers |
|---|---|---|
| 01 | Keynote: .NET 11 ships | Scott Hanselman, Damian Edwards + guests |
| 02 | What's new in C# | Mads Torgersen, Dustin Campbell |
| 03 | Modern web development with ASP.NET Core & Blazor in .NET 11 | Daniel Roth |
| 04 | Moving `dotnet` Ahead (of Time)! | Chet Husk |
| 05 | Why WinForms must not change — yet reinvented itself with .NET 11 | Klaus Löffelmann |
| 06 | The .NET AI Stack | Luis Quintanilla |
| 07 | What's New in .NET MAUI in .NET 11 | Gerald Versluis |
| 08 | C# Dev Kit 11 | Drew Noakes, Emanuel Fernandez Dell'Oca |
| 09 | More Processes, More Problems: Multithreaded MSBuild | Chet Husk |
| 10 | What's New in Aspire for .NET Developers | Maddy Montaquila, Damian Edwards |
| 11 | 2 Secure 2 Curmudgeonly | Barry Dorrans |
| 12 | Beyond Autocomplete: Getting the Most from GitHub Copilot for .NET | Wendy Breiding |
| 13 | .NET 11 Numerics | Tanner Gooding |
| 14 | How Aspire uses .NET to build an agent-first toolchain for any language | Maddy Montaquila, Jose Perez Rodriguez |
| 15 | .NET Runtime vNext: Memory Safety and Runtime Async | Richard Lander, Andy Gocke |
| 16 | Post-Quantum Cryptography with .NET 11 | Jeremy Barton |
| 17 | Bringing `dotnet run`, `test`, and `watch` to .NET MAUI | Jonathan Peppers |

Day 1 is complete: all 17 agenda sessions, 159 slides.

### Day 2 (2026-11-11, Microsoft product team day): `slides/day2.md`

| # | Session | Speakers |
|---|---|---|
| 01 | Keynote: Visual Studio Now and Next | Mads Kristensen |
| 02 | The State of AI in Visual Studio: New Brain. More Choice. | Rachel Kang, Barbara Boyajian |
| 03 | What's new in Visual Studio | Jason Chlus |
| 04 | Get the most out of Version Control in Visual Studio 2026 | Sebastian Hernandez |
| 05 | What's New in Visual Studio Diagnostics | Harshada Hole |
| 06 | Blazor Server in .NET 11: Fast, resilient, and scalable | Daniel Roth |
| 07 | What's new in the MCP C# SDK | Stephen Halter |
| 08 | Building great Windows apps with WinUI and agents | Niels Laute, Morten Nielsen |
| 09 | Building the future of agentic UI with Blazor | Daniel Roth |
| 10 | CsWinRT 3.0: Modernizing the Windows Projections for .NET | Manodasan Wignarajah, Sergio Pedri |
| 11 | GitHub Copilot modernization | Mika Dumont |
| 12 | Beyond Code Generation: Give AI Eyes and Hands for .NET MAUI | Gerald Versluis |
| 13 | No XAML Required: Native Windows Apps in Pure C# | Alexandre Zollinger Chohfi |
| 14 | Azure's new lineup for .NET developers (Part 1) | Matt Soucoup, Paul Yuknewicz |
| 15 | Azure's new lineup for .NET developers (Part 2) | Matt Soucoup, Paul Yuknewicz |
| 16 | C# File-based apps turned up to 11! | Damian Edwards |
| 17 | .NET + Foundry: Better Together | Bruno Capuano |
| 18 | EF Core 11: Vector Search, Smarter LINQ, and a Friendlier dotnet ef | Jiri Cincura |

Day 2 is complete: all 18 agenda sessions, 127 slides. Its screenshots are
in `public/shots/day2/`. A surprise guest segment (likely Scott Hunter;
the name was not said on stream) sits between sessions 04 and 05.

## How it was made

- A separate agent watched the stream. It saved screenshots, transcripts
  and a running list of highlights.
- This deck took those highlights and added slides in near real time.
  Each change was committed and pushed to `main`.
- Each claim on a slide or in the notes was checked against the session
  transcript or the stream screenshot before it went in. Claims that
  could not be checked were left out or marked in the notes.

## Before you present

Read the presenter notes. They carry caveats you should say out loud, or
check first:

- Several AI APIs are experimental (`DocumentExtractionClient`,
  `RoutingChatClient`, Blazor AI Components). Confirm package
  availability.
- Android NativeAOT for MAUI is experimental. The p90 startup is still
  slow.
- MAUI 10 support ends May 2027.
- The Media Studio final video was prepared before the session, not
  rendered live.
- The "best AI demo" quote names only "Kevin". Confirm it was your post.
- A few speaker quotes were tidied for grammar. The notes say which.
- Runtime async: speakers said two different things about whether the .NET 11
  framework libraries use it. The slide avoids that claim; the notes quote
  both.
- Some stream frames carry a "Microsoft Confidential" footer. Those frames
  are not in this repo.

Day 2 caveats (details in the notes):

- Several VS features shown are Insiders-only, not in 18.12 stable: UI
  automation for Copilot/Debugger Agent, PerfTip and dump analysis with
  Copilot, managed settings (18.13 Insiders).
- "Roundtrip sessions from the CLI into VS" and connected diagnostics are
  coming, not shipped (speakers disagreed; the notes quote both).
- Three VS features are off by default: stop build on first failure,
  colorized output, hot exit.
- Experimental or preview: CsWinRT 3.0, Microsoft.UI.Reactor, maui-labs
  tools, Blazor AI components, MCP Skills package, Azure Functions Hosted
  Skills ("initial concept").
- EF Core 11 on SQL Server defaults to compatibility level 160; set it
  lower for older servers.
- Some demo frames showed user paths, subscription IDs, bookmarks or a
  password manager. Those frames were cropped or left out.

## Layout

```text
slides/
  slides.md      Day 1 deck (159 slides)
  day2.md        Day 2 deck (127 slides)
  layouts/       cover, session, section, statement, shot, default, code, ...
  components/    Badge, BigNum, Caption, Card, Panel, ...
  public/shots/  stream screenshots used on slides
  styles/        theme CSS and fonts
solo.yml         Solo commands
```

The theme comes from an earlier talk. Two layouts are new for this deck:

- `session`: gold divider for each conference session (`num`, `time`,
  `speakers`).
- `shot`: one headline plus a stream screenshot (`image`, `time`).

## Credits

Screenshots and quotes are from the public .NET Conf 2026 stream by
Microsoft and the speakers named above. Agenda:
<https://www.dotnetconf.net/agenda>.
