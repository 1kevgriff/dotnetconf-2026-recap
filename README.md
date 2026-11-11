# .NET Conf 2026 Recap

A [Slidev](https://sli.dev) deck of Day 1 highlights from .NET Conf 2026
(2026-11-10), by Kevin Griffin. It was built live while the stream ran.
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
```

For `npm run export`, approve the Playwright install script first:

```bash
npm install-scripts approve playwright-chromium
```

### Solo

`solo.yml` defines three commands: `Slidev` (dev server, auto-start),
`Build`, and `Export PDF`. Trust them in the Solo UI before the first run.

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

## Layout

```text
slides/
  slides.md      the deck
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
