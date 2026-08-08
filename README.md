# INTL-I 522 — Global Development (Fall 2026)

Working directory and Quarto source for **INTL-I 522: Global Development**, Fall 2026, taught by Sarah Bauerle Danzman at Indiana University. Graduate seminar, 4 students, Mon/Wed 12:45–2:00 PM, Cedar Hall C107, Aug 24 – Dec 18, 2026.

Built 2026-08-07 from the 503/103 course-site template (see `COURSE-BUILD-HANDOFF.md` in `503 - IPE/` for the conventions this folder follows). Course design decisions are also mirrored in the Claude project "522 - International Development" (`course-facts.md`, `reading-schedule-fall2026.md`, `assessment-structure-fall2026.md`, `ground-rules-and-conventions.md`).

## What's at the root

| File | Purpose |
|------|---------|
| `_quarto.yml` | Site config — navbar, theme, render list |
| `index.qmd` | Site home page |
| `syllabus.qmd` | Syllabus (rendered to the public site) |
| `schedule.qmd` | Full semester schedule — the authoritative what's-due-when |
| `assignments.qmd` | Assignment descriptions (single page, per the 103 pattern) |
| `session-notes-roles.qmd` | Full instructions for session notes + the four rotating discussion roles (Leader/Skeptic/Connector/Practitioner). Notes turned in on paper (4 printed copies), per Sarah's edit |
| `final-project.qmd` | Full final-project instructions: genre menu, milestones, evaluation |
| `course-precis.qmd` | Full précis instructions: causal-map requirements, build rhythm, evaluation |
| `data-projects.qmd` | Both data-project briefs: tasks, sources, deliverable format, shared rubric |
| `resources.qmd` | Student-facing resources incl. data sources for the two data projects |
| `theme.scss` | IU crimson theme (carried over verbatim from 503/103) |
| `.gitignore` | Excludes build artifacts + instructor-only folders. **No trailing comments on pattern lines** — see the handoff note for why |

## Subfolders

| Folder | Contents |
|--------|----------|
| `content/` | (Phase 2) Per-session landing pages, `dayXX.qmd` |
| `slides/` | (Phase 2) Any decks — e.g., adapted 203 lectures. Create `SLIDE-CONVENTIONS.md` before the first deck |
| `teaching-notes/` | Instructor prep notes — never rendered, never pushed |
| `_archive/` | Superseded drafts and planning logs — never rendered, never pushed |
| `readings/` | (Create when needed) Instructor copies of PDFs — gitignored |

## Building the site

```bash
quarto render
```

Or the Build pane in RStudio. Output lands in `_site/`. Publishing (once a repo exists): `quarto publish gh-pages` — see `PUBLISH-GITHUB.md` in the 503 folder for the one-time setup.

## Status / TODO

- [x] Cedar Hall room number — C107 (added 2026-08-07)
- [x] Office hours — M/W 2–3:30 PM, GISB 1013 + by appointment (added 2026-08-07)
- [x] McVety chapter cite confirmed — ch. 2 of Macekura & Manela, *The Development Century* (2018), pp. 21–39 (added 2026-08-07)
- [x] Week-15 AI readings selected — Jones w34779 + Acemoglu w32487 (Nov 30); Korinek & Stiglitz w28453 + Otis et al. 2025 (Dec 2). Post PDFs to Canvas
- [ ] Data-project briefs: format/length guidance to post on Canvas (site pages point there)
- [ ] Full render check + publish to GitHub Pages as repo `intl522` — **follow `PUBLISH.md`** (pre-flight checklist, gitignore verification, `quarto publish gh-pages`)
- [ ] Role rotation schedule + DP1 region sign-up sheet (need roster; post to Canvas)
- [ ] Phase 2 (deferred deliberately): content pages (`content/dayXX.qmd`), framing decks (from 203 material), `slides/SLIDE-CONVENTIONS.md`

## What never gets pushed

If this folder becomes a public repo: `readings/`, `teaching-notes/`, `_archive/`, and any grades/rosters (those live in Canvas, never here). Verify with `git check-ignore -v <path>` — no output means NOT excluded.
