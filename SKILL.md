---
name: scientific-research
description: Research workspace governance for code-heavy scientific projects with strict directory, backup, review, and explainer-site conventions. Use when Codex needs to organize or operate inside a research project that should maintain sibling `backUp`, `ansisly`, `results`, and `else` directories; create or review analysis scripts; manage project plans, reviews, todo lists, and progress pages; or update conversation backups after finishing research work.
---

# Scientific Research

Use this skill to keep a research code workspace consistent across conversations. Treat the literal folder names from the user's convention as canonical, including the spelling `ansisly`.

## Workflow

1. Identify the project root whose sibling directories should include `backUp`, `ansisly`, `results`, and `else`.
2. Ensure those four sibling directories exist before any other file creation or code work.
3. Choose the target project under `ansisly`:
   - Reuse an existing first-level project folder when one already matches the current topic.
   - Otherwise create a new first-level project folder named after a concise project summary.
4. Inside that project, ensure the required first-level folders exist: `script`, `data`, `plan`, `review`, `todolist`, `progress`.
5. Read `references/workspace-rules.md` before creating or moving scripts, data, results, or auxiliary files.
6. When the task needs a research explainer frontend or a `progress.html` page, reuse the exact prompt templates in `references/frontend-prompts.md`.
7. When the task involves backup logging, follow `references/backup-format.md` exactly. Update backup only after the task is actually finished.

## Required Behaviors

- Create missing directory scaffolding before writing scripts or results.
- Keep analysis scripts out of the first level of `ansisly/<project>/script`; use named subfolders for grouped work and method variants according to the workspace rules.
- Keep project goals and architecture in `plan/headplan.txt`; update it only when the research objective or overall framework changes.
- Create a new `todolist/todolist_MMDDHH.md` during each qualifying conversation.
- Create review files using the naming rules from the workspace reference when reviewing scripts.
- Create or update `progress/progress.html` whenever it is missing. Also update it whenever the current conversation changes more than 100 lines of code.
- Create the explainer project folder `progress/项目讲解` whenever it is missing.
- Mirror each first-level `ansisly/<project>` folder with a same-named first-level folder under `results`, and store outputs inside timestamped `results_MMDDHH` subfolders.
- Use `else` only for one-off scripts, tests, downloads, or raw temporary artifacts, and clean disposable one-off files as described in the workspace rules.
- Finish every qualifying conversation by appending a backup record in `backUp`.

## Frontend Guidance

When creating the explainer site or progress page:

- Prefer available local frontend/design skills such as `frontend-design`, `build-web-apps:frontend-app-builder`, `design-taste-frontend`, and `figma`.
- If the user names a skill that is not installed, do not fabricate it. Use the closest available local skill and say which fallback you used.
- Keep the source research directories read-only unless the user explicitly asks to modify them.
- Show missing data, missing results, and read failures honestly in the generated UI. Do not invent content.

## Deliverables Checklist

Before finishing, verify all of the following that apply to the task:

- Required root sibling directories exist.
- The target `ansisly/<project>` structure follows the workspace rules.
- New scripts, data, plans, reviews, todos, progress pages, and results landed in the right folders.
- `progress.html` and `项目讲解` exist when required.
- A backup entry was appended after the work was completed.
