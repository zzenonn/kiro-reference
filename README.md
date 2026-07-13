# Kiro in a Day — Workshop Reference

A hands-on reference for learning **Kiro** and the **AI-DLC** workflow in a single-day workshop.
It assumes **zero prior Kiro knowledge** and takes you from "what is agentic development?"
all the way to shipping a feature with specs, hooks, MCP, and the AI-Driven Development Life Cycle.

> Kiro is an AI IDE (plus CLI and browser surfaces) built for taking software from
> **prototype to production** with *spec-driven development* — keeping you in control at every step.

---

## ⚠️ Disclaimers

- **Reference material only.** This repository is a learning/reference resource for a workshop.
  It is **not production-ready**, is **not a supported product**, and comes with **no warranty**.
- **Not for production use.** Nothing here is intended to be deployed or relied upon in a
  production environment. Validate everything against official sources before real-world use.
- **Views are my own.** Any opinions, framing, or recommendations expressed here are **my own**
  and do **not** represent the views of my employer, Kiro, AWS, or any other organization.
- **Sources may change.** Kiro and the AI-DLC project evolve; always defer to the official
  [Kiro docs](https://kiro.dev/docs) and [awslabs/aidlc-workflows](https://github.com/awslabs/aidlc-workflows)
  for current, authoritative guidance.

---

## Who this is for

- Developers and teams trying Kiro for the first time.
- Workshop facilitators who want a ready-made, do-it-yourself track.
- Anyone who wants a concise, opinionated tour instead of scattered docs.

No specific language or framework is required. You'll bring your **own** project idea —
the more fun, the better (a Pac-Man clone, a habit tracker, a Discord bot, whatever excites you).

---

## The day at a glance

| # | Session | Guide | Format |
|---|---------|-------|--------|
| 1 | **Getting started with Kiro** — the concepts | [`docs/01-getting-started-with-kiro.md`](docs/01-getting-started-with-kiro.md) | Read + discuss (~45 min) |
| 2 | **Your first project** — build a feature end to end | [`docs/02-your-first-project.md`](docs/02-your-first-project.md) | Hands-on (~2–3 hrs) |
| 3 | **AI-DLC with Kiro** — a repeatable delivery workflow | [`docs/03-aidlc-with-kiro.md`](docs/03-aidlc-with-kiro.md) | Hands-on (~1.5–2 hrs) |

Do them in order. Session 1 gives you the vocabulary, Session 2 gets your hands dirty,
and Session 3 layers a structured lifecycle on top.

---

## Prerequisites

Before the workshop, make sure you have:

- **Kiro installed** — see [kiro.dev](https://kiro.dev) for the IDE, CLI, and web preview.
- **A project idea** you're excited to build (you'll create it during Session 2 — no starter code needed).
- **Basic familiarity** with a terminal and your language/framework of choice.
- *(For Session 3)* `git` installed, so you can clone the AI-DLC rules.

---

## How to use this repo

1. Start with [Session 1](docs/01-getting-started-with-kiro.md) to understand *why* Kiro works the way it does.
2. Open Kiro on a fresh project and follow [Session 2](docs/02-your-first-project.md) step by step.
3. When you're comfortable, adopt the [AI-DLC workflow](docs/03-aidlc-with-kiro.md) for real delivery.

Everything here is a **reference you can return to** after the workshop.

---

## Credits & sources

- Kiro product concepts and screenshots are drawn from official Kiro materials — see [kiro.dev](https://kiro.dev).
- The AI-DLC workflow in Session 3 is based on the open-source
  **[awslabs/aidlc-workflows](https://github.com/awslabs/aidlc-workflows)** project by AWS Labs.
  That repository is the **source of truth** for the AI-DLC rules; this guide distills the
  Kiro-specific path and links back to the original rather than copying its files.
