---
name: project-resource
description: File a reading resource (URL, local file, or pasted text) under an open ideas.md project idea — pick category, pick project, save it with a summary into that project's references/.
disable-model-invocation: true
argument-hint: "<URL, file path, or pasted text>"
---

# Project resource — reading material into an open idea's references/

Attaches the resource in `$ARGUMENTS` to one **open idea**: an unticked `- [ ]` line in `ideas.md` whose parenthesised path names its folder, e.g. `- [ ] SkinMatch (projects/app-projects/skinmatch/)`. Folders are scaffolded by `/project-idea`; this skill writes only into `references/` and `ideas.md`.

## Steps

### 1. Read the resource

- **URL**: fetch it with WebFetch. If the fetch fails, carry on from the URL alone and say so in step 5.
- **Local file**: read it (PDFs by page range).
- **Pasted text**: use it as given.

Done when you can state in two sentences what the resource argues and what concrete material it offers a builder (competitors, market data, pricing, user pain, APIs, technical approaches).

### 2. Ask the category

One `AskUserQuestion` call, options exactly `app-projects`, `saas-projects`, `side-projects`. Put the category the resource fits best first, marked `(Recommended)`; each description is one line on why the resource does or does not fit that category.

Done when you hold one category.

### 3. Ask the project

Map the category to its `ideas.md` section (`app-projects` → `## App Projects`, `saas-projects` → `## SaaS Projects`, `side-projects` → `## Side Projects`) and collect its open ideas.

- **No open ideas**: tell the user the section is empty, suggest `/project-idea` to create one, and stop.
- **Otherwise**: rank the open ideas by how directly the resource feeds that project, and offer at most five in one `AskUserQuestion` call. The tool shows four options, so put the top four there and, when a fifth exists, name it in the question text so the user can type it via "Other". Label = the idea's name (shortened to fit), description = the decision or assumption of that project the resource would inform. Best fit first, marked `(Recommended)`. With a single open idea, offer it plus `Cancel`.

Done when you hold one idea and its folder path.

### 4. Save it into references/

In `<folder>/references/` (create it if missing; delete a lone `.gitkeep` once a real file lands), write `<source-slug>.md`, kebab-case from the source's title or author (`yc-how-to-find-startup-ideas`). If the slug is taken and the file is this same source, update it in place; otherwise choose a more specific slug.

```markdown
<!-- Source: <url or original path> — fetched <YYYY-MM-DD> for reference only; not written by me -->
# <Resource title>

## Summary

<3–6 sentences: what it is, who wrote it, its core claim, and the evidence behind it.>

## Why it matters for this project

- <bullet per concrete use: the assumption it tests, the competitor or number it supplies, the approach it offers — name the part of the project where it lands (landscape, lean canvas, PRD, build)>

## Content

<the fetched page or pasted text as markdown>
```

A **local binary** (PDF, image) is copied into `references/` as-is, and the `.md` above sits beside it with `## Content` replaced by a link to the copied file. A failed fetch leaves `## Content` holding the URL and a line saying the content still needs capturing.

Done when the file exists and its summary is written from what you read in step 1.

### 5. Link it from ideas.md

Beneath the chosen idea's line, add `  - Reference: <url or references/ file name>`, after any existing `Reference:` lines.

### 6. Report

Show the chosen idea, the file(s) written, and the summary. Done when every file named above exists on disk.
