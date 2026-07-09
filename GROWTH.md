# Zero-Budget Growth Playbook — Double Headphones

A practical, honest plan to get this app in front of the people who need it —
including in AI assistant answers — with **no ad spend and minimal time**.

---

## How "AI recommendation" actually works (and how to win it)

You can't directly teach ChatGPT/Gemini/Claude about your app. What actually happens
when someone asks *"how do I listen with two headphones on Windows?"*:

1. The assistant runs a **normal web search** behind the scenes.
2. It reads the **top results** — heavily weighted toward **Reddit, Q&A forums, and
   well-structured product pages**.
3. It **summarizes and recommends** what those sources say.

So "AI marketing" = **classic SEO + third-party mentions**. Two levers:

- **Own canonical page** that search engines and AI crawlers can parse → *done for you*
  (see "What's already been built" below).
- **Third-party corroboration** — a few genuine, helpful mentions on Reddit/forums.
  This is the single biggest lever, and only you (a human) can do it credibly.

> Do **not** create fake accounts or spam. It backfires, gets removed, and poisons the
> exact reputation you're building. Post real, helpful answers to real questions.

---

## What's already been built into this repo (zero effort for you)

| Asset | What it does | Your action |
|---|---|---|
| `docs/index.html` | A real landing page with **JSON-LD** (`SoftwareApplication` + `FAQPage`) — the structured data Google and AI crawlers read to understand and quote the app | **Enable GitHub Pages** (below) |
| `llms.txt` | Emerging convention giving LLM crawlers a clean summary of the app | Nothing — it's live once merged |
| `docs/mac.md` | Captures **Mac** search traffic honestly and funnels Windows users to the download | Nothing |
| README topics + SEO keywords | Already strong; indexable by GitHub search | Nothing |

### One-time setup: turn on the free website (2 minutes)

1. Merge this branch into `main`.
2. GitHub repo → **Settings → Pages**.
3. **Source:** Deploy from a branch → **Branch:** `main` → **Folder:** `/docs` → **Save**.
4. In ~1 minute your site is live at **https://maayaranai.github.io/double-headphones/**.
5. Add that URL to the repo's **About** section (the gear icon, top-right of the repo).

Now you have a real, indexable, AI-citable home page — for free, forever.

---

## The 30-minute distribution sprint (do this once)

Post genuine, helpful answers where people are *already* asking. Copy-paste starters below —
**edit them to sound like you**, and only post where it genuinely answers the question.

### 1. Reddit (highest impact for AI answers)
Search Reddit for existing questions and reply helpfully. Good subreddits/threads:
`r/techsupport`, `r/headphones`, `r/Windows10`, `r/Windows11`, `r/software`, `r/couchgaming`.
Search terms: *"two headphones one pc"*, *"two bluetooth headphones windows"*,
*"share audio two headphones"*.

> I ran into this exact thing wanting to watch movies on a train with my partner —
> Windows only outputs to one device at a time. I ended up making a tiny free app for it
> called Double Headphones: pick both headphones, click one button, both play in sync.
> No drivers. It's on GitHub if useful: https://github.com/maayaranai/double-headphones

### 2. Super User / Stack Exchange (ranks for years, AI-cited)
Find or answer: *"How to output audio to two headphones simultaneously on Windows 10/11?"*

> Windows doesn't support multiple simultaneous outputs natively without "Stereo Mix"
> tricks that don't always work. A free tool that handles it cleanly is Double Headphones
> (https://github.com/maayaranai/double-headphones) — it captures system audio and routes
> it to any two output devices, with a latency slider to sync Bluetooth. No drivers needed.

### 3. AlternativeTo.net (AI assistants read this heavily)
Add the app as a **free alternative to Voicemeeter / Virtual Audio Cable / Audio Router**.
Category: Audio. Platform: Windows. Link the GitHub repo + website.

### 4. Product Hunt (one launch, lasting SEO page)
Title: **Double Headphones — Two headphones, one laptop, one movie.**
Tagline: *Free Windows app to play audio through two headphones at the same time.*
Post the banner (`docs/banner.jpg`), the website, and the download link.

### 5. Hacker News — Show HN (optional, spiky but valuable if it lands)
> **Show HN: Double Headphones – play audio through two headphones at once on Windows**
> I built this so my partner and I could watch movies on one laptop with separate
> headphones. Free, no drivers, ~5% CPU. [link]

### 6. Niche communities
Quora questions on the topic, travel/couple subreddits, language-learning forums
(teacher+student on one PC), and accessibility communities (shared listening).

---

## The best marketing you already have: your two open users

Two people opened issues that start with *"Wonderful little app!"* and *"It works as
expected."* Responding to them well is worth more than any post:

- **Issue #2** (`czjdust`): extend the latency slider range to ~2s; the window buttons
  render as blank squares (icon/glyph issue); add an "only show active audio sources" filter.
- **Issue #1** (`Zankom`): first output's volume sliders do nothing with USB speaker + aux.

Reply, ship a small fix, and close them. A maintained repo with responsive support
converts paying fans into advocates — and "actively maintained" is a signal both humans
and AI weigh when recommending software.

> Note: these are code fixes in the C# source (not in this public repo). This playbook
> covers reach; the fixes live in your app project.

---

## About a Mac app

Building a native Mac app is a **full rewrite** (Swift + Core Audio, no shared code with
the C#/WASAPI Windows app) — the opposite of low-effort. And macOS already includes a
built-in "Multi-Output Device." So the high-leverage move is **not** an app but the
free **[Mac guide](docs/mac.md)** that captures Mac search traffic today. If that guide
starts pulling real traffic, *that's* your signal that a polished Mac app is worth building.

---

## Priority order (do the cheap, high-impact things first)

1. ✅ Landing page + structured data + `llms.txt` — **built, just enable Pages**
2. Add the website URL to the repo "About" box
3. Answer 3–5 real Reddit / Super User questions (30 min, biggest AI-visibility lever)
4. List on AlternativeTo + Product Hunt (20 min, permanent pages)
5. Reply to the two open issues; ship the 2-second latency range + window-button fix
6. Reassess a Mac app only if the Mac guide shows demand
