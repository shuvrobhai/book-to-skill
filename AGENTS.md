# AGENTS.md — Personal Preferences

This is a **personal fork** of `virgiliojr94/book-to-skill`, maintained by **shuvrobhai**
for converting books and documents into agent skills. Read this before running the
converter so generated skills match these preferences without re-asking.

## Who I am

- GitHub: **shuvrobhai**
- Primary skill root: **`~/.agents/skills/`** (cross-agent — discoverable by GitHub
  Copilot CLI and Amp)
- I work with PDFs, EPUBs, and Markdown documents; my current books live in the repo
  folder alongside this file.

## Default preferences (don't re-ask unless I say otherwise)

| Setting | Default |
|---|---|
| Skill destination | `~/.agents/skills/<slug>/` |
| Chapter depth | `reference` (lean, fast-lookup chapters, no worked examples) |
| Slug style | Title-derived: lowercase, hyphenated (e.g. `book-of-creating-skills`) |
| Book type | `text` (prose) unless the book has code/tables → then `technical` |
| Extractor | pdftotext for text; docling (`--mode technical`) for tables/code/formulas |
| Install mode | `ask` — offer to install missing extractors, never auto-install |

## Workflow to follow

1. Run extraction: `python3 scripts/extract.py <path> --mode <text|technical> --install-missing ask`
2. Present the Step 2.5 cost estimate and get confirmation.
3. Generate the skill per `SKILL.md` Steps 3–9 using the defaults above.
4. Record every generated skill in **`MY-SKILLS.md`** (append a row).
5. Run `tools/scan_generated_skill.py` and `tools/validate_skill.py` on the result
   before reporting success.

## Maintenance notes

- This repo is **slimmed for skill use** — docs/, tests/, and CI were removed on
  purpose. Recovering them is possible via git history (`git log --diff-filter=D`).
- Remotes: `origin` = upstream `virgiliojr94/book-to-skill` · `fork` = my fork.
  Push changes to `fork` (`git push fork master`); sync upstream via
  `git fetch origin && git merge origin/master`.
- Never commit `.venv/`, book PDFs, or other personal documents — they're
  gitignored.
