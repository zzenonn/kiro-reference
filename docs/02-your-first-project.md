# Session 2 — Your First Project

*Hands-on. This is where you build. You'll take one feature from idea to working code using
steering → specs → tasks → hooks, with the timeline as your safety net.*

> If you skipped [Session 1](01-getting-started-with-kiro.md), run through its warm-up tasks first —
> this guide assumes you've already found the chat, steering, specs, and hooks panels.

---

## What you'll do

1. Open a project in Kiro and start a chat.
2. Generate **steering files** so Kiro understands your project.
3. Turn a feature idea into a **spec** (requirements → design → tasks).
4. **Execute the tasks** and watch them build your feature.
5. Automate a chore with an **agent hook**.
6. Use the **timeline** to roll back fearlessly.

Focus on the *workflow*, not on shipping something huge. A small, finished feature teaches more
than a big, half-done one.

---

## Bring your own idea

Don't overthink it — pick something **small and fun** you'd actually enjoy building. The workflow
is identical whatever you choose. A few starters to spark ideas:

- 🕹️ **Pac-Man (or Snake / Breakout) clone** — a grid, some ghosts, a score counter.
- ✅ **Habit tracker** — check off habits, keep a streak, show a weekly grid.
- 🤖 **Discord/Slack bot** — responds to a slash command with something delightful.
- 🍜 **Recipe randomizer** — "what should I cook?" from a list of ingredients.
- 🌦️ **ASCII weather** — fetch a forecast, draw it in the terminal.
- 🎲 **Dice/RPG roller** — parse `2d6+3`, roll, and explain the result.
- 📇 **Tiny CRM / contact book** — add, search, tag people.

Pick one. Then create an **empty folder** for it (Kiro will help you fill it) — e.g.:

```bash
mkdir my-kiro-project && cd my-kiro-project
```

> Facilitator tip: budget ~5 minutes for people to choose. Encourage the fun option over the
> "impressive" one — energy matters more than scope on day one.

---

## Step 1 — Open your project in Kiro

1. **Open the folder:**
   - click **File > Open Folder** and select your project directory, **or**
   - drag and drop the folder into Kiro, **or**
   - run `kiro .` from inside the folder in your terminal.
2. **Open the Kiro panel** — click the **Kiro Ghost icon** in the activity bar (left sidebar).
   This panel is your home for all of Kiro's AI features.
3. **Start a chat session** — the chat pane is open by default. This is where you talk to Kiro.

---

## Step 2 — Set up steering files

Steering files give Kiro context about your project so it stops guessing — you got a first taste
of this in [Session 1, Task 3](01-getting-started-with-kiro.md). Now you'll make them count.

1. In the Kiro panel, choose **Generate Steering Docs**.
2. Kiro creates files in **`.kiro/steering/`** describing:
   - **Product** — what you're building and its purpose.
   - **Tech** — your stack and frameworks.
   - **Structure** — project layout and conventions.
3. **Open and read them.** On a brand-new project they'll be sparse — that's expected. Edit them
   to reflect what you actually intend to build. For example, in `product.md`:

   ```markdown
   # Product
   A browser-based Pac-Man clone. Single player, keyboard controls,
   one maze, four ghosts, a score, and a game-over screen. Fun over realism.
   ```

4. **Add a custom steering file** — click the **`+`** in the steering section to capture things
   like coding standards, workflows, or team best practices. A quick one to try:

   ```markdown
   # Coding Standards
   - Keep functions small and named by intent.
   - No frameworks unless the spec calls for one.
   - Every module gets a matching test file.
   ```

> ✅ **Checkpoint:** you should have a `.kiro/steering/` folder with at least product, tech, and
> structure files that reflect *your* idea.

---

## Step 3 — Build a feature with a spec

Specs turn a high-level idea into an implementation plan through **three phases**:

1. **Requirements** — user stories with acceptance criteria in **EARS notation**.
2. **Design** — technical architecture and approach.
3. **Tasks** — discrete, trackable implementation steps.

### Create your first spec

1. In your chat session, click the **Spec** button — or choose the **`+`** in the panel's
   **Specs** section.
2. **Describe the feature in natural language.** Keep the first one bite-sized. Examples:
   - *"Render the Pac-Man maze as a grid and let the player move with arrow keys."*
   - *"Add a habit list where I can add a habit and toggle it done for today."*
   - *"Add a `/roll 2d6+3` command that parses the dice notation and returns the total."*
3. **Follow the guided workflow.** Kiro walks you through each phase — review and refine at each
   step before moving on:
   - **Requirements phase** — Kiro structures your requirements in EARS notation. Read them; fix
     anything that doesn't match your intent.
   - **Design phase** — Kiro documents the architecture and components. This is the cheapest place
     to catch a bad approach, so push back here.
   - **Tasks phase** — Kiro breaks the work into discrete tasks.

> 💡 The spec is a conversation, not a form. If a requirement is wrong, say so — Kiro updates it.

---

## Step 4 — Execute the spec tasks

Once the spec is complete:

1. **Review the generated tasks** in the spec's **`tasks.md`**.
2. **Execute a task** by clicking the individual task item. Kiro implements just that slice.
3. **Track progress** — tasks update automatically to **In Progress**, then **Done**.

Work task by task. After each one, glance at the code Kiro wrote and run your project to see it
grow. If a task's result isn't right, tell Kiro what to change before moving to the next.

> ✅ **Checkpoint:** at least one task marked **Done** and something you can actually run.

---

## Step 5 — Automate a chore with a hook

**Agent hooks** eliminate manual work by running predefined actions automatically when files are
created/saved/deleted, on manual triggers, or on other lifecycle events.

1. **Open the Agent Hooks section** in the Kiro panel and click **`+`** to create a hook.
2. **Describe what to automate** in natural language, for example:
   - *"When I save a source file, create or update its matching test file."*
   - *"When I save the maze module, re-check that every ghost has a start position."*
3. **Configure the hook:**
   - **Event type** — file events (created, saved, deleted), prompt/agent lifecycle events,
     spec task events (pre/post task), or a **manual trigger**.
   - **File pattern** — which files trigger it (e.g., `src/**/*.js`).
   - **Instructions** — the specific actions to perform.
4. **Test it** — save a matching file and watch the hook fire.

> Start with one small hook. "Keep tests in sync on save" is a great first one because you'll
> *see* it work immediately.

---

## Step 6 — Explore fearlessly with the timeline

You don't have to get it right the first time.

- Kiro **snapshots each modified file** as you work.
- Use the **timeline / checkpoints** to **roll back** to an earlier point if an approach goes
  sideways.
- This is your **safety net** for trying a second (or third) approach to a task without fear.

Try it: after a task, deliberately ask Kiro for a different approach, compare, then roll back to
whichever you preferred.

---

## Wrap-up

You've now run the full Kiro build loop on your own idea:

**steering** (context) → **spec** (requirements → design → tasks) → **execute tasks** →
**hook** (automation) → **timeline** (safety net).

That loop scales from a Pac-Man clone to a production feature — the discipline is the same.

**Next:** [Session 3 — AI-DLC with Kiro →](03-aidlc-with-kiro.md) — a repeatable delivery
workflow layered on top of everything you just learned.
