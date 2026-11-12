---
theme: default
title: .NET Conf 2026 Recap - C# and the .NET 11 runtime
info: |
  ## .NET Conf 2026 Recap - C# and the .NET 11 runtime
  Kevin Griffin - Microsoft MVP
  C#, the runtime, numerics: highlights from Day 1 (2026-11-10) and Day 2 (2026-11-11), captured live.
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

- C# and the .NET 11 runtime
- Kevin Griffin
- Microsoft MVP

<!--
- [title]
- Say: This is a .NET Conf 2026 recap on one topic: C#, the runtime, numerics. It pulls the highlights from Day 1 (2026-11-10) and Day 2 (2026-11-11), captured live from the stream.
- Sessions in this deck:
  - 01 From the keynote: .NET 11 and C# 15 (Day 1, 11:00 AM)
  - 02 What's new in C# (Day 1, 12:00 PM)
  - 03 .NET 11 Numerics (Day 1, 5:30 PM)
  - 04 .NET Runtime vNext: Memory Safety and Runtime Async (Day 1, 6:30 PM)
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

# From the keynote: .NET 11 and C# 15

<!--
- [Session 01 · part of the Day 1 keynote] 11:00 AM ET, 2026-11-10.
- Say: The Day 1 keynote was a one-hour tour of .NET 11. These slides are the keynote parts about C#, the runtime, numerics.
- Next slides: .NET 11 GA, TinyOS, C# 15 and unions, runtime async, memory safety v2.
-->

---
layout: "shot"
image: "/shots/110905.jpg"
time: "Day 1 · 11:09"
---

# .NET 11 is GA

<!--
- Released today. get.dot.net
- Damian Edwards: "five eras, one platform" (Windows, Web, Mobile, Cloud, AI)
- Say: Damian Edwards made it official: .NET 11 is available today. Go to get.dot.net.
- Verbatim (Damian): "I'd love to announce that .NET 11 is now available. It's rolling out now."
- Verbatim (Damian): "if you take anything away from .NET Conf this year, let it be that .NET is durable."
- The five-eras slide: 2002 Windows, 2008 Web, 2008 Mobile, 2016 Cloud, Today AI ("Agents write, test and review code alongside us").
- Damian on the cloud era: performance became a feature because "It cost real money when you were running it on someone else's computer."
- Why it matters: .NET 11 is the new current release. You can install it today.
- Source: 11:07-11:09 ET, 20261110-110505.txt; shots 110705.jpg, 110905.jpg.
-->

---
layout: "shot"
image: "/shots/110459.jpg"
time: "Day 1 · 11:04"
---

# 2002 homework OS, running on .NET 11

<!--
- Hanselman's TinyOS from .NET 1 days, updated and running on .NET 11
- The point: .NET code is durable
- Say: Scott Hanselman found the tiny operating system he wrote in .NET 1 as a college senior project, and brought it forward to .NET 11.
- He showed the original slides from TechEd Malaysia 2002. He called it a "virtual operating system" "all written in .NET 1".
- The "TinyOS Time Machine": power button, tiny floppy disks, live memory view, the original source, and a CRT glass effect. Verbatim: "still running my original homework."
- Verbatim (Hanselman, on .NET): "It's there. It's reliable. It's fast as heck."
- Fun extras: he has coded since 1984, his GitHub user ID is "under 3,000", and "It took me 11 years to get my four-year degree."
- Why it matters: code you wrote 24 years ago can still run on the newest runtime.
- Source: 11:02-11:06 ET, 20261110-110004.txt and 20261110-110505.txt; shot 110459.jpg.
-->

---
layout: "shot"
image: "/shots/110920.jpg"
time: "Day 1 · 11:09"
---

# C# 15

<!--
- Unions, closed hierarchies, collection arguments
- Labeled break, extension indexers
- Memory safety preview
- Say: Mads Torgersen's slide title was "C# 15: Cleaner, safer, faster." Unions are the headline feature.
- Union types: public union Pet(Dog, Cat); - exhaustive over the listed case types.
- Closed hierarchies: public closed class Pet; - a subclass from another assembly is an error.
- Collection arguments: HashSet<string> tags = [with(comparer), "one", "two", "three"]; - pass capacity or a comparer inline.
- Labeled break and continue ("break outer", no flag variables); extension indexers (index into types you don't own); memory safety preview (unsafe calls explicit and auditable).
- Why it matters: less boilerplate and more compiler checks in everyday C#.
- Source: 11:09 ET, shot 110920.jpg; 20261110-110505.txt.
-->

---
layout: "shot"
image: "/shots/111254.jpg"
time: "Day 1 · 11:12"
---

# Unions: add a case, every switch lights up

<!--
- union Pet(Dog, Cat, Bird, Hamster)
- Add Hamster: every non-exhaustive switch is flagged
- Say: Mads called unions "probably the most anticipated and requested" C# feature "for a long, long time." The demo shows why.
- Before: pets in a List<object>. No type safety, a Shark can sneak in, and the switch warns it is not exhaustive with no good fix.
- After: union Pet(Dog, Cat, Bird). The case types don't have to participate. Each case converts implicitly to Pet; other types don't. Matching on Shark is now an error, and the warning goes away.
- Verbatim (Mads): "ironically, with that warning going away, It sort of makes the warning useful again." Add Hamster and every consuming switch warns again: "this is now actionable."
- Verbatim (Mads): "clarity, safety, those are things that are great regardless of whether human or an agent are actually working on the code."
- Why it matters: you can model "one of these types" without a fake base class, and the compiler finds every place to update.
- Source: 11:10-11:13 ET, 20261110-110505.txt and 20261110-111004.txt; shot 111254.jpg. Deep dive: Mads + Dustin Campbell, 12:00 PM ET.
-->

---
layout: "shot"
image: "/shots/112046.jpg"
time: "Day 1 · 11:20"
---

# Runtime async: 0 bytes allocated

<!--
- No state machines, no ValueTask needed
- 0 B per op vs 216–504 B with state machines
- Default in .NET 12
- Say: Richard Lander showed runtime async. Your async code stays the same, but the compiler stops generating state machines and the JIT does the work.
- Opt in with an MSBuild Features property in .NET 11. Verbatim: "We expect it to be the default in .NET 12."
- Verbatim: "near-synchronous performance for async code, which is a claim that we've never been able to make before."
- Chart: 216 / 360 / 504 B per operation at 3 / 5 / 7 async frames with state machines; 0 B with runtime async. Synchronous-completion case. Benchmark: a C# port of Restic.
- Why it matters: free allocation savings in hot async paths, with no code changes.
- Source: 11:19-11:21 ET, 20261110-111503.txt and 20261110-112031.txt; shot 112046.jpg.
-->

---
layout: "shot"
image: "/shots/112220.jpg"
time: "Day 1 · 11:22"
---

# Memory safety v2: the Rust/Swift model, stricter

<!--
- Unsafe is off by default
- An unmarked unsafe call is an error
- Preview in .NET 11, GA in .NET 12
- Say: C# adopts the same unsafe-contract model as Rust and Swift, with near-identical syntax, but C# is the strictest of the three.
- Slide table: unmarked unsafe call - C# Error, Rust 2024 Error, Swift Warning. Unmarked op inside an unsafe member - C# Error, Rust and Swift Warning. Unsafe allowed by default - C# No, Rust and Swift Yes.
- Verbatim (Lander): "security is our top priority." He cited Microsoft's statement that "70% of vulnerabilities are due to memory safety issues."
- AllowUnsafeBlocks stays false by default, as since C# 1.0. New: unsafe expressions, so a method can expose a safe facade over unsafe code.
- Deep dive: Richard Lander + Andy Gocke. Agenda: 6:30 PM ET. (Lander said "3:30 PM" on stream; (Inference) that is Pacific time.)
- Why it matters: unsafe code becomes explicit and auditable, which helps security reviews.
- Source: 11:21-11:23 ET, 20261110-112031.txt and 20261110-112200.txt; shots 112116.jpg, 112220.jpg.
-->

---
layout: "session"
num: 2
time: "Day 1 · 12:00 PM"
speakers: "Mads Torgersen, Dustin Campbell"
---

# What's new in C#

<!--
[Session 02 · Day 1]
- Say: Session 2 is Mads Torgersen and Dustin Campbell on C# 15. Most of it is unions, plus a few smaller features.
- 12:00 PM ET. Speakers: Mads Torgersen, Dustin Campbell (both work on C#)
- Version rule from the stream: C# version = .NET version + 4, so C# 15
- Theme: let the compiler know the full set of types, so switches are exhaustive
- Next slides: unions (before/after demo, how they work), `closed` classes, collection expression args (`with(...)`), labeled break/continue, extension indexers, Q&A on closed vs union
- Wrap-up also named a memory safety preview and runtime async ("not different, just faster")
- Why it matters: C# 15 gives you safe closed sets of types without a class hierarchy or a discard arm.
- Source: 12:00–12:28 ET, transcripts 20261110-120000.txt to 20261110-122802.txt
-->

---
layout: "statement"
---

Unions: 18 years in the making.

<!--
- Say: Unions shipped in C# 15. Mads said the team talked about them when he joined Microsoft, about 18 years ago.
- 12:00 ET. Mads: "we were talking about it ... like 18 years ago"
- C# version = .NET version + 4, so C# 15
- Demo: Dog, Cat, Bird, Shark from libraries you don't own
- Verbatim (light cleanup): "when I joined Microsoft, now like 18 years ago or something like that, we were kind of talking about it then."
- "A lot of designs came through, and I'm really excited about this one."
- Demo types come from other libraries: "We don't own, this isn't a hierarchy that we have built ourselves."
- Why it matters: a long-requested feature is now in the language, so plan where it replaces object or marker interfaces.
- Source: 12:00 ET, transcripts/20261110-120000.txt
-->

---
layout: "shot"
image: "/shots/120317.jpg"
time: "Day 1 · 12:03"
---

# Before: `object`, and a switch that's never exhaustive

<!--
- Say: Before unions, the only common type for Dog, Cat, and Bird is object. So a Shark gets in, and the switch can never be exhaustive.
- List<object> accepts anything, so the switch warns CS8509
- Fix: union Pet(Dog, Cat, Bird), then List<Pet>. A Shark no longer fits.
- Verbatim: "Yeah, object, all the way to object, just like .NET 1.0, except with generics"
- The suggested fix is a discard pattern: "there is a way of doing it, but not a good way ... Because now you're just silencing everything that might come in."
- Union syntax: `union Pet(Dog, Cat, Bird)`. Dog, Cat, Bird are called "case types".
- Why it matters: object plus a discard hides bugs; a union makes the compiler check the set.
- Source: 12:02–12:04 ET, transcripts/20261110-120202.txt; shot /shots/120317.jpg
-->

---
layout: "shot"
image: "/shots/120500.jpg"
time: "Day 1 · 12:05"
---

# After: Shark is a compile error

<!--
- Say: With List<Pet>, adding a Shark is now a compile error, and the switch over Pet is exhaustive with no discard.
- Case types convert implicitly to the union
- Remove the Shark arm: the switch is exhaustive, no discard needed
- Make a case nullable (Cat?) and you must add a null arm
- Errors seen: Shark "cannot implicitly convert to pet"; a Shark arm in the switch is not a case of the union
- Two things a union gives: implicit conversion from case type to union, and pattern matching on the case types
- Nullable Cat demo (a Schrödinger's cat joke): the warning said exactly what was missing, the null case
- Verbatim: "when the warning's gone, you know you've dealt with everything."
- Why it matters: the compiler becomes the checklist for every case you must handle.
- Source: 12:04–12:06 ET, transcripts/20261110-120405.txt and 20261110-120602.txt; shot /shots/120500.jpg
-->

---
layout: "shot"
image: "/shots/120737.jpg"
time: "Day 1 · 12:07"
---

# Unions are real types

<!--
- Say: A union is a real type. You can add members and generics, and you can hand-write one with the [Union] attribute.
- Generic type parameters, function members (`this switch`)
- No extra state: the value inside is the state
- Case types: any type convertible to object, incl. type parameters
- Default union is a struct. Add [Union] to any class/struct to roll your own; the compiler lists what's missing (e.g. a Value property).
- Under the hood: an object? Value plus one constructor per case type. Conversion calls the constructor; pattern matching reads Value.
- Hand-write a [Union] (IUnion) to avoid boxing value types, or to adapt an existing union-like type.
- The compiler-generated union also implements IUnion (just the Value property), so code can work with unions without the exact type. "It's optional, but it's useful."
- Advanced customization is documented on Microsoft Learn ("all documented on the Learn at Microsoft")
- Why it matters: you can adapt existing union-like types and control storage to avoid boxing.
- Source: 12:06–12:13 ET, transcripts/20261110-120602.txt to 20261110-121200.txt; shot /shots/120737.jpg
-->

---
layout: "shot"
image: "/shots/121715.jpg"
time: "Day 1 · 12:17"
---

# `closed`: only your assembly can inherit

<!--
- Say: `closed` fixes the same problem for your own class hierarchy. Only your assembly can derive from it, so the switch is exhaustive.
- Setup: public abstract Operation, another project adds EvilAdd, so no exhaustive switch
- `closed` makes the class implicitly abstract
- Subclasses in other assemblies are errors
- The switch is exhaustive again
- Demo: a calculator with abstract Operation and Number, Add, Subtract, Multiply, Divide; another project added EvilAdd and EvilSubtract
- Wrapping the five classes in a union works but is "painful": "That's not the scenario that unions were created for."
- Verbatim: "When you are a close class, only in your own assembly do you get to directly inherit from that."
- Why it matters: public data models in libraries can now be closed without constructor tricks.
- Source: 12:14–12:18 ET, transcripts/20261110-121403.txt and 20261110-121600.txt; shot /shots/121715.jpg
-->

---
layout: "default"
codeSize: "22"
---

# Collection expressions take constructor args

```csharp
// before
var tags = new HashSet<string>(StringComparer.OrdinalIgnoreCase) { "one", "two" };

// C# 15
HashSet<string> tags = [with(StringComparer.OrdinalIgnoreCase), "one", "two"];
```

<!--
- Say: Collection expressions can now pass constructor arguments. Put `with(...)` first inside the brackets.
- 12:20 ET. with(...) passes constructor args: a comparer, a capacity
- Ctrl+. in the IDE offers the fix
- Screenshot: /shots/122000.jpg (not shown)
- Before: to pass a comparer or capacity you had to fall back to `new HashSet<string>(comparer) { ... }`
- After: `[with(StringComparer.OrdinalIgnoreCase), "one", "two"]` calls that constructor, then adds the items
- Verbatim: "use the with keyword, and then give a list of arguments that that collection type responds to" (transcript says "width", a speech-to-text error)
- Why it matters: you keep collection expression syntax even when the collection needs configuration.
- Source: 12:18–12:20 ET, transcripts/20261110-121805.txt and 20261110-122002.txt
-->

---
layout: "default"
codeSize: "22"
---

# Labeled `break` and `continue`

```csharp
outer: for (int i = 0; i < 19; i++)
{
    for (int j = 0; j < 23; j++)
    {
        if ((i + j) % 2 == 0)
        {
            break outer;
        }
    }
}
```

<!--
- Say: C# 15 adds labeled break and continue. Label the outer loop, then break or continue to it from deep inside.
- 12:21 ET. Replaces the "am I done yet" flag variable
- Works with continue too
- IDE refactoring: "use labeled jump statement"
- Before: a "done" flag variable, set in the inner loop and checked in the outer loop
- After: `outer:` on the outer loop, then `break outer;` leaves both loops at once
- Verbatim: "bypasses everything in between"; "Easier to not make a mistake."
- "many, many languages have something like this" ... "we're late to the game, but now we're in the game"
- Why it matters: fewer flag variables and fewer mistakes when you edit nested loops.
- Source: 12:20–12:22 ET, transcripts/20261110-122002.txt and 20261110-122200.txt
-->

---
layout: "shot"
image: "/shots/122230.jpg"
time: "Day 1 · 12:22"
---

# Extension indexers

<!--
- Say: C# 14 added extension blocks with properties. C# 15 adds extension indexers with the same syntax.
- Index into types you don't own
- Builds on C# 14 extension blocks (properties came first)
- The extension block syntax scales to new member kinds
- Wrap-up (12:24): memory safety preview lets you mark your own APIs unsafe and track it transitively; async is "not different, just faster" with runtime async
- Why it matters: you can add natural indexing to types you do not own.
- Source: 12:22–12:24 ET, transcripts/20261110-122200.txt and 20261110-122403.txt; shot /shots/122230.jpg
-->

---
layout: "statement"
---

`closed` for your hierarchy. `union` for types you don't own.

<!--
- Say: Use `closed` when you own the hierarchy. Use a union when the types are not in one hierarchy or you do not control them.
- 12:26 ET Q&A
- closed: the list is your direct descendants
- union: types not in a hierarchy, or you don't control (e.g. data over the wire)
- Generated unions are structs, so implicitly sealed
- System.Text.Json supports unions (some cases still need attributes)
- No new runtime needed: older consumers (e.g. .NET Framework 4.8) read .Value, without union pattern matching
- Why it matters: pick the right tool for closed sets; both give exhaustive switches.
- Source: 12:24–12:28 ET, transcripts/20261110-122403.txt to 20261110-122802.txt
-->

---
layout: "session"
num: 3
time: "Day 1 · 5:30 PM"
speakers: "Tanner Gooding"
---

# .NET 11 Numerics

<!--
[Session 03 · Day 1]
-->

---
layout: "shot"
image: "/shots/173229.jpg"
time: "Day 1 · 17:32"
---

# New in .NET 11: `Decimal32`, `Decimal64`, `Decimal128`

<!--
- Say: .NET 11 adds IEEE 754 decimal floating-point types in three sizes.
- Decimal32 / Decimal64 / Decimal128: 7 / 16 / 34 significant decimal digits; 32 / 64 / 128 bits
- "IEEE 754 semantics. Generic math. Your choice of representation." (stream slide)
- vs System.Decimal: both base 10, but decimal "is primarily oriented around currency"; "the IEEE decimal types ... are designed for scientific computing"
- "Not just a bigger decimal" (17:34 stream slide): System.Decimal = 28–29 significant digits, no NaN or infinity. IEEE decimals = 7/16/34 digits, NaNs, infinities, signed zero, floating-point math functions. "Same radix does not mean the same contract." (/shots/173455.jpg)
- Why it matters: base-10 floating point with standard IEEE behavior, usable in generic math code.
- Source: 17:32–17:35 ET, transcripts 20261110-173204, 20261110-173405, /shots/173229.jpg
-->

---
layout: "default"
codeSize: "18"
---

# `Decimal64` in code

```csharp
Decimal64 a = Decimal64.Parse("0.1", CultureInfo.InvariantCulture);
Decimal64 b = Decimal64.Parse("0.2", CultureInfo.InvariantCulture);
output.WriteLine($"Double sum: {0.1 + 0.2:R}");
output.WriteLine($"Decimal64 sum: {a + b}");

Decimal64 oneDecimalPlace  = Decimal64.Parse("1.0",  CultureInfo.InvariantCulture);
Decimal64 twoDecimalPlaces = Decimal64.Parse("1.00", CultureInfo.InvariantCulture);
Decimal64.HaveSameQuantum(oneDecimalPlace, twoDecimalPlaces);

Decimal64 cents = Decimal64.Parse("0.01", CultureInfo.InvariantCulture);
Decimal64.Quantize(value, cents);
```

<!--
- Say: The classic 0.1 + 0.2 demo, side by side with double — plus "quantum", which keeps track of how many digits you actually meant.
- Code copied from the stream demo (/shots/173753.jpg, DecimalDemo.cs); lines trimmed to fit.
- Output on stream (17:40, Runtime .NET 11.0.0): Double sum 0.3000000000000000444089209850062616169452667236328125 · Decimal64 sum 0.3 · Same value: True · HaveSameQuantum: False · Quantum of 1.0: 0.1, of 1.00: 0.01 · Quantize 1.235 → 1.24, 1.245 → 1.24 · IEEE divide by zero: Infinity · Acos(1 − 1e-30): double input becomes 1, Double Acos 0; Decimal128 Acos 1.414213562373095048801688724209816E-15
- Quantum: 1.0 and 1.00 are the same value but not the same quantum — "you want to keep track of the fact that you have at least a guaranteed zero digit"; it matters "when you have to worry about precision and tolerances"
- Demo also showed IEEE divide by zero (Decimal64.One / Decimal64.Zero) and Decimal128.Acos near 1 vs Math.Acos on double
- Why it matters: decimal values that remember their precision, with IEEE behavior for edge cases.
- Gotcha (Q&A, 17:58): operators (==, <, >) follow IEEE — "NaN equals NaN, it will always report false"; "If you compare 1.0 to 1.00, it will compare as equal." But `Decimal64.Equals` / `.CompareTo` follow the rules "required for collections and sorting": "NaN will equal NaN, and you still have the quantums comparing to each other." So `==` and `Equals` can disagree.
- Source: 17:36–17:58 ET, transcripts 20261110-173603, 20261110-173800, 20261110-175802, /shots/173753.jpg, /shots/174000.jpg
-->

---
layout: "shot"
image: "/shots/174113.jpg"
time: "Day 1 · 17:41"
---

# New in .NET 11: `BFloat16`

<!--
- Say: .NET 11 adds BFloat16, the 16-bit float format from Google that's common in AI.
- "It's actually a type designed by Google. Its formal name is the Brainfloat 16-bit."
- It takes float32 and "basically chops off the lower 16 bits", so it "has the same exponent range" as float "just with less precision"
- vs Half (System.Half): both 16 bits. Half = more precision near one; BFloat16 = float-like exponent range (stream slide: "16 bits. Different priorities.")
- Why it matters: pick Half for precision near one, BFloat16 when you need float's range in 16 bits.
- Source: 17:40–17:42 ET, transcript 20261110-174003, /shots/174113.jpg
-->

---
layout: "shot"
image: "/shots/174220.jpg"
time: "Day 1 · 17:42"
---

# `Complex<T>`: complex numbers in your choice of `T`

<!--
- Say: System.Numerics.Complex was double-only. .NET 11 adds Complex<T>, so you pick float, double, or Decimal128.
- "System.Numerics.Complex ... that's only supported double. People have been asking for a while ... can you also give support for float?"
- Enabled by generic math: "we were finally able to go and expose a complex of T, where the user gets to decide what that T is"
- Behavior made "compliant with the standard specification for complex number handling"
- Demo: one generic Square function "operates regardless of whether we have float or decimal 128 or complex of either of those types"
- Why it matters: write numeric code once with generic math and run it on real or complex values at the precision you choose.
- Source: 17:42–17:44 ET, transcript 20261110-174200, /shots/174220.jpg
-->

---
layout: "shot"
image: "/shots/174412.jpg"
time: "Day 1 · 17:44"
---

# Constrain the capability, not the concrete type

<!--
- Say: One generic Square<T> where T : INumberBase<T> works for Decimal128, Complex<float>, and Complex<Decimal128>.
- Code on the stream slide: `static T Square<T>(T value) where T : INumberBase<T> => value * value;`
- Inside .NET: generic math let the team write "many algorithms compressing the amount of code we have to maintain to a few hundred lines instead of several thousand"
- Why so much: int, float, double, decimal, Decimal128/64/32, complex of all of them — "it starts out as 10 to 12 primitive types, and it quickly expands out to many times more than that"
- Why it matters: in your own numeric code, constrain on the interface you need (INumberBase<T> etc.) and one method serves every type.
- Source: 17:44 ET, transcript 20261110-174402, /shots/174412.jpg
-->

---
layout: "shot"
image: "/shots/174734.jpg"
time: "Day 1 · 17:47"
---

# Tensors: layout-aware paths, dense Add ~143× faster

<!--
- Say: Tensor slices can have gaps. .NET 11's tensor code now takes the data layout into account, and some operations got dramatically faster.
- Tensors can have "dimensions or even gaps between the data. You can have non-linear slices of the data." (17:46)
- Chart: Dense float Add 16.37 µs → 0.114 µs (~143×). Gapped-row FlattenTo 7.92 µs → 0.875 µs (~9×). 64×16 float inputs, Windows x64, Ryzen 9 7950X
- Caveat: the chart compares a "Release baseline" with a ".NET 11 backport" — "Same .NET 11 runtime; baseline vs. backport assemblies." What ships where wasn't explained in this part; check before saying "in .NET 11 GA". Numbers come from the chart only (not spoken).
- Correctness too (17:48 stream slide "Fast is only useful when it's right"): fixes for broadcasting, empty tensors, slice origins, overlap validation, NaNs/ties/signed zero, and Resize now zero-fills (`default(T)`, "not repeated input": [1,2] → [1,2,0,0,0]) (/shots/174852.jpg)
- Demo output (17:52, Runtime .NET 11.0.0): gapped storage [1, 2, -99, 3, 4, -99], IsDense False, flattened view [1, 2, 3, 4]; Resize [1, 2] → [1, 2, 0, 0, 0]; overlapping dense copy [1, 1, 2, 3, 4]; strided overlap → "ArgumentException; buffer unchanged" (rejected, not silently wrong); first NaN index 2; first maximum tie index 1
- Why it matters: large speedups for common tensor operations like Add and FlattenTo.
- Source: 17:46–17:53 ET, transcripts 20261110-174604, 20261110-174802, 20261110-175203, /shots/174734.jpg, /shots/174852.jpg
-->

---
layout: "statement"
---

Accuracy is part of performance: one path got slower on purpose.

<!--
- Say: On hardware without FMA, the .NET team made one Tan path slower on purpose to keep it accurate.
- Stream slide (17:54): "A faster path must still honor the numeric contract." With FMA: guaranteed fused vector range reduction. Without FMA: scalar fallback "only for cancellation-sensitive vectors"
- "Selected non-FMA Tan case: 5.60 us -> 9.19 us. An intentional accuracy tradeoff." (/shots/175455.jpg)
- Also new in .NET 11, System.Random: you used to get only Int32/Int64/Double etc. — "You couldn't get it for custom numeric types ... any other floating point type like half." New APIs request "the next integer given a particular type" (0 inclusive to a limit exclusive) and "the next binary floating point value given the specified type"
- Why it matters: when you optimize numeric code, correctness on all hardware comes first.
- Source: 17:54–17:56 ET, transcript 20261110-175400, /shots/175455.jpg
-->

---
layout: "shot"
image: "/shots/175703.jpg"
time: "Day 1 · 17:57"
---

# Parse "12.5ms": partial parsing, UTF-8, hex floats

<!--
- Say: New parsing building blocks — parse just the number out of "12.5ms", parse straight from UTF-8 bytes, and read hex floats.
- Partial parsing: "I've got 12.5 milliseconds, I want to parse out just the number — we have new API TryParsePartial"; it stops at the first invalid character and "will then give you back how much it consumed", so you can validate the unit next
- UTF-8: bytes ↔ BigInteger / Complex (stream slide)
- Hexadecimal floats: 0x1.8p+1 → 3 (stream slide)
- Why it matters: parse a number and its unit (or trailing text) in one pass, and parse directly from UTF-8 data.
- Source: 17:56–17:58 ET, transcript 20261110-175603, /shots/175703.jpg
-->

---
layout: "session"
num: 4
time: "Day 1 · 6:30 PM"
speakers: "Richard Lander, Andy Gocke"
---

# .NET Runtime vNext: Memory Safety and Runtime Async

<!--
[Session 04 · Day 1] Agenda title; the notes agent logged it as ".NET Runtime vNext: Async and Safety". Started ~6:32 PM ET.
- The keynote already has runtime async (0 B allocated) and memory safety v2 slides; add only new details here.
-->

---
layout: "statement"
---

Runtime async: opt in your apps now. Libraries wait for .NET 12.

<!--
- Say: Runtime async is opt-in in .NET 11 and expected to be the default in .NET 12. Apps can turn it on now; libraries should wait for .NET 12.
- Guidance (Q&A, 18:56): "right now, libraries should stay on compiler async, while applications, by all means." Reason: "not all of the runtimes that we're shipping in .NET 11 support runtime async" — "It's just MonoWASM." "In .NET 12, they will."
- ⚠ CONFLICTING STATEMENTS on stream — don't claim either as fact without checking: at 18:32 Rich said "we actually compiled much of the framework libraries with this feature enabled ... you're going to be getting some benefit"; at 18:56 the speakers said "our libraries are staying on compiler async for the moment".
- Rich Lander (18:32): "This feature is new in .NET 11, but it's opt-in. This is this feature's MSBuild property is how you turn it on, and we expect it to be the default in .NET 12."
- "We actually compiled much of the framework libraries with this feature enabled. So no matter what, you're going to be getting some benefit from this feature when you install and start using .NET 11."
- Stream slide: "No IL state machines. No ValueTask. Near Synchronous Performance." (/shots/183325.jpg)
- The exact MSBuild property wasn't readable in what I verified; the notes agent says `<Features>runtime-async=on</Features>` — check docs before quoting it.
- Speed (18:40 chart, "The performance advantage grows with async depth", synchronous completion, modeled on a backup app): time per op state machines vs runtime async — 3 frames 1.487 vs 1.399 µs (1.06×), 5 frames 1.547 vs 1.431 µs (1.08×), 7 frames 1.621 vs 1.437 µs (1.13×). Allocations: see the keynote "0 bytes" slide. (Chart image not added to the repo: it carries a "Microsoft Confidential" footer.)
- Why it matters: try it in your apps now (unless you target Mono WASM); hold off in libraries until .NET 12.
- Source: 18:32–18:34 and 18:56 ET, transcripts 20261110-183200, 20261110-185603, /shots/183325.jpg
-->

---
layout: "shot"
image: "/shots/183743-compare.jpg"
time: "Day 1 · 18:37"
---

# One `await`, lowered: a state machine vs. one line

<!--
- Say: Here's the same one-await method after the compiler lowers it. Left: today's compiler-generated state machine. Right: runtime async — one line.
- Compiler async "turns into this big complicated state machine with all this plumbing"
- Runtime async lowers to `[MethodImpl(MethodImplOptions.Async)]` + `AsyncHelpers.Await(Task.Delay(1))` (stream slide)
- MethodImplOptions.Async "is actually this new calling convention ... so that each method can be optimized and do like interprocedural optimization to get the whole chain to behave as one"
- AsyncHelpers.Await is "a JIT intrinsic" — no state machine transformation at C# compile time
- Why it matters: the runtime, not the compiler, now owns async. (Inference: this is what enables the keynote's 0-byte allocation numbers.)
- Source: 18:36–18:38 ET, transcript 20261110-183603, /shots/183743-compare.jpg
-->

---
layout: "shot"
image: "/shots/183943-compare.jpg"
time: "Day 1 · 18:39"
---

# Async stack traces: just your methods

<!--
- Say: With runtime async, the call stack shows just your methods, in the order you wrote them — no MoveNext or builder frames in between.
- Before: 9 frames — each of your 3 calls wrapped in `<Method>d__N.MoveNext()` and `AsyncMethodBuilderCore.Start<TStateMachine>(...)`
- After: 3 frames — OrderService.LoadAsync, OrderService.GetOrderAsync, OrdersController.Get
- Stream slide: "The runtime suspends and resumes the method itself: no generated state machine. The same stack now shows just your methods, in the order you wrote them."
- Shown with Environment.StackTrace (18:38); "debuggers and profilers show those frames between every one of your calls" before
- Why it matters: easier debugging, profiling and log reading for async code.
- Source: 18:38–18:40 ET, transcript 20261110-183803, /shots/183943-compare.jpg
-->

---
layout: "statement"
---

Async exceptions: 2.5–3.4× faster with runtime async.

<!--
- Say: When things fail, async exceptions get expensive. Runtime async makes them 2.5 to 3.4 times faster at 8 frames.
- Chart (18:42, ".NET 11 RC", mean time per op, lower is better): No suspension — 2.5× faster than compiler async at 8 frames. Suspended async — 3.4× faster at 8 frames. Compiler async climbs steeply with depth (to ~80+ µs at 32 frames); runtime async stays near the sync reference
- Why it matters (speaker): when a service fails, "you get a lot of exceptions ... and just the exceptions start piling up" — "the async cost really flows through to exceptions"
- Allocations: "even if you go down to 32 frames, it doesn't matter. It's all zero byte allocation all the way through."
- Chart frame /shots/184254.jpg not added to the repo (it may carry the confidential footer).
- At depth (18:44): exception handling with runtime async "gets cheaper than sync when we get down to 32 frames ... actually outperforming fully synchronous code"; "almost all of that allocation is reduced or eliminated" (the notes agent's 77%/73% figures were not confirmed in the transcript)
- Source: 18:42–18:45 ET, transcripts 20261110-184204, 20261110-184404
-->

---
layout: "default"
codeSize: "20"
---

# Memory safety v2: turn it on (preview)

```xml
<LangVersion>preview</LangVersion>
<MemorySafetyRulesVersion>2</MemorySafetyRulesVersion>
<AllowUnsafeBlocks>false</AllowUnsafeBlocks>
```

```csharp
var dotnet12 = unsafe(CodeHasASafetyContract());
```

<!--
- Say: Memory safety v2 is a preview in .NET 11 and expected to GA in .NET 12. Here's how you opt in today.
- "This feature is in preview in .NET 11 ... we expect it to be fully GA prod in .NET 12." (18:45)
- Project properties copied from the stream slide "Making C# code safer" (/shots/184544.jpg); the `unsafe(...)` line is the stream's own joke-title code, not a real API to quote
- Keynote recap: adopts the Rust/Swift unsafe model, stricter — unsafe off by default, unmarked unsafe calls are errors
- Why it matters: try it on a branch now so you're ready when it becomes the default rules.
- Source: 18:44–18:46 ET, transcript 20261110-184404, /shots/184544.jpg
-->

---
layout: "statement"
---

"~70% of the vulnerabilities Microsoft assigns a CVE each year continue to be memory safety issues."

<!--
- Say: That's why memory safety v2 exists. Set the rules version to 2 and turn off unsafe blocks, and no unsafe code gets in — whether a person or an AI agent writes it.
- Quote on the stream slide, attributed to Microsoft (18:46). Rich Lander: "Microsoft made this statement a few years ago that 70% of vulnerabilities are caused by memory safety issues."
- With MemorySafetyRulesVersion 2 (and AllowUnsafeBlocks false), "or AI agents are writing code for you" — the rules apply either way
- Frame /shots/184708.jpg not added to the repo (bottom-left footer looks like the confidential label).
- Why it matters: in the agent era, a compiler-enforced "no unsafe" rule is a guardrail you don't have to remember.
- Source: 18:46–18:48 ET, transcript 20261110-184603
-->

---
layout: "default"
codeSize: "20"
---

# `unsafe` becomes a contract callers can see

```csharp
// Before — callers saw a normal method
public static string PtrToStringAnsi(
    IntPtr ptr, int len);

// Unsafe-v2 — callers must explicitly opt in
public static unsafe string PtrToStringAnsi(
    IntPtr ptr, int len);
```

<!--
- Say: Under memory safety v2, a method can be marked unsafe, and that requirement flows up to everyone who calls it.
- C# already gives safety by default (18:48): definite assignment, "all of the dynamically allocated memory is zeroed", "bounds checks by default on all array accesses and collections", and the GC
- "But we also have escape hatches" (pointers, P/Invoke) — and "we have no way of delivering that safety contract up to our callers." Now "the escape hatches can propagate that information up to the callers."
- Example from the stream: Marshal.PtrToStringAnsi becomes a method-level `unsafe` member ("requires-unsafe")
- Obligation model (18:50): "when you declare something to be unsafe, that means that there's additional rules that the caller has to" follow. A safe wrapper can satisfy them: `DecodeAnsi` "is a safe method with a usage of the unsafe method pointer to string ANSI inside it" — it takes a ReadOnlySpan ("a bounds check safe C# construct") and calls PtrToStringAnsi "inside an unsafe block", the point where "the caller has satisfied all the requirements". So unsafe doesn't have to spread to every caller.
- More (18:52): unsafe on a method "means dragons may lie here"; a new "safety" documentation concept to describe the caller's obligation; "fields can have unsafe contracts"; and "we have unsafe expressions now" alongside unsafe blocks
- Same model as Rust and Swift (18:54): "Rust is kind of like the gold standard for how to do memory safety"; Swift's 2025 release "more or less implemented the Rust memory safety programming model". Side by side, the three safe wrappers and unsafe APIs "look exactly the same" (see the keynote memory safety slide; this session's frame not added — may carry the confidential footer)
- Advice (Q&A, 18:56): "if you don't actually have a use case in mind, I would say don't reach for it" (unsafe)
- Code copied from the stream slide "Unsafe is a contract"; the frame itself (/shots/184848.jpg) is NOT in the repo — it carries the "Microsoft Confidential" footer
- Why it matters: you can see in code review which calls need care, instead of it hiding in a normal-looking API.
- Source: 18:48–18:56 ET, transcripts 20261110-184803, 20261110-185000, 20261110-185204, 20261110-185404, 20261110-185603
-->

---
layout: "statement"
---

He turned on memory safety v2. The build failed. An AI agent had added unsafe code.

<!--
- Say: Rich Lander turned on memory safety v2 in his own project and found unsafe code an AI agent had slipped in. None of it was needed.
- Rich (18:58): "I flipped the memory safe v2 property ... As soon as I did that, my build failed. And it's like, oh, man, some AI agent brought in some unsafe code that I didn't realize."
- "None of this needs to be here ... there's better approaches, more modern approaches for all of these things. Ripped out all the unsafe code."
- It was "preview 7 or something like that"; he now has the feature on in his app code. "So, quote, unquote, the feature works."
- Also (Q&A): with v2, you can see when "the framework method you're using actually contains unsafe", because it's annotated
- Why it matters: turning it on catches unsafe code an agent added without you noticing.
- Source: 18:58–19:00 ET, transcript 20261110-185800
-->

---
layout: "shot"
image: "/shots/115537.jpg"
time: "Day 1 · 11:55"
---

# Microsoft builds with .NET too

<!--
- Copilot, Teams, Bing, Xbox, Azure, Exchange Online, Windows 365, Intune
- aka.ms/dotnet-developer-stories
- Say: Microsoft runs its own big products on .NET.
- Full slide list: Microsoft Copilot, Teams, Bing, Copilot Studio, Intune, Azure, Xbox, Exchange Online, Windows 365, Azure Service Fabric.
- Verbatim (Kathy): "if you're getting a Teams message on your phone, that's backed by a .NET service." Cloud PC is also .NET, "running Aspire on the back-end."
- Source: 11:55 ET, 20261110-115402.txt; shot 115537.jpg.
-->

---
layout: "shot"
image: "/shots/115635.jpg"
time: "Day 1 · 11:56"
---

# Download .NET 11: get.dot.net

<!--
- winget and other installers "soon"
- Say: That's the keynote. .NET 11 is out now at get.dot.net.
- Verbatim (close, light cleanup): "So, get.dot.net. I said the site correctly, get.dot.net. Soon it will be in winget, dotnetup, all the other places you can install it as well" (STT fixed: "winget.net up").
- Also at the close: a 2026 developer survey (about 15 minutes) that feeds .NET 12 planning.
- Why it matters: install it today, try the features you just saw.
- Source: 11:56-11:58 ET, 20261110-115600.txt and 20261110-115802.txt; shot 115635.jpg.
-->

---
layout: "shot"
image: "/shots/day2/200735-crop.jpg"
time: "Day 2 · 20:07"
---

# .NET 11: over 7,000 contributors. 589,000+ NuGet packages. 1.1 trillion downloads.

<!--
- Say: The host closed Day 2 with the ".NET 11" announcement blog: over 7,000 contributors built it, and the ecosystem has more than 589,000 unique NuGet packages and over 1.1 trillion package downloads. Days 3 and 4 belong to the community.
- On screen (devblogs.microsoft.com "Announcing .NET 11", section "Thank you for building .NET with us"): ".NET 11 is the work of over 7,000 contributors." "more than 589,000 unique packages on NuGet and over 1.1 trillion package downloads." The image is a mosaic of contributor avatars.
- Host (20:06-20:07): the avatars are "some of the folks that helped build out .NET 11 ... I work with the dev team ... they pulled down a list of all the contributors." Days 3 and 4 "are run completely by the community", reachable from the .NET Conf site or dotnetconf.net. The Day 1 and Day 2 "mega streams" will be "chopped up" into per-session videos in the .NET YouTube playlist; some pre-records are already there.
- Image: the blog page, cropped (browser tabs and taskbar removed).
- Source: 20:06-20:08 ET, transcript 20261111-200600; crop of shot 20261111/200735.
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
