---
name: project-idea
description: Capture a raw project idea or URL — sharpen it into four name+pitch angles, pick a category, scaffold projects/<category>/<slug>/ with references/ and TODO.md, and add it to ideas.md.
disable-model-invocation: true
argument-hint: "<raw idea, a URL, or both>"
---

# Project idea — raw thought to a scaffolded project folder

Turns whatever the user dropped (`$ARGUMENTS`: a half-sentence, a URL, or both) into a named project folder, `projects/<category>/<slug>/`, holding `references/` (source material) and `TODO.md` (the discovery-to-launch checklist). Later work lands in the same folder: discovery and product docs in `docs/`, code alongside.

## Steps

### 1. Understand the idea

If the input holds a URL, fetch it with WebFetch and read enough to know what the product does, who it serves, and how it makes money. Keep the fetched text; step 4 saves it. If the fetch fails, carry on from the URL and the user's words, and say so in step 2.

Done when you can state in one sentence what the project solves and for whom.

### 2. Pitch four angles and a category

Draft four distinct **angles** on the idea: each a different user, problem, wedge, or business model, not four rewordings of one. Each angle is a working name plus a 2–3 sentence pitch saying who the user is, the pain it removes, and what the first version does. Put your preferred angle first.

Ask both questions in one `AskUserQuestion` call:

- **Angle**: the four angles as options; label = working name (shorten to fit if needed), description = the pitch. Mark your preferred one `(Recommended)`.
- **Category**: exactly `app-projects` (consumer mobile/web app), `saas-projects` (subscription product for businesses or teams), `side-projects` (small build, tool, or experiment). Put the best fit first, marked `(Recommended)`.

If the user answers "Other" with their own name or tweak, use it as written. Done when you hold one final name, its pitch, and one category.

### 3. Pick the slug

Kebab-case, 2–5 words, taken from the final name (`skinmatch`, `invoice-chaser`). List `projects/<category>/`; if the slug is taken, choose a more specific one. The folder is `projects/<category>/<slug>/`.

### 4. Scaffold the folder

Create `projects/<category>/<slug>/references/`.

- **URL given**: save the fetched content as `references/<source-slug>.md`, first line the provenance comment:
  `<!-- Source: <url> — fetched <YYYY-MM-DD> for reference only; not written by me -->`
  followed by the page title and its content as markdown. If the fetch failed, the file holds the provenance comment and the URL, with a line noting the content still needs capturing.
- **No URL**: add an empty `references/.gitkeep` so git keeps the folder.

Write `TODO.md`:

```markdown
# TODO — <Name>

<the chosen pitch>

- [ ] Gather sources into `references/` <name the gaps the idea obviously needs: competitors, market data, APIs, datasets>
- [ ] Grill the idea: target user, the painful problem, why now, why me (`grilling`)
- [ ] Competitive landscape → `docs/`
- [ ] Lean canvas + riskiest assumptions → `docs/`
- [ ] Experiments to test the riskiest assumptions
- [ ] PRD for the MVP → `docs/`
- [ ] Build the MVP
- [ ] Launch + LinkedIn post
- [ ] Tick this idea in `ideas.md`
```

Make the first item specific to this idea; the rest stay as the release checklist.

### 5. Add it to ideas.md

Under the `ideas.md` section matching the category (`app-projects` → `## App Projects`, `saas-projects` → `## SaaS Projects`, `side-projects` → `## Side Projects`), append:

```markdown
- [ ] <Name> (projects/<category>/<slug>/)
```

Indent a `  - Reference: <url>` line beneath it when a URL was given. If the section is missing, add its heading in the order above; if it holds only the `_(nothing yet)_` placeholder, replace the placeholder.

### 6. Report

Show the name, the folder path, the files created, and the `ideas.md` line. Done when every file named above exists on disk.
