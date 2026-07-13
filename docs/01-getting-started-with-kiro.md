# Session 1 — Get Your Feet Wet with Kiro

*Hands-on. The slides gave you the **why**; this session gets your hands on the tool with a
series of small, low-stakes tasks. The goal isn't to build anything real yet — it's to learn
where the buttons are and get comfortable driving Kiro.*

> 📚 **Official companion:** this session follows the shape of Kiro's own
> [Your first project](https://kiro.dev/docs/getting-started/first-project/) guide, kept
> deliberately small. Keep that page open in a tab — it has short video transcripts for each step.
>
> When you're comfortable here, [Session 2](02-your-first-project.md) uses these same features to
> build a real feature end to end.

---

## Before you start

Make sure you have:

- **Kiro installed** — see [kiro.dev](https://kiro.dev).
- **A folder to play in** — any existing project, or a brand-new empty folder. Nothing is
  precious in this session; we're just poking around.
- **A terminal** and basic familiarity with your machine.

> No coding required in this session. If you don't have a project handy, make a scratch one:
> ```bash
> mkdir kiro-playground && cd kiro-playground
> ```

---

## Task 1 — Open a project and say hello

**What to do:**

1. **Open your folder** in Kiro — click **File > Open Folder**, or drag-and-drop the folder onto
   Kiro, or run `kiro .` from inside it in your terminal.
2. **Open the Kiro panel** — click the **Kiro Ghost icon** 👻 in the activity bar (left sidebar).
   This panel is home base for every feature you'll touch today.
3. **Find the chat pane** — it's open by default. This is where you talk to Kiro.

👉 **Try it — your first prompt.** Type this into the chat and send it:

> *"Give me a one-sentence summary of what's in this folder, then suggest three tiny things I
> could build here for fun."*

Watch how Kiro reads your workspace before answering. Congratulations — you're driving Kiro.

> ✅ **You learned:** how to open a project, where the Kiro panel and chat live, and that Kiro
> sees your workspace.

---

## Task 2 — Make a trivial change, then undo it with the timeline

Now let Kiro *write* something — and practice rolling back, so you'll never be afraid to
experiment.

👉 **Try it — ask for a tiny change:**

> *"Create a file called `HELLO.md` with a friendly one-line greeting and today's date."*

**What to do:**

1. Review the change Kiro proposes and **accept** it. Open `HELLO.md` to confirm it's there.
2. Find the **timeline / checkpoints** for the session (in the chat/execution view).
3. **Roll back** to the checkpoint *before* that change and watch `HELLO.md` disappear — Kiro
   restores the snapshot of your files.

👉 **Try it again — a second approach.** Ask for a *different* version, compare, and keep whichever
you like:

> *"Actually, make `HELLO.md` an ASCII-art banner of the word HELLO instead."*

> ✅ **You learned:** Kiro proposes → you approve, and the timeline is your safety net for trying
> multiple approaches without fear.

---

## Task 3 — Generate steering files and add one rule

**Steering files** live in `.kiro/steering/` and give Kiro context about your project so it stops
guessing. Let's create them and feel the difference.

**What to do:**

1. In the Kiro panel, choose **Generate Steering Docs**.
2. Open the files Kiro creates in **`.kiro/steering/`** — typically **product**, **tech**, and
   **structure**. Skim them. On a fresh folder they'll be sparse; that's fine.
3. Click the **`+`** in the steering section to add a **custom** steering file. Paste something
   small and opinionated:

   ```markdown
   # Coding Standards
   - Prefer clear names over clever ones.
   - Keep functions short.
   - Add a matching test file for every module.
   ```

👉 **Try it — feel the difference.** Ask Kiro the same kind of question and notice it now respects
your file:

> *"Add a tiny example module for this project — follow my coding standards."*

Kiro should honor the naming and the "matching test file" rule you just wrote. That's steering:
turning generic output into output that fits *your* project.

> ✅ **You learned:** how to generate steering docs, add a custom rule, and see Kiro follow it.
> [Session 2](02-your-first-project.md) puts steering to work on a real feature.

---

## Task 4 — Peek at a spec (don't build it yet)

**Specs** turn an idea into a plan in three phases: **Requirements → Design → Tasks**. Here you'll
just *create one and look* — you'll actually execute a spec in Session 2.

**What to do:**

1. Click the **Spec** button in chat, or the **`+`** in the panel's **Specs** section.
2. Describe something tiny in plain language, for example:

   > *"Add a command that prints a random motivational quote."*

3. Walk through the **Requirements** phase and read what Kiro produces — note the structured,
   testable acceptance criteria (EARS notation). Peek at the **Design** and **Tasks** it drafts.

You don't have to run the tasks now. The point is to *see* how a one-line idea becomes a
reviewable plan.

> ✅ **You learned:** where specs live and what the three phases look like — the core of
> spec-driven development you'll use for real next session.

---

## Task 5 — Turn on an MCP server and use it

**MCP (Model Context Protocol)** connects Kiro to outside tools and data. Kiro ships with a
built-in **`fetch`** server — let's switch it on. No API key needed.

**What to do:**

1. In the Kiro panel, **enable MCP**, then click the **edit (pencil) icon** next to MCP to open
   its JSON config.
2. Find the built-in **`fetch`** server and set **`"disabled": false`**, then save.

👉 **Try it — ask something that needs the web:**

> *"#[fetch] Fetch the Kiro docs homepage at https://kiro.dev/docs and summarize what's there."*

Notice Kiro reaching out through the `fetch` tool to get real content. (Adding other servers — like
web search — just means another entry in that JSON, e.g. `command`, `args`, and an API key in
`env`.)

> ✅ **You learned:** how to enable an MCP server and invoke a tool with `#[...]`. MCP is how Kiro
> reaches docs, APIs, and databases.

---

## Task 6 — Look around: Hooks and Powers

Two more panels worth a 2-minute look so you know they exist.

**Agent Hooks** — automations that run on events (file saved/created/deleted, or a manual trigger).

👉 **Try it — create a manual hook:** open the **Agent Hooks** section, click **`+`**, choose a
**manual trigger**, and give it an instruction like *"Summarize what changed in this project since
I started."* Save it, then run it from the panel and watch it fire. (Session 2 wires a hook to
**file save** for real.)

**Powers** — downloadable bundles of best practices (MCP servers + steering + hooks) from experts
and partners.

👉 **Try it — browse Powers:** open the **Powers** section and skim what's available. Notice how a
single power can bundle context and actions you'd otherwise set up by hand.

> ✅ **You learned:** hooks automate chores on triggers; powers package best practices you can pull
> in with a click.

---

## You're warmed up

In a few small tasks you've driven every core surface of Kiro:

**chat → approve/rollback (timeline) → steering → specs → MCP → hooks & powers.**

You didn't build a product — you got the feel of the platform. Now do it for real.

**Next:** [Session 2 — Your first project →](02-your-first-project.md) — take one feature from
idea to working code using the full build loop.
