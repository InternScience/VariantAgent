# VariantAgent repo update: README rewrite, figure swap, skills/ purge

## Context

The GitHub repo `github.com/InternScience/PGI` (being renamed to
`github.com/InternScience/VariantAgent`, matching the manuscript's Code
Availability statement) currently ships a developer-quickstart README built
around an older draft ("pgi ms - Google 文档.pdf", already gitignored and not
used further) and a 3-agent description ("VariantsAgent": Planner / Execution
/ Self-reflection).

The source of truth is now exclusively the local file `初稿投递nature.pdf`
(64-page Nature submission draft, not to be committed or published). All
architecture, terminology and benchmark numbers in the README must come from
this document, not from the old draft or the current README's stale content.

The user also supplied a new architecture diagram (pasted image, currently
saved at `20260825-222834.jpg`, 10604×8528) that matches the manuscript's
Methods description of a 5-agent architecture (Orchestrator, Planner,
Executor, Reflector, Report Agent) run through 4 stages (Planning → Module
Execution & Reflection → Workflow Reflection & Revision → Reporting).

The user wants the `skills/` directory removed from the repo **and
unrecoverable from git history**, requiring a full history rewrite and
force-push, not just a new commit.

## Goals

1. Rewrite `README.md` in two parts, sourced only from `初稿投递nature.pdf`:
   - Part 1: paper-style overview (title, framework description, new
     architecture figure, 5-agent workflow, benchmark results, code/data
     availability)
   - Part 2: usage guide (keep the existing 5-step Docker quickstart, with
     the skills mount/verify steps marked optional since `skills/` is no
     longer bundled in this repo)
2. Replace `figure/framework.png` with a resized/converted version of the
   new diagram.
3. Update the local git remote from `PGI.git` to `VariantAgent.git`.
4. Remove `skills/` from the working tree and purge it from **all** git
   history via `git-filter-repo`, then force-push the rewritten history.
5. Restore the 10 currently-deleted-but-uncommitted `benchmarks/*.csv`
   files.
6. Add `初稿投递nature.pdf` to `.gitignore` (it must never be committed).

## Non-goals

- No changes to `docker/`, `LICENSE`, or `.gitignore` rules other than the
  one addition above.
- No changes to benchmark CSV *contents* — only restoring the deletion.
- Not committing the manuscript PDF or the raw pasted screenshot JPEG.

## A. README content plan

All facts/numbers below are drawn directly from `初稿投递nature.pdf`
(pdftotext-extracted, `/tmp/nature_draft.txt`, line references from that
extraction given in parentheses for traceability during writing).

### Part 1 — Paper overview

- **H1 title** — use the manuscript's actual title verbatim:
  `# Scaling genetic discovery through automated post-GWAS interpretation`
  (line 1). Do not use "PGI — Post-GWAS Intelligence" as the title; introduce
  PGI/VariantAgent as names within the body text instead.
- **Framing paragraph** — PGI (Post-GWAS Intelligence) is the framework;
  VariantAgent is its multi-agent execution engine. Paraphrase from the
  Abstract (lines ~22-39): GWAS made association discovery systematic but
  not cumulative; PGI couples context-dependent post-GWAS analysis to a
  common evidence representation; VariantAgent executes workflows and
  records tool-derived results in standardized variant-centred evidence
  units linked to trait-level reports.
- **Architecture figure** — embed the new `figure/framework.png`.
- **"How VariantAgent works"** — replace the old 3-agent bullet list.
  Describe, from Methods (lines 468-520):
  - **Orchestrator** — central controller, maintains global workflow state,
    coordinates agents by task dependency and reflection outcomes.
  - **Planner** — builds the structured execution plan (modules, inputs/
    outputs, dependencies) at workflow start.
  - **Executor** — one instantiated per eligible module; runs the analysis,
    persists artifacts.
  - **Reflector** — module-level: reviews artifacts for completeness,
    execution correctness, result validity; returns PASS / NEED_REVISION /
    SKIP_WITH_REASON (max 3 execution-reflection cycles per module).
    Workflow-level: reviews plan coverage, module dependencies, cross-module
    consistency once all modules reach terminal state.
  - **Report Agent** — launched after workflow-level reflection passes;
    synthesizes validated artifacts + execution record into the traceable
    final report.
  - Note the >40 task-specific skills used as operational specs by
    Executors/Reflectors (line 515) — mention as a concept, without
    referencing this repo's (now-removed) `skills/` directory as the
    canonical source.
- **Benchmarks** — replace the existing backbone-model ablation table
  entirely with the manuscript's reported comparisons:
  - 313 published questions (Fig. 2b, lines 201-208): VariantAgent 270/313
    (86.3%) vs OpenCode 246 (78.6%), Tool Universe 241 (77.0%), Claude Code
    235 (75.1%); other systems 51.4-57.5%. VariantAgent beat the strongest
    competitor by 7.7 points (95% CI 3.8-11.8).
  - 26 GWAS-grounded questions (Fig. 2c, lines 179-185): open-answer
    accuracy VariantAgent 65.4% (17/26) vs Biomni 53.9% (14/26) vs Claude
    Code 46.2% (12/26).
  - Process-validated accuracy (correct answer + valid analytical trace,
    lines 198-206): VariantAgent 61.5% vs Biomni 30.8% vs Claude Code 7.7%.
    Among answers scored correct, 94.0% of VariantAgent's were trace-valid
    vs 57.1% (Biomni) / 16.7% (Claude Code).
  - 34-published-GWAS matched reanalysis (lines 279-282, 331): mean recovery
    82.1% (95% CI 75.3-88.9%) of directly comparable source-study findings.
  - Scale (lines 314-317): applied to 1,041 GWAS → 530,949 variant-centred
    evidence units + trait-level reports, indexed across 370 traits.
  - Keep pointers to the raw question sets already published under
    `benchmarks/` (these CSVs correspond to the 313-question benchmark's
    GenomeArena/Biomni/SDE source sets — confirm filenames still match after
    restoring the deleted CSVs).
- **Code/Data availability** (lines 1646-1649):
  - Code: `https://github.com/InternScience/VariantAgent`
  - Data/portal: `https://pgi.aigenomicsyulab.com/` — explain (from lines
    1642-1644 and 322-333) that this hosts the generated evidence-unit
    catalogue and an evidence-grounded conversational interface for
    querying it; distinguish from the GitHub repo, which hosts the code.

### Part 2 — Usage guide (kept, adapted)

- Keep the existing 5-step flow: build image → start container → configure
  model API (cc-switch) → load skills → run full pipeline.
- Step 2 (mount `-v /path/to/PGI/skills:/root/.claude/skills`) and step 4
  ("verify skills are discoverable"): reword as **optional** — this repo's
  release does not bundle a `skills/` directory; if the user has their own
  skill library, the same mount mechanism applies. Do not imply skills are
  present in this repo.
- "Repository layout" section: remove the `skills/` entry.
- Everything else (Dockerfile build args, cc-switch commands, example
  pipeline prompt) stays as-is — not sourced from the manuscript, still
  accurate to the repo's actual `docker/` contents.
- Status line at the end: replace "Research prototype accompanying the PGI
  manuscript" framing if needed to stay consistent with Part 1, but no
  substantive change needed here.

## B. Figure replacement

- Source: `20260825-222834.jpg` (10604×8528, ~3.6MB)
- Resize to a reasonable display width (~2400px, preserve aspect ratio),
  convert to PNG.
- Overwrite `figure/framework.png` (discard the old 1301×1544 diagram
  content).
- Do not commit the raw original JPEG to the repo.

## C. Repo rename

- `git remote set-url origin https://github.com/InternScience/VariantAgent.git`
- Confirm the user has renamed (or will rename) the GitHub-side repo from
  `PGI` to `VariantAgent`; GitHub's redirect covers the old URL either way.

## D. Remove `skills/`, purge from history, force-push

This is the highest-risk step (irreversible without a backup, rewrites all
commit hashes, requires force-push). Sequence, using an isolated mirror
clone so the working copy's object store is never directly mutated by
filter-repo:

1. In the working repo: apply all Part A/B/C/E content changes, then
   `git rm -r skills/`, commit as a normal commit on `main`.
2. Install `git-filter-repo` (`brew install git-filter-repo` — confirmed not
   currently installed).
3. `git clone --mirror <path-to-working-repo> /tmp/variantagent-filter.git`
   — isolated copy, safe to mutate destructively.
4. Inside the mirror clone: `git filter-repo --path skills --invert-paths`
   — strips `skills/` from every commit across all branches/tags.
5. In the mirror clone: add/confirm `origin` remote points to
   `https://github.com/InternScience/VariantAgent.git`, then
   `git push --force --mirror origin`.
6. Back in the working copy: `git fetch origin`, then hard-reset local
   `main` to `origin/main` so local history matches the rewritten remote.
7. **Explicit confirmation before step 5**: force-pushing rewrites every
   commit hash on the remote. Anyone who has already cloned/forked this
   repo will hit a non-fast-forward divergence and need to re-clone; any
   open PRs against old commits will no longer apply cleanly. Proceed only
   with the user's final go-ahead immediately before this push.

## E. Benchmarks & ignore rules

- Restore the 10 deleted-but-uncommitted files under `benchmarks/` via
  `git checkout -- benchmarks/`.
- Add `初稿投递nature.pdf` as a new line in `.gitignore`, alongside the
  existing `pgi ms - Google 文档.pdf` entry, so it can never be
  accidentally staged/committed.

## Verification

- `git log --stat` on the final local `main` after the filter-repo rewrite
  should show zero occurrences of any `skills/` path across all commits
  (`git log --all --full-history -- skills` returns nothing).
- `git show HEAD:README.md` renders correctly with the new figure path and
  no dangling references to the removed `skills/` directory as a bundled
  asset.
- `ls benchmarks/*.csv` shows all 10 files restored.
- `git status` is clean except for the intentionally-untracked local-only
  files (PDF, raw screenshot), which `git status` should now show as
  ignored, not just untracked.
