# Lesson Plan Workflow — Internal Notes (not for students)

This file documents the repeatable process for turning a jCoders curriculum slide
deck into a student-facing "Udhezues" lesson plan for this group's repo. It's a
personal reference for Rreze / Claude, not course content — see the `.gitignore`
entry that keeps it out of git.

## Context

- Group repo: `rreze-ejupi-webfundamentals-280`, one folder per lesson (`Ora-N-Topic`),
  each containing `Ora-N-Topic-Udhezues.md`.
- Source material lives in Google Drive under:
  `2. Trainer Experience jCoders → 1. Planprogramet Current → Viti I Web
  Fundamentals → Aktivitetet → 1. HTML Fundamentals` — this folder holds the
  `.pptx` decks per activity (e.g. `A6 - Njoftimi me Web-in.pptx`).
- This group has **no GitHub-setup lesson**, so there's no fixed offset like the
  JS repo — `Ora-N` numbering starts sequential from `Ora-1 = Aktiviteti 1`.
  However it can still drift from the Drive's `Aktiviteti` numbering for two
  reasons, so always sanity-check against the actual slide title before
  finalizing a folder's number/topic name:
  - **Skipped "Ora Sfiduese" hours.** These are practice/challenge-only sessions
    with no new teaching content — they get no folder at all (no placeholder),
    so the next real lesson just takes the next `Ora-N` in sequence even though
    it skips an `Aktiviteti` number in Drive.
  - **Merged multi-hour topics.** When two (or more) consecutive `Aktivitete`
    are really one continuous topic taught across multiple class hours (e.g. a
    Figma project started in one hour and finished in the next, or a "vazhdim"
    continuation activity), they get combined into a **single** `Ora-N` folder
    and a single Udhezues file rather than one folder each. Fold the content
    together into one continuous narrative (don't just concatenate two
    documents) and keep only one `# Aktiviteti <n>` header for the pair.
- Some lessons cover **Figma / design tool** work rather than code — for those,
  in-class exercises describe UI steps (menus, panels, values to set) instead of
  code blocks, but every other structural rule below still applies.

## Steps for every new lesson

1. **Find the slides.** Search Drive for the activity's `.pptx` under the HTML
   Fundamentals path above and read its content (concepts, code/design examples,
   in-class exercises). If a deck is unreadable (very large, mostly images) or
   no longer exists in Drive, reconstruct the lesson from the activity's known
   scope/title plus standard curriculum knowledge, and add an explicit
   `> ⚠️ **Shënim:**` warning at the very top of the file flagging this so it
   gets reviewed.
2. **Check the repo.** List the repo root, find the highest existing `Ora-N`
   folder, and use `N+1` with a short Title-Case topic name for the new folder:
   `Ora-<N>-<Topic>`. Decide whether this activity should merge into the
   previous `Ora-N` folder (continuation of the same multi-hour topic) or start
   a new one, per the merging rule above.
3. **Read an existing Udhezues as the template.** Open at least one recent
   `Ora-N-Topic-Udhezues.md` in full and match its exact format:
   - Header is exactly two lines, nothing else before the first `---`:
     ```
     # Aktiviteti <n> — <Topic Title>
     ## Udhëzues
     ```
     No subtitle, no objective/materials list, no minute-by-minute timing table —
     this file goes straight from the heading + `---` into the narrative intro.
     **It is a student-facing document.** Any planning scaffolding (objective,
     materials, agenda/timing) stays out of it entirely.
   - Albanian, informal-but-precise teaching voice, narrative tense ("mësuam...",
     "pamë...", "ushtrimi që bëmë...").
   - Numbered `##` sections building concept by concept — code lessons use a
     fenced ` ```html ` (or relevant language) example per concept; design
     lessons use short numbered steps or a description of what to click/set.
   - Callout blockquotes: `> 💡` for tips/notes, `> ⚠️` for gotchas/warnings.
   - Closing sections, in order: `## Përmbledhje e shpejtë` (plain fenced summary
     block), `## Fjalë të shkurtra` (glossary, bullet list of **term** —
     definition), `## 🎯 Sfida jote (pikë ekstra)` (bonus challenge, usually taken
     straight from the deck's own extension/challenge slide).
4. **Write the lesson content.** Adapt (don't just paste) the slide's bullet
   points into the narrative style above. Slide in-class exercises become
   "Ushtrimi/Ushtrimet që bëmë në klasë"; the slide's challenge/extension
   exercise becomes "Sfida jote". Scope the material to the actual teaching
   time by how much content is included — never by adding an explicit timing
   table to the document.
5. **Deliver.**
   - Write the `.md` file, send it to Rreze, then commit it onto the local
     machine at `<repo>/Ora-<N>-<Topic>/Ora-<N>-<Topic>-Udhezues.md` (this
     creates the new lesson folder).
   - Confirm the folder was created and its name matches the `Ora-N-Topic`
     convention exactly.
   - Flag anything that looks off — e.g. the Drive slide numbering and the
     repo's `Ora-N` numbering have diverged, a lesson seems to have been
     skipped, or content had to be reconstructed without the original deck.
