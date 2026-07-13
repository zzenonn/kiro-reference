# Session 1 — Getting Started with Kiro

*The concepts, in the order that makes them click. Read this before you touch the keyboard.*

By the end you'll understand **why** Kiro exists, **what** spec-driven development is, and the
**surfaces** (IDE, CLI) and **building blocks** (steering, specs, hooks, MCP, powers) you'll use
for the rest of the day.

> 📚 **Official companion:** this session pairs with Kiro's own
> [Your first project](https://kiro.dev/docs/getting-started/first-project/) guide. Read this for
> the concepts and *why*; use the official guide (and [Session 2](02-your-first-project.md)) for
> the click-by-click *how*.

---

## 1. The promise of agentic development

AI agents can do more than autocomplete. When you truly work *with* them, you get:

- **Autonomy** — agents take on and complete increasingly challenging tasks on their own.
- **True collaboration** — developers and agents work together to get more done.
- **Higher quality** — agents handle the heavy lifting: increasing test coverage, documenting
  code, optimizing performance, and fixing security vulnerabilities.

That's the upside. But most AI coding tools don't get you there. Why not?

---

## 2. The challenges with AI development

Three things get in the way today:

- **Scaling AI development** — AI coding tools excel at small tasks but *fail on complex projects*.
- **Limited control** — existing tools make it hard to collaborate with and manage agents.
- **Code quality** — getting a project from proof-of-concept to production *while maintaining
  quality* becomes increasingly difficult.

In short: vibe coding gets you a demo, not a product.

---

## 3. The question

> **What would a development experience look like if it could take full advantage of working with AI agents?**

Hold that question. The rest of Kiro is one answer to it.

---

## 4. The solution: spec-driven development

> **Vibe coding ships the prototype. Traditional SDLC practices ship the product.**

Kiro brings the discipline of the software development lifecycle to AI coding:

```
PLANNING & DESIGN → IMPLEMENTATION →  ⟳ (issues found) → TESTING & QA → DEPLOYMENT → MAINTENANCE
```

Instead of jumping straight to code (where issues are found late and loop back expensively),
Kiro turns your prompt into a **spec** — clear requirements, a system design, and discrete tasks —
*before* implementation starts. Kiro helps developers and engineering teams ship high-quality
software with AI agents.

You'll build a real spec in [Session 2](02-your-first-project.md).

---

## 5. Kiro the AI IDE — from prototype to production

The Kiro IDE is where spec-driven development lives. Its core capabilities:

### Spec-driven development
- Kiro turns your prompt into clear **requirements, system design, and discrete tasks**.
- You **iterate with Kiro** on the spec and architecture *before* code is written.
- Kiro agents implement the spec while **keeping you in control**.

### Agent hooks
- **Delegate tasks to AI agents that trigger on events** — like "on file save."
- Agents **autonomously execute in the background** based on your pre-defined prompts.
- Hooks help you **scale your work**: generating documentation, unit tests, or optimizing
  code performance without manual effort.

### Advanced context management
Kiro's answer to "the agent doesn't know my project" is context you control:

- **Steering files** — configure how Kiro agents work *per project* (conventions, stack,
  architecture, preferences). More on why this matters below.
- **MCP (Model Context Protocol)** — connect Kiro to docs, databases, APIs, and other tools
  natively (see §6).
- **Drop in an image** of your UI design, or a photo of an architecture whiteboard session,
  and Kiro can use it to guide implementation.

### Steering in action — with vs. without

Steering files live in `.kiro/steering/` and are loaded automatically so Kiro shares the
context an experienced teammate would have. Here's why they matter. Imagine the same prompt:

> *"Add an endpoint to save a new user."*

**Without steering** — Kiro has no project context, so it guesses:

```python
# Guesses a framework, an ORM, naming, and structure — often the wrong ones.
@app.route('/api/saveUser', methods=['POST'])   # camelCase route
def saveUser():
    conn = sqlite3.connect('db.sqlite')          # raw sqlite3
    cur = conn.cursor()
    cur.execute("INSERT INTO users ...")          # inline SQL, no model
    return {'ok': True}
```

You now spend time correcting the framework, the naming, the data layer, and where the file
even goes.

**With steering** — a `tech.md` steering file says *"Flask + SQLAlchemy, snake_case routes,
models in `app/models/`, blueprints in `app/routes/`"*:

```python
# app/routes/users.py  — matches your conventions the first time.
from app.models.user import User
from app.extensions import db
from . import users_bp

@users_bp.route('/users', methods=['POST'])       # snake_case, blueprint
def create_user():
    user = User(**request.get_json())
    db.session.add(user)
    db.session.commit()
    return jsonify(user.to_dict()), 201
```

Same prompt, dramatically less rework. **Steering turns "plausible generic code" into "code that
fits your project."** You'll generate these files in [Session 2](02-your-first-project.md).

### Timeline & checkpointing
- **Roll back** to earlier points in the execution log.
- A **safety net** to explore multiple approaches to a problem.
- Kiro **snapshots the contents of each modified file** and restores that snapshot when you
  revert to a checkpoint.

---

## 6. MCP — connecting Kiro to the outside world

**Model Context Protocol (MCP)** lets Kiro reach beyond your codebase to:

- Access specialized knowledge bases and documentation.
- Integrate with external APIs and services.
- Use domain-specific tools and utilities.
- Connect to databases and cloud services.

Kiro ships with a built-in **`fetch`** MCP server (disabled by default — you flip it on).
You can add any MCP server by asking Kiro or editing a small JSON config, for example:

```json
{
  "mcpServers": {
    "web-search": {
      "command": "uvx",
      "args": ["mcp-server-brave-search"],
      "env": { "BRAVE_API_KEY": "your-api-key-here" },
      "disabled": false,
      "autoApprove": ["search"]
    }
  }
}
```

Once configured, you use MCP tools by **asking questions** ("search for the latest React 18 best
practices"), **referencing tools explicitly** (`#[fetch] ...`), or **combining them with hooks
and specs**. MCP is a *context* capability — you'll see it conceptually here; the day's hands-on
focus stays on the build loop.

---

## 7. Kiro in the terminal — the CLI

Kiro is also a CLI (`kiro`), so you can **turn ideas into implementation with speed and
precision while staying in complete control**. Highlights:

### Custom agents
- Optimize Kiro for specific tasks — documentation, code reviews, unit tests.
- Provide **pre-approved tool permissions, context files, and prompts**.
- Kiro **builds on your feedback**, delivering smarter defaults while reducing interruptions.
- Run agents **in parallel with Kiro subagents** — isolated context, independent execution,
  and task summaries on completion.

### Headless execution
- Run the Kiro CLI **programmatically inside CI/CD pipelines** to ship releases faster.
- Enable automation by **executing prompts without user input** locally.
- Authenticate with **API keys, device codes, or PKCE**.

---

## 8. Power, flexibility, and security

Kiro is built to be adopted by real teams:

- **Familiar environments** — Kiro imports your VS Code settings into a streamlined,
  AI-ready environment, and is available in the terminal for macOS, Linux, and Windows.
- **Cutting-edge models** — access frontier and open-weight AI models. Pick the right one
  for the job, or let Kiro decide by selecting **Auto**.
- **Enterprise-grade security** — built and operated following the same security, governance,
  and encryption standards as the AWS cloud infrastructure.

---

## 9. Kiro powers — sharable best practices

**Powers extend Kiro agent capabilities through sharable best practices.**

A **Kiro power** is a bundle of sharable knowledge and best practices that may contain:
- **MCP servers** for access,
- **Steering files** for context,
- **Hooks** for actions.

Powers flow from **use cases** (ISV use cases, expert use cases) into reusable powers, and out
to the **community** via a community exchange.

### Benefits
- **Targeted context for fast decisions** — dynamic loading to avoid context overload,
  one-click download for IDE use, and the option to customize a power.
- **Knowledge from ISVs and experts** — best practices from ISVs for dev tools, opinionated
  guidance from experts, and a mechanism to share powers with the community.
- **Dev-to-deployment use cases** — application development spanning full-stack use cases,
  automated code build and deployment, and observability on application performance and security.

### Partners (examples)
Powers span the whole stack: **Figma** (UI), **Supabase** (backend), **Stripe** (full-stack),
**Postman** (API), **Strands Agents SDK** (agent dev), **Neon** (databases),
**Netlify / HashiCorp / AgentCore** (deployment), and **Datadog / Dynatrace** (observability).

---

## Recap — the vocabulary you now own

| Term | One-liner |
|------|-----------|
| **Spec-driven development** | Turn a prompt into requirements → design → tasks *before* coding. |
| **Steering files** | Per-project context that guides how Kiro behaves (`.kiro/steering/`). |
| **Specs** | Structured requirements, design, and tasks for a feature (`.kiro/specs/`). |
| **Agent hooks** | Automations that trigger on events (e.g., file save) or manually. |
| **MCP** | Model Context Protocol — connect Kiro to docs, APIs, databases, and tools. |
| **Timeline / checkpointing** | Snapshot-and-rollback safety net for exploring changes. |
| **Custom agents** | Task-specialized agents with pre-approved tools and context (CLI). |
| **Powers** | Sharable bundles of MCP + steering + hooks. |

**Next:** [Session 2 — Your first project →](02-your-first-project.md)
