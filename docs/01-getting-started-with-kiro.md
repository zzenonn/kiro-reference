# Session 1 — Get Your Feet Wet with Kiro

*Hands-on. The slides gave you the **why**; this session gets your hands on the tool by writing
**real code** — starting with a one-line script and ending with Kiro building a small multi-file
program in one shot. The point isn't the app; it's learning where the buttons are and seeing that
Kiro handles both trivial and genuinely complex work.*

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
- **A folder to play in** — a brand-new empty folder is perfect. Nothing here is precious.
- **A language runtime** so you can *run* what Kiro writes. Examples below use **Python 3**
  because it's quick to run, but tell Kiro to use whatever you prefer — the workflow is identical.

> Make a scratch folder to work in:
> ```bash
> mkdir kiro-playground && cd kiro-playground
> ```

---

## Task 1 — Open a project and write your first script

**What to do:**

1. **Open your folder** in Kiro — click **File > Open Folder**, drag-and-drop the folder onto
   Kiro, or run `kiro .` from inside it.
2. **Open the Kiro panel** — click the **Kiro Ghost icon** 👻 in the activity bar (left sidebar).
   This is home base for every feature today.
3. **Find the chat pane** — it's open by default. This is where you talk to Kiro.

👉 **Try it — your first prompt.** Type this into the chat and send it:

> *"Create `roll.py`: a command-line dice roller. Running `python roll.py` should roll one
> six-sided die and print the result."*

**Then:** review the file Kiro proposes, **accept** it, and run it in the terminal:

```bash
python roll.py
```

You just went from a sentence to running code.

> ✅ **You learned:** how to open a project, where the chat lives, and that Kiro writes real,
> runnable code from a plain-English prompt.

---

## Task 2 — Iterate, then undo it fearlessly with the timeline

Let's grow the script — and practice rolling back so you'll never be scared to experiment.

👉 **Try it — extend the script:**

> *"Update `roll.py` so I can run `python roll.py 2d6+3` — parse standard dice notation
> (`NdM+K`), roll it, and print each die plus the total."*

**Then:** run `python roll.py 2d6+3` and confirm it works.

👉 **Try a different approach:** ask Kiro to rewrite the parsing a second way so you can compare:

> *"Rewrite the dice-notation parsing using a regular expression instead."*

**Now roll it back:**

1. Open the **timeline / checkpoints** for the session (in the chat/execution view).
2. **Roll back** to the checkpoint *before* the regex rewrite. Watch Kiro restore the previous
   version of `roll.py` from its snapshot.

> ✅ **You learned:** Kiro proposes → you approve, and the timeline lets you try multiple
> approaches to the *same* problem without fear.

---

## Task 3 — Add steering, and watch Kiro follow your standards

**Steering files** (`.kiro/steering/`) give Kiro context so it writes code *your* way instead of
guessing.

**What to do:**

1. In the Kiro panel, choose **Generate Steering Docs**. Skim the **product**, **tech**, and
   **structure** files Kiro creates.
2. Click the **`+`** in the steering section to add a **custom** steering file. Paste something
   opinionated and specific:

   ```markdown
   # Coding Standards
   - Python: use type hints and a docstring on every function.
   - Write pytest tests alongside code in a `tests/` folder.
   - Prefer small, single-purpose functions.
   ```

👉 **Try it — feel the difference.** Ask for a change and watch Kiro honor the rules you just wrote:

> *"Refactor `roll.py` into a `roll_dice()` function with type hints and a docstring, and add
> pytest tests for it."*

**Then** run the tests to prove it:

```bash
pytest
```

Notice Kiro added type hints, a docstring, *and* a `tests/` file — because your steering told it to.

> ✅ **You learned:** how to generate steering docs and add a rule, and that steering turns
> generic output into code that fits your conventions. [Session 2](02-your-first-project.md) puts
> this to work on a real feature.

---

## Task 4 — Plan a bigger feature with a spec

**Specs** turn an idea into a plan in three phases — **Requirements → Design → Tasks** — *before*
code is written. Here you'll create one for a deliberately larger feature and see how Kiro breaks
it down.

**What to do:**

1. Click the **Spec** button in chat, or the **`+`** in the panel's **Specs** section.
2. Describe something bigger than a script — a small service:

   > *"Add a spec for a dice-rolling REST API: an endpoint that accepts dice notation, returns
   > the roll as JSON, and keeps a history of the last 20 rolls."*

3. Walk the **Requirements** phase and read the structured, testable acceptance criteria (EARS
   notation). Then look at the **Design** (endpoints, data model) and the **Tasks** Kiro drafts.
4. *(Optional)* Click **one** task in `tasks.md` to let Kiro implement just that slice, and watch
   it move to **In Progress → Done**.

Notice how a one-line idea became a reviewable engineering plan. That's the heart of spec-driven
development — and you'll run a full spec in Session 2.

> ✅ **You learned:** where specs live, the three phases, and how Kiro decomposes complex work
> into trackable tasks.

---

## Task 5 — Pull in real-world data with MCP

**MCP (Model Context Protocol)** connects Kiro to outside tools and data. Kiro ships with a
built-in **`fetch`** server — let's switch it on and *write code from real data*. No API key needed.

**What to do:**

1. In the Kiro panel, **enable MCP**, then click the **edit (pencil) icon** next to MCP to open
   its JSON config.
2. Find the built-in **`fetch`** server and set `"disabled": false`, then save.

👉 **Try it — fetch, then generate code:**

> *"#[fetch] Fetch https://api.github.com/repos/awslabs/aidlc-workflows and write `stars.py`
> that prints the repo's star count. Match my coding standards."*

**Then** run `python stars.py`. Kiro reached out through the `fetch` tool, inspected the real API
response, and wrote code against it. (Adding other servers — like web search — is just another
entry in that JSON with a `command`, `args`, and an API key in `env`.)

> ✅ **You learned:** how to enable an MCP server, invoke a tool with `#[...]`, and have Kiro build
> code from live external data.

---

## Task 6 — Let Kiro handle something complex (plus hooks & powers)

Time to see the ceiling. Instead of small edits, give Kiro a **multi-file, complex** ask in one go.

👉 **Try it — one prompt, a whole small program:**

> *"Build a playable text adventure in Python: at least three connected rooms, an inventory I can
> pick up and drop items from, a win condition, and save/load to a JSON file. Split it into
> sensible modules, follow my coding standards, and add pytest tests for the core logic."*

**Then** run it and play:

```bash
python game.py
```

Watch Kiro plan the structure, create **multiple files**, and wire them together — the same tool
that wrote your one-line dice roller just built a small program. That's the range.

**While you're here, look at two more panels:**

- **Agent Hooks** — automations that run on events. 👉 Open the **Agent Hooks** section, click
  **`+`**, choose a **file-save** trigger with a file pattern like `**/*.py`, and instruct it:
  *"When I save a Python file, run pytest and summarize any failures."* Save a file and watch it
  fire. (Session 2 wires a hook for real.)
- **Powers** — downloadable bundles of best practices (MCP + steering + hooks) from experts and
  partners. 👉 Open the **Powers** section and skim what's available — one click pulls in context
  and actions you'd otherwise set up by hand.

> ✅ **You learned:** Kiro scales from a one-liner to a multi-file program; hooks automate chores
> on triggers; powers package best practices you can pull in with a click.

---

## You're warmed up

In a handful of tasks you drove every core surface of Kiro **and wrote real, running code** the
whole way:

**chat → iterate + rollback (timeline) → steering → specs → MCP → a complex multi-file build →
hooks & powers.**

You saw both ends of the range — trivial edits *and* a program built in one shot. Now do it for
real.

**Next:** [Session 2 — Your first project →](02-your-first-project.md) — take one feature from
idea to working code using the full build loop.
