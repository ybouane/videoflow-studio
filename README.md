<a href="https://studio.videoflow.dev">
  <img src="https://studio.videoflow.dev/images/banner.png" alt="VideoFlow Studio — your website, in motion" />
</a>

# @videoflow/studio

[![npm](https://img.shields.io/npm/v/@videoflow/studio.svg)](https://www.npmjs.com/package/@videoflow/studio)
[![node](https://img.shields.io/node/v/@videoflow/studio.svg)](https://nodejs.org)
[![license](https://img.shields.io/badge/license-proprietary-orange.svg)](./LICENSE)

**Turn a product URL into a finished launch video.**

```bash
npx @videoflow/studio
```

Point it at your website. It reads the site, works out what the product is and
who it is for, plans a film, writes it, renders it, watches the result back,
fixes what it finds, and hands you an MP4 — plus a link to keep editing it.

> **Dashboard:** [studio.videoflow.dev](https://studio.videoflow.dev) ·
> **Pricing:** [studio.videoflow.dev/pricing](https://studio.videoflow.dev/pricing) ·
> **The engine:** [videoflow.dev](https://videoflow.dev)

Studio is a **harness**, not a model. The intelligence is whichever coding agent
you already pay for — [Claude Code](https://claude.com/claude-code) or
[Codex](https://openai.com/codex) — running on your machine, on your account.
Studio gives it the brief, the skill library, the tools and the review pass, and
gets out of the way.

---

## Quick start

```bash
npx @videoflow/studio --url stripe.com --duration 30
```

First run asks for your email and sends a link. Open it, press **Authorize**,
and the terminal signs itself in. No password, and nothing to copy back.

Then watch it work — in the terminal, or on the dashboard URL it prints.

```
◇  ✓ Researching the site and planning the film · 4m 12s
◇  ✓ Writing the scenes · 11m 38s
◇  ✓ Rendering frames to look at (round 1) · 27s
◇  ✓ Reviewing the film and measuring the script (round 1) · 4m 37s
◇  ✓ Applying the notes (round 1) · 6m 02s
◇  ✓ Rendering the film · 2m 14s

● Your trailer
  ~/.videoflow-trailers/stripe-com-1789673130357/trailer.mp4
```

---

## How it works

You give it a URL. It:

1. **Reads your site** — the real pages, screenshotted and inspected. Your copy,
   your colours, your typefaces, your logo, the features worth showing.
2. **Plans the film** — one concept with a spine, not a list of features. It
   picks a bed from a scored music library and builds the cut on that track's
   own beat grid.
3. **Writes the scenes** — as a real, editable document: typed layers with
   timing and properties, not an opaque render.
4. **Renders it** — deterministically, in a browser-based renderer, on your
   machine. Every shape and letter is drawn from data, so it is sharp at any
   size and nothing melts.
5. **Reviews its own work** — it watches the encoded frames back and measures
   what the eye cannot check: contrast against the real background, text inside
   the safe area, a shape an order of magnitude out of scale, a scene that never
   moves. Then it fixes what it found and renders again, before you see it.

Then keep directing it in plain language — *"hold the end card a beat longer"* —
or open the film in the browser editor and move things yourself.

---

## What you need

| | |
| --- | --- |
| **Node** | 20 or newer |
| **A coding agent** | [Claude Code](https://claude.com/claude-code) or [Codex](https://openai.com/codex), signed in. Studio drives it; the usage is on your own subscription. |
| **An account** | Free. Created on first run, from the link we email you. |

Rendering happens locally as well. Nothing about your product leaves your
machine except the studio API calls that coordinate the run.

## Free to start

**4 renders or edits a month.** A render is one film; an edit is one round of
changes. So four trailers, or two trailers and two rounds of notes — your call.
No card required. [See plans →](https://studio.videoflow.dev/pricing)

---

## Usage

```bash
npx @videoflow/studio                       # it will ask you everything
npx @videoflow/studio logout                # sign this machine out
npx @videoflow/studio help
```

### Options

| Flag | |
| --- | --- |
| `--url <url>` | Skip the question |
| `--brief "<text>"` | Guidance for the producer and director, in your words |
| `--duration <n>` | Seconds (default `30`) |
| `--rounds <n>` | Review rounds (default `1`) |
| `--provider <id>` | `claude` (default) or `codex` |
| `--model <id>` | claude: `opus` (default), `sonnet`, `haiku` · codex: `sol` (default), `terra` |
| `--workdir <path>` | Where the run is written |
| `--edit "<request>"` | Change an existing film in `--workdir`, then re-render |
| `--resume <projectId>` | Reopen a project by its id (the dashboard shows this) |
| `--new` | Skip the "what are we doing?" list, start fresh |
| `--yes` | Take every default, ask nothing |

### Examples

```bash
# a 20-second cut, with direction
npx @videoflow/studio --url acme.dev --duration 20 \
  --brief "lead with the API, developer audience, no stock smiles"

# change one you already made
npx @videoflow/studio --edit "cut the map scene, hold the end card longer" \
  --workdir ~/.videoflow-trailers/acme-dev-1789673130357

# pick a run back up where it stopped
npx @videoflow/studio --resume 115afa1e-d6e3-4b8d-ae61-3f2b0be5be1b
```

Install it globally if you would rather:

```bash
npm i -g @videoflow/studio
videoflow
```

---

## Every run has a page

The CLI prints a dashboard URL as soon as it starts. Watch the phases, the
frames and the film as they happen; download the MP4 when it is done; open it in
the **browser editor** to move a layer by hand; or type a change in plain
language and let the agent make it. Every version is kept.

Projects are private to your account.

---

## Licensing — please read

**This CLI is proprietary software.** It is published so you can install and run
it under the terms in [LICENSE](./LICENSE). It is *not* open source, and what is
in this package is minified build output rather than a readable copy. Reverse
engineering it — including by pointing a coding assistant at it — is prohibited.

**The rendering engine is a different thing.** VideoFlow itself, the renderer
that draws the frames, is open source under Apache-2.0 and lives at
[videoflow.dev](https://videoflow.dev). Studio is the agent harness built on top
of it.

Open engine, closed harness. Do not infer the licence of one from the other.

---

## Resources

- [studio.videoflow.dev](https://studio.videoflow.dev) — account, plans, your projects
- [Pricing](https://studio.videoflow.dev/pricing)
- [Studio vs. Remotion](https://studio.videoflow.dev/studio-vs-remotion) · [Studio vs. HyperFrames](https://studio.videoflow.dev/studio-vs-hyperframes)
- [videoflow.dev](https://videoflow.dev) — the open-source rendering engine
- [`@videoflow/core`](https://www.npmjs.com/package/@videoflow/core) — the video model underneath it all
- Support: [hello@videoflow.dev](mailto:hello@videoflow.dev)

## License

[SEE LICENSE IN LICENSE](./LICENSE) — proprietary.
