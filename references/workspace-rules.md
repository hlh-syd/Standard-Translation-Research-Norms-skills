# Workspace Rules

Apply these rules literally. Do not silently rename folders such as `ansisly`.

## Root Sibling Directories

Check whether the project root has the sibling directories `backUp`, `ansisly`, `results`, and `else`.

- Create any missing directory before other work starts.

## ansisly

Keep all analysis projects under `ansisly`. Do not place scripts directly under the first level of `ansisly`.

Each first-level project folder under `ansisly` must contain:

- `script`
- `data`
- `plan`
- `review`
- `todolist`
- `progress`

Choose the first-level project folder name from a concise project summary or reuse the existing established project name.

### script

Store scripts only inside `script`.

- When creating a new script grouping, create a folder named after the script purpose.
- When trying a new method branch for an existing script, create a folder named after the original script.
- Inside that folder, create a subfolder named after the changed aspect.
- Name each variant file as `<original_script_name>_<index>.py`.

Example:

```text
ansisly
  Casual gene
    script
      dataset.py
      Model.py
      Model
        更换模型
          Model_2.py
        改变数据来源
          Model_3.py
```

### plan

Store planning files under `plan`.

- Keep one project-specific `headplan.txt` with the research goal and framework.
- Update `headplan.txt` only when the project goal or research framework changes.
- Store subplans as `plan_MMDDHH.txt`.
- Example: `plan_051612.txt`

### review

Store script review reports under `review`.

Naming rules:

- Review all scripts under `script`: `script_MMDDHH.md`
- Review one script: `<script_name>_MMDDHH.md`
- Review multiple scripts: `multiple_MMDDHH.md`

### todolist

Store action lists under `todolist`.

- Name each file `todolist_MMDDHH.md`
- Create a new todo list during each qualifying conversation

### progress

Keep two deliverables under `progress`:

- `progress.html`
- `项目讲解` folder

`progress.html` must compare the plan in `headplan.txt` with the current script progress, show branches in the approach, and present progress on a timeline.

`项目讲解` must be a complete explainer frontend project with strong visuals and rich narration for non-experts.

- Create either deliverable when missing.

### data

Store all datasets used by scripts under `data`.

Top-level structure:

- `noTracke`
- `trackled`

Inside `trackled`, keep:

- `Current`
- `Unused`

Rules:

- Unprocessed data goes into `noTracke`.
- Processed data goes into `trackled`.
- Currently used processed data goes into `trackled/Current`.
- Processed but not currently used data goes into `trackled/Unused`.
- For active datasets, mirror the relevant script path under `trackled/Current`.

Example:

- Script path: `ansisly/CasualGene/script/更换数据/dataset2.py`
- Dataset file: `eQt.csv`
- Store dataset at: `ansisly/CasualGene/data/trackled/Current/更换数据/dataset2/eQt.csv`

## results

Mirror every first-level project under `ansisly` with a same-named first-level directory under `results`.

- Create the project folder under `results` if missing.
- For every conversation output batch, create a new timestamped folder named `results_MMDDHH`.
- Store that conversation's output files inside the new `results_MMDDHH` folder.

## else

Use `else` for tests, one-off scripts, downloads, and other non-project artifacts.

Structure:

- `file`
- `rawDone`
- `oneFile`

Rules:

- Put one-off scripts and throwaway tests in `oneFile`.
- Put outputs from download scripts into `rawDone/<date-folder>`.
- Do not modify files already stored in `rawDone`.
- Put non-one-off auxiliary scripts into `file/<date-folder>`.

Cleanup rule for each qualifying conversation:

- Search for disposable test files and one-off download scripts in `else` and clean them up.
- Do not touch `rawDone`.

