# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

Harness is a **Claude Code plugin** distributed as a meta-skill — a "team-architecture
factory." Its single product is a skill that, given a one-sentence domain description,
generates an agent team (`.claude/agents/`) and the skills those agents use
(`.claude/skills/`) in a *target* project, choosing from six team-architecture patterns
(Pipeline, Fan-out/Fan-in, Expert Pool, Producer-Reviewer, Supervisor, Hierarchical
Delegation).

There is **no application code, build step, or test runner** here. The repository is
content: Markdown (skill definitions, references, docs, READMEs), JSON manifests, and
images. The deliverable is the prose in `skills/harness/`.

Critical distinction: this repo *is* the factory. The `.claude/agents/` and
`.claude/skills/` directories described throughout the skill are what the harness
**produces in other projects** — they are not part of this repo (and `.claude/` is
gitignored).

## Layout that matters

- `skills/harness/SKILL.md` — the heart of the project. The full 7-phase workflow
  (Phase 0 audit → 1 domain analysis → 2 team architecture → 3 agent definitions →
  4 skill generation → 5 orchestration → 6 validation → 7 evolution). Written in
  **Korean**. Keep its body under ~500 lines; push detail into `references/`.
- `skills/harness/references/*.md` — conditionally-loaded deep docs (agent patterns,
  orchestrator template, team examples, skill-writing/testing guides, QA agent guide).
  These are loaded on demand, so they can be longer; files past ~300 lines should carry
  a table of contents.
- `.claude-plugin/plugin.json` — plugin manifest. **The canonical version source.**
- `.claude-plugin/marketplace.json` — marketplace entry (`harness-marketplace`).
- `docs/` — long-form docs (`quickstart.md`, `experimental-dependency.md`) kept out of
  the README to prevent README bloat.
- `_workspace/` — internal release/audit working files. This is the same file-passing
  convention the skill teaches (`_workspace/{phase}_{agent}_{artifact}.md`); it is
  committed here as the project's own audit trail, not generated output.
- `README.md` + `README_KO.md` + `README_JA.md` — trilingual; all three carry a version
  badge that must stay in sync (see below).

## Conventions specific to this repo

### Version synchronization (high-frequency bug source)
The version appears in **five** places that drift apart: `plugin.json`,
`marketplace.json`, and the badge in each of the three READMEs. `plugin.json` is the
source of truth. Any version bump must update all five together — a past release shipped
with a three-way mismatch (see `CHANGELOG.md` [1.2.1]). Tags follow `vMAJOR.MINOR.PATCH`,
cut from `main`.

### Commits → SemVer (Conventional Commits, light variant)
`<type>(<scope>)!: <summary>`. The mapping is enforced for releases:
- `feat!:` / `BREAKING CHANGE:` footer → **major**
- `feat:` → **minor**
- `fix:` → **patch**
- `docs:` / `chore:` / `refactor:` / `test:` → no release bump

The `!` suffix is the *only* canonical major trigger — don't set it lightly. **Korean or
English commit summaries are both accepted.** Update `CHANGELOG.md` (Korean,
Keep-a-Changelog style, `[Unreleased]` section at top) in the same change.

### Branch naming
`type/short-description` with prefixes `feat/ fix/ docs/ refactor/ chore/ test/`
(e.g. `docs/quickstart-section`).

### Writing skills (the product's own house style — follow it when editing SKILL.md or references)
- **Explain *why*, not just "ALWAYS/NEVER".** The LLM generalizes correctly from reasons.
- Write imperatively; keep `SKILL.md` lean and move detail to `references/`.
- **Descriptions are the only trigger mechanism** — write them "pushy": list what the
  skill does *and* concrete trigger phrasings, including follow-up keywords
  ("다시 실행", "재실행", "업데이트", "수정").
- The harness never generates `.claude/commands/` — only agents and skills.
- Generated agents are pinned to `model: "opus"`; Agent calls pass `model: "opus"`.

## Commands

No build. Lint/validation (run from repo root; Node ≥ 18 for tooling):

```bash
npx markdownlint '**/*.md'      # Markdown lint
npx yaml-lint .github/          # YAML lint for issue templates & workflows
```

`scripts/validate_skills.py` is referenced in CONTRIBUTING.md as "if present" — it does
not currently exist in the tree.

### Testing the plugin locally
```bash
claude plugin link ./harness        # link this checkout into a session
claude plugin list | grep harness   # verify
claude "build a harness for a fintech risk-assessment team"   # exercise the meta-skill
claude plugin unlink harness        # cleanup
```

## Runtime dependency

The harness requires Claude Code's experimental Agent Teams feature:

```bash
export CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1
```

Requires Claude Code v2.x. The status of this flag is tracked in
`docs/experimental-dependency.md`; if Anthropic promotes it to stable, update the README.

## Claims discipline

The "+60%" effectiveness number is an author-measured A/B (n=15). Repo policy: never cite
it without the disclosure "n=15, author-measured, third-party replications pending" in the
same sentence. Preserve that pairing if you touch any file that mentions it.
