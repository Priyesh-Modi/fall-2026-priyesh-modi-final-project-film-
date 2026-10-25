# FRICTIONAL: honest log

All entries are from 2026-10-24. Times are approximate, local (EDT).

## Afternoon: choosing the project
- I picked a version-aware docs Q&A agent over extending my Reallocation Engine sponsor-triage recipe. I want to learn evaluation and agent loops on something a stranger can check.
- I'd already cloned Pydantic v2.14.1 into `~/INFO7375/snap/` (18:48). Its v1→v2 migration guide gives a concrete, checkable reason the version matters.

## Building the first cut with Brutalist (show-tell)
- **Kokoro wasn't found at first.** The toolkit's dependencies are in `~/INFO7375/.venv`, not the system `python3`. Fix: activate that venv.
- **The skill defaults to the instructor's persona:** "Liam, in for Bear", an `@NikBearBrown` handle and outro, and a Bear-Brown logo bug. The assignment says to narrate as myself. I rewrote the greeting in the first person, used my own name everywhere, dropped the logo bug, and dropped the "Your Turn" exercise, because this is a pitch, not a lesson.
- **The outro card ignored my handle.** The first review render still showed `@NikBearBrown`: `ClaudeTitleOutro.tsx` hardcodes it (`OUTRO-LOCK.md`). The toolkit's `bookend_check.py` checks props, not pixels, so it would have passed. I only caught it by looking at the frame. I replaced it with my own drawn outro card. As a result, `bookend_check.py` now reports the outro as non-standard, and I kept that report.
- **Kokoro mispronunciations, caught with a faster-whisper transcript:**
  - "dict" was voiced as an obscenity. Reworded to "the method that turns a model into a dictionary".
  - "AI engineer" came out as "our engineer", "eye" and "iEngineering" in different takes. Reworded to "roles building with language models".
  - "misses included" came out as "Mrs. Included". Reworded.
- **GATE T blocked the first master.** The definitions card had a 40 px text run against a 41 px floor. Four fixes, in order:
  1. Capitalising the terms didn't help.
  2. Removing the name label didn't help.
  3. Measuring the midpoint frame myself showed the gate splits words at glyph gaps (so "rawn" in "drawn"). Rewording didn't help either.
  4. The component has no size prop, and I didn't want to edit the shared toolkit. Its `dark` polarity passed, at exactly the floor.
- **Honesty tags:** every drawn beat has a corner tag ("plan · not built", "real · …", "my comparison" or "about me"), because the drawings are metaphors and nothing is built yet.

## Evening: the scope changed three times
1. **Pydantic only → any technical docs.** My first brief described "one library, one version". That isn't what I mean: the tool is for coders reading any library's docs to see what changed between versions, because assistants like Copilot can hallucinate or refer to older versions. Pydantic is just the first test case. I rewrote the brief and the beats.
2. **Is it strong enough?** I asked Claude for an honest assessment. Its view: "docs Q&A with citations" is a crowded space (it named Context7, Cursor's `@Docs` and hosted docs chatbots), and a generic RAG demo won't stand out. I looked at alternative projects (a CI-failure explainer, a Terraform plan reviewer, questions over Boston open data, a city-council tracker) and decided to keep mine and make it stronger.
3. **Simple but strong.** I chose four additions that are small to build:
   - a word-for-word quote check,
   - running any code answer against the pinned version (Pydantic's own guide, line 133, says old names emit `DeprecationWarning`),
   - eval questions taken from the changelog and migration guide, plus trap questions,
   - a comparison against a plain model as the headline result.

   I dropped the separate version-comparison mode and moved the second library to "if time allows". Estimated build: 6–8 working days.

## Decisions on the content
- **Alternatives:** I compared GitHub Copilot and Cursor myself. The docs-search comparison I had in an earlier draft is gone, because I hadn't actually used it as an alternative. Context7 is listed as "to evaluate next", not as compared.
- **Reader:** the coder only. I removed "and, for my portfolio, a hiring manager" from the film. The target role is stated in B10 instead ("for roles building with language models").
- **Skills:**
  - New: eval sets, agent loops, prompt contracts.
  - Existing: Python, FastAPI, Streamlit, Supabase, CI/CD.
  - Evidence: `github.com/Priyesh-Modi/webapp`, whose CI runs tests on pull requests. The film first said "every push", but I checked `ci.yml` (`on: pull_request`) and corrected it. Supabase is backed by my Nuxt + Supabase projects, which are on my machine but not yet public.
  - Python, FastAPI and Streamlit were used during my co-op; that code is the employer's, so it isn't linked (see the open items).
- **Rubric check:** comparing against the rubric showed "shown, not asserted" was weak, because every picture was a metaphor. B02 and B13 now show **real data**: the actual `docs/migration.md` table rows (lines 140–145) and my snapshot's real record (tag, commit `b2212c78`, 91 pages). Both were captured at 21:28 into `pinned-docs-pitch/evidence/snapshot-and-migration.txt`.
  - In the first card test, one row (`model_json_schema()`) overflowed the card edge, so I swapped it for another real row.
- **Brief length:** I cut it from about 1,100 to about 750 words. It's still about a page and a half; cutting more would drop real content.

## Late evening: second render
- **GATE T blocked the master on B03** (the branch-junction drawing). At the midpoint frame, two of the prop's flat route plates were detected as two text runs whose boxes overlapped by 18%. No real labels overlapped. Running the gate's own `check_bbox_overlap` on single frames showed the rest pose passes and the moved pose fails. Fix: the packet now moves on "Mine will answer…", after the midpoint, which also fits the narration.
- After that fix, every render gate passed (A, layout, W, V, T, fact check). The bookend check still fails on the outro, by choice. The master is 230.8 s, SHA-256 `72c41aa6eab5e5cbdc58c53a9b4bdad1d4c703b633d6316a2101d8ecde04924c`.

## Open items before I submit
- [x] Python / FastAPI / Streamlit evidence: used during my co-op. The code is the employer's and can't be linked, so the brief says so rather than pointing to nothing. A small public sample repo would make this checkable; optional.
- [x] Watched the whole film with sound (2026-10-24). It looks and sounds right.
- [done] Commit to `fall-2026/priyesh-m/final-project-film/` and paste the link and commit hash into Canvas.
