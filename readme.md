# SpecPilot  
A drop-in rule file that brings GitHub-style **spec-driven development** to any AI-powered editor.  
Write the spec → generate the plan → ship small tasks. No more ad-hoc prompts.

---

## 🚀 30-second start

1. Copy the rule file into your repo (see per-editor paths below).  
2. Open the command palette and run:  
   - **Cursor** → “Apply Rule: SpecPilot”  
   - **Cline** → `cline rules load .clinerules/specpilot.mdc`  
   - **GitHub Copilot** → simply mention `@specpilot` in any chat.  
3. Type `/specify` and watch the AI write the first version of your spec.  
4. Continue with `/plan` → `/tasks` → code → repeat.

---

## 📁 Installation

| Editor | Where to place the file | Auto-load? |
|---|---|---|
| **Cursor** | `.cursor/rules/specpilot.mdc` | ✅ |
| **Cline** | `.clinerules/specpilot.mdc` (or any file listed in `cline.rules`) | ✅ |
| **GitHub Copilot** (VS Code) | `.github/copilot-instructions.md` | ✅* |

\*Copilot treats the file as global instructions; prefix any prompt with `@specpilot` to trigger the workflow.

---

## 🧩 Commands you get

| Command | When to use | One-liner prompt you can paste |
|---|---|---|
| `/specify` | Starting a feature or when requirements feel fuzzy | “`/specify` create a spec for a rate-limited API key service” |
| `/plan` | After the spec is stable | “`/plan` choose stack and architecture for the above spec” |
| `/tasks` | Ready to code | “`/tasks` split the plan into 1-day PR-able chunks” |

The rule guarantees the AI always:  
1. researches first (no assumptions),  
2. validates against the spec continuously,  
3. writes tests for the **requirement**, not the code,  
4. updates the spec when reality diverges.

---

## 🛠️ Example session (Cursor)

```
User: /specify  
AI: writes SPEC.md with goals, journeys, acceptance criteria.  
User: /plan  
AI: writes PLAN.md with NestJS + Postgres + Redis, diagrams, risks.  
User: /tasks  
AI: writes TASKS.md with 5 tickets, each < 200 LOC, ordered by dependency.  
User: start task-1  
AI: codes, tests, updates SPEC.md with discovered edge case.  
```

Same flow works in Cline or Copilot chat—only the UI changes.

---

## 🧪 Customising

Edit the `.mdc` file to:

* change the quality gates,  
* add your tech-stack defaults,  
* inject company-wide standards.

The file is plain markdown + front-matter; no compilation step.

---

## 📜 License

MIT – feel free to fork, vendor, or PR improvements.

---

## 🤝 Contributing

Issues and PRs welcome in the [SpecPilot repo](https://github.com/your-org/specpilot).  
Add your own editor integration under `/integrations`.

---

**Happy spec-driven shipping!**
