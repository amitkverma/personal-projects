# Personal Projects

Ideas, discovery work, and builds for my personal projects, one folder per project.

## Layout

```
ideas.md                         # index of every idea, grouped by category
projects/
  app-projects/                  # consumer mobile/web apps
  saas-projects/                 # subscription products for businesses or teams
  side-projects/                 # small builds, tools, experiments
    <slug>/
      TODO.md                    # pitch + discovery-to-launch checklist
      references/                # source material, not written by me
      docs/                      # discovery and product docs (landscape, lean canvas, PRD, ...)
```

Files in `references/` start with a provenance comment:
`<!-- Source: <url> — fetched <YYYY-MM-DD> for reference only; not written by me -->`

## Workflow

1. `/idea <raw idea or URL>`: pitches four angles, picks a category, scaffolds `projects/<category>/<slug>/` with `references/` and `TODO.md`, and adds the idea to `ideas.md`.
2. `/resource <URL, file, or pasted text>`: files reading material under an open idea's `references/` with a summary, and links it from `ideas.md`.
3. Work through the idea's `TODO.md`: grill the idea, write discovery docs into `docs/`, test the riskiest assumptions, write the MVP PRD, build, launch.
4. Tick the idea in `ideas.md` once shipped or dropped.

Skills live in `.claude/skills/`, mirrored in `.agents/skills/`.
