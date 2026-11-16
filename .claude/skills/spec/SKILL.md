---
name: spec
description: Turn a case brief into a spec and a slice plan, before any code is written. Use when the user types /spec or pastes a brief and asks to start.
disable-model-invocation: true
argument-hint: "[leave empty: reads docs/BRIEF.md]"
---

Turn the brief into a spec and a plan. **Write no application code in this step.**

## Steps
1. **Read the brief** from `docs/BRIEF.md`. If short plain text was given after `/spec` ($ARGUMENTS), save it verbatim to `docs/BRIEF.md` first. If the file is still empty, ask the user to save the brief into `docs/BRIEF.md` (open it in an editor and paste) and run `/spec` again, then stop.
2. **Ask before assuming.** List up to five questions where the brief is ambiguous and the answer would change what gets built (users, data available, success measure, constraints). Ask them in one message and wait. If the user says to proceed, take the most reasonable reading and record each assumption in the spec.
3. **Write `docs/SPEC.md`** using its template headings. Keep it to about a page. Scope must fit the time box in the brief (default: 5 hours total, with about 3 hours of building). Be explicit about what is out of scope.
4. **Write `docs/PLAN.md`:** 3 to 5 slices in build order. Each slice works end to end and can be shown, has a one-line goal, what gets built, how it will be tested, and a rough time estimate. The last slices are always evaluation and wrap-up.
5. **Record the first decisions** in `docs/DECISIONS.md`. At minimum: the overall approach (plain software, fixed workflow, retrieval or agent) with the alternatives considered and why they lost, and the choice of model or provider.
6. **Fill the Project section** at the top of `CLAUDE.md` (five lines).
7. **Replace `README.md`** with `docs/kit/README_TEMPLATE.md`, filling in only the title and problem statement for now.
8. **Commit:** `spec: scope and plan`.
9. **Stop and report.** Summarise the spec and plan in under 15 lines, list your assumptions, and suggest: "Review and edit `docs/SPEC.md` and `docs/PLAN.md`, then run `/codex-review plan` for a second opinion, or `/slice` to start building."
