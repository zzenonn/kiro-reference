# Session 1 — Get Your Feet Wet with Kiro

*Hands-on. The slides gave you the **why**; this session gets your hands on the tool by building
**real, visual web pages** — starting with a single button, growing into a full-stack app with a
Python backend, and ending with Kiro building a playable canvas game in one shot. The point isn't
the app; it's learning where the buttons are and seeing that Kiro handles both trivial and
genuinely complex work, across more than one language.*

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
- **A web browser** — that's your entire runtime. To *see* a page, open the `.html` file in it.

> Make a scratch folder to work in:
> ```bash
> mkdir kiro-playground && cd kiro-playground
> ```
>
> 💡 Tip: after Kiro writes a page, keep the browser tab open and just **refresh** it after each
> change to watch your work evolve.

---

## Task 1 — Open a project and build your first page

**What to do:**

1. **Open your folder** in Kiro — click **File > Open Folder**, drag-and-drop the folder onto
   Kiro, or run `kiro .` from inside it.
2. **Open the Kiro panel** — click the **Kiro Ghost icon** 👻 in the activity bar (left sidebar).
   This is home base for every feature today.
3. **Find the chat pane** — it's open by default. This is where you talk to Kiro.

👉 **Try it — your first prompt.** Type this into the chat and send it:

> *"Create `index.html`: a single page with a big 'Roll' button. When I click it, roll one
> six-sided die and show the result in large text. Put everything in one file for now."*

**Then:** review the file Kiro proposes, **accept** it, and **open `index.html` in your browser**.
Click the button.

You just went from a sentence to something running on screen.

> ✅ **You learned:** how to open a project, where the chat lives, and that Kiro writes real,
> viewable code from a plain-English prompt.

---

## Task 2 — Iterate, then undo it fearlessly with the timeline

Let's grow the page — and practice rolling back so you'll never be scared to experiment.

👉 **Try it — make it richer:**

> *"Add a text box where I can type dice notation like `2d6+3`. On Roll, parse it, show each die
> as a large number, and display the total. Style it so it looks clean and centered."*

**Then:** refresh the browser, type `2d6+3`, and click Roll.

👉 **Try a different look:** ask Kiro to restyle it so you can compare:

> *"Give it a dark theme with dice that briefly animate when rolled."*

**Now roll it back:**

1. Open the **timeline / checkpoints** for the session (in the chat/execution view).
2. **Roll back** to the checkpoint *before* the dark-theme change. Refresh the browser and watch
   the previous version return — Kiro restores the file from its snapshot.

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
   - Separate concerns: HTML in .html, CSS in styles.css, JavaScript in app.js.
   - Vanilla JavaScript only — no frameworks or CDNs.
   - Use semantic HTML and accessible labels (aria-* where needed).
   ```

👉 **Try it — feel the difference.** Ask for a change and watch Kiro honor the rules you just wrote:

> *"Refactor my dice roller to follow my coding standards."*

**Then** refresh the browser — it should look the same, but the code is now split into
`index.html`, `styles.css`, and `app.js` with accessible markup, *because your steering told it to*.

> ✅ **You learned:** how to generate steering docs and add a rule, and that steering turns
> generic output into code that fits your conventions. [Session 2](02-your-first-project.md) puts
> this to work on a real feature.

---

## Task 4 — Go full-stack with a spec (enter Python)

So far everything has run in the browser. Now let's go bigger — add a **backend** — and let a
**spec** plan it. Specs turn an idea into a plan in three phases (**Requirements → Design →
Tasks**) *before* code is written. This also shows Kiro isn't a one-language tool: your frontend
stays HTML5, and the backend will be Python.

**What to do:**

1. Click the **Spec** button in chat, or the **`+`** in the panel's **Specs** section.
2. Describe a full-stack feature that needs a server:

   > *"Add a spec for a dice-rolling web app with a Python backend: a small Flask API with a
   > `/roll` endpoint that accepts dice notation and returns JSON, and a `/history` endpoint that
   > returns the last 20 rolls. The existing HTML5 page should call the API instead of rolling in
   > the browser."*

3. Walk the **Requirements** phase and read the structured, testable acceptance criteria (EARS
   notation). Then look at the **Design** (endpoints, data model, how the frontend talks to the
   backend) and the **Tasks** Kiro drafts.
4. *(Optional)* Click **one** task in `tasks.md` to let Kiro implement just that slice — e.g. the
   Flask app skeleton — and watch the task move to **In Progress → Done**. To run it later you'd
   `pip install flask` and start the server, but reading the plan is enough for now.

Notice how a one-line idea became a reviewable, full-stack engineering plan — spanning HTML,
JavaScript, *and* Python. That's the heart of spec-driven development, and you'll run a full spec
in Session 2.

> ✅ **You learned:** where specs live, the three phases, and how Kiro decomposes complex work
> into trackable tasks.

---

## Task 5 — Pull in real-world data with MCP

**MCP (Model Context Protocol)** connects Kiro to outside tools and data. Kiro ships with a
built-in **`fetch`** server — let's switch it on and *build UI from real data*. No API key needed.

**What to do:**

1. In the Kiro panel, **enable MCP**, then click the **edit (pencil) icon** next to MCP to open
   its JSON config.
2. Find the built-in **`fetch`** server and set `"disabled": false`, then save.

👉 **Try it — fetch, then build a visual:**

> *"#[fetch] Fetch https://api.github.com/repos/awslabs/aidlc-workflows and create `stars.html`
> — a styled card that displays the repo name, description, and star count. Follow my coding
> standards."*

**Then** open `stars.html` in your browser. Kiro reached out through the `fetch` tool, inspected the
real API response, and built a UI around it. (Adding other servers — like web search — is just
another entry in that JSON with a `command`, `args`, and an API key in `env`.)

> ✅ **You learned:** how to enable an MCP server, invoke a tool with `#[...]`, and have Kiro build
> a visual interface from live external data.

---

## Task 6 — Let Kiro handle something complex (plus hooks & powers)

Time to see the ceiling. Instead of small edits, give Kiro a **multi-file, complex** ask in one go.

👉 **Try it — one prompt, a whole playable game:**

> *"Build a playable Breakout game using an HTML5 canvas: paddle controlled by the arrow keys, a
> ball that bounces off walls and bricks, a score, lives, and a game-over screen with restart.
> Split it into `index.html`, `styles.css`, and `game.js`, and follow my coding standards."*

**Then** open `index.html` in your browser and **play it**.

Watch Kiro plan the structure, create **multiple files**, and wire up canvas rendering, collision,
and game state — the same tool that wrote your one-button page just built a real game. That's the
range.

**While you're here, look at two more panels:**

- **Agent Hooks** — automations that run on events. 👉 Open the **Agent Hooks** section, click
  **`+`**, choose a **file-save** trigger with a file pattern like `**/*.js`, and instruct it:
  *"When I save a JavaScript file, review it for bugs and accessibility issues and summarize what
  you'd fix."* Save a file and watch it fire. (Session 2 wires a hook for real.)
- **Powers** — downloadable bundles of best practices (MCP + steering + hooks) from experts and
  partners. 👉 Open the **Powers** section and skim what's available — one click pulls in context
  and actions you'd otherwise set up by hand.

> ✅ **You learned:** Kiro scales from a one-button page to a multi-file game; hooks automate
> chores on triggers; powers package best practices you can pull in with a click.

---

## You're warmed up

In a handful of tasks you drove every core surface of Kiro **and built real, working code** the
whole way — from a browser page to a Python backend:

**chat → iterate + rollback (timeline) → steering → full-stack spec (HTML + Python) → MCP →
a complex multi-file game → hooks & powers.**

You saw both ends of the range — a single button *and* a playable game — and Kiro spanning
frontend and backend in one project. Now do it for real.

**Next:** [Session 2 — Your first project →](02-your-first-project.md) — take one feature from
idea to working code using the full build loop.
