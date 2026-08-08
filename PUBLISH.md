# Publishing INTL-I 522 to GitHub Pages (slug: `intl522`)

Same process as the 503 site (`503 - IPE/PUBLISH-GITHUB.md`), adapted for this course. Because your personal site lives at `USERNAME.github.io` with a custom domain, any public project repo is automatically served at `YOURDOMAIN.com/<repo-name>/` — repo `intl522` → **`https://YOURDOMAIN.com/intl522/`** with no DNS work.

---

## Step 1 — Pre-flight render check (before any git)

From the project folder in RStudio's terminal (or the Build pane):

```bash
quarto render
```

Then open `_site/index.html` in a browser and click through every page. What to verify on each:

- [ ] **index** — hero banner styled (crimson gradient); instructor/course-details grid side-by-side on desktop; icons render (envelope, clock, calendar); all five Getting Started links work
- [ ] **syllabus** — "Course at a glance" box shows five stacked lines (not one run-on paragraph); grading tables render; all seven article citations present; AI policy section reads correctly
- [ ] **schedule** — all four part tables render; Sep 2 row shows the Sep 4 due date; no stray "room TBD" anywhere (`grep -ri "TBD" *.qmd` should return nothing)
- [ ] **assignments** — six assignment cards with hover borders; every "Full instructions" link resolves
- [ ] **session-notes-roles / final-project / course-precis / data-projects** — info-boxes styled, tables render, internal links back to syllabus/assignments/resources work
- [ ] **resources** — external links spot-check (WDI, DHS, Findex at minimum, since students will follow them)
- [ ] **navbar** — all five items work from every page; footer shows on each page

Fix anything broken before proceeding (or bring it back to Claude).

## Step 2 — One-time git + GitHub setup

1. On github.com: **New repository** → name `intl522` → **Public** → do NOT add a README/.gitignore/license → Create.
2. In the terminal, from this folder:

```bash
cd "/Users/sarahbauerledanzman/Library/CloudStorage/OneDrive-IndianaUniversity/Teaching/IU Courses/522 - Global Development/Fall 2026 Course Site"
git init
git add .
git status        # eyeball the file list BEFORE committing — see step 3
```

3. **Verify the .gitignore is actually working** before the first commit (this is the step that failed silently on 503 and leaked 283 files):

```bash
git check-ignore -v teaching-notes/ _archive/ _site/ .Rproj.user/
```

Each path should print the rule that caught it. **No output for a path = NOT excluded = stop and fix.** Also confirm `git status` does not list anything from `_site/`, `_freeze/`, or `teaching-notes/`. (There is no `readings/` or `exams/` folder here yet — if you add one later, add it to `.gitignore` first, on its own line, with no trailing comment.)

4. Commit and push:

```bash
git commit -m "Initial commit: INTL-I 522 course site, Fall 2026"
git branch -M main
git remote add origin https://github.com/USERNAME/intl522.git
git push -u origin main
```

## Step 3 — Publish the rendered site

```bash
quarto publish gh-pages
```

Say yes when it asks. This renders, creates the `gh-pages` branch, pushes the HTML, adds `.nojekyll`, and enables Pages.

## Step 4 — Check Pages settings

Repo **Settings → Pages**: Source = **Deploy from a branch → `gh-pages` / (root)**. Leave the **custom domain field blank** — blank is what makes it inherit `YOURDOMAIN.com/intl522/`.

## Step 5 — Visit and link

After a minute or two: `https://YOURDOMAIN.com/intl522/`. Then add a nav/menu link on your personal site pointing to `/intl522/`.

---

## Updating during the semester

Content change → re-run:

```bash
quarto publish gh-pages
```

That one command re-renders and re-publishes. To also save source history: `git add . && git commit -m "..." && git push`.

## Notes

- Quarto uses relative links, so nothing in `_quarto.yml` needs to change to live under `/intl522/`. If an asset ever 404s, the fix is adding `site-url: https://YOURDOMAIN.com/intl522/` to `_quarto.yml`.
- No password protection on GitHub Pages. Nothing on this site needs it — readings are on Canvas, not here. Keep it that way.
- Grades, rosters, student work: Canvas only, never this folder.
