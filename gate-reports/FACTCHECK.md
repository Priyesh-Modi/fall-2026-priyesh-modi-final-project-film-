# Fact check

Status: checked 2026-10-24 by Claude (agent); reviewed and signed off by Priyesh Modi, 2026-10-24.

Every claim about the project's future is labelled 'will' in the narration and 'plan · not built' on screen; those rows are plans, not results.

| # | Beat | Claim | Verdict | Source | Fix |
|---|---|---|---|---|---|
| 1 | BIDEA | The voice is synthetic, reading the author's script. | PASS | Kokoro am_onyx, local; make_sheet.py | None |
| 2 | B00 B01 B04–B12 B15 | Agent, repo, checks, comparison, eval: all future tense. | EXEMPT | PROJECT-BRIEF.md 'Will exist' | 'will' throughout; on-screen plan tags |
| 3 | B02 | The v2 migration guide maps dict() to model_dump(); the card shows five real rows of that table (lines 140, 141, 142, 144, 145; line 143 left out because it overflows the card). | PASS | evidence/snapshot-and-migration.txt (captured 2026-10-24); docs/migration.md:140-145 | Kokoro voices 'dict' badly; spoken as 'the method that turns a model into a dictionary' |
| 4 | B03 | The author compared GitHub Copilot and Cursor; neither said which version an answer was for, or quoted the official docs. | PASS | The author's own comparison (stated by Priyesh Modi, 2026-10-24) | Stated as personal experience, not a product claim |
| 5 | B07 | Old v1 method names emit DeprecationWarning, so running code can catch them. | PASS | evidence/snapshot-and-migration.txt (captured 2026-10-24); docs/migration.md:133 | None |
| 6 | B13 | Cloned 2026-10-24 at release 2.14.1, commit b2212c78, 91 docs pages; the card's rows are real. | PASS | evidence/snapshot-and-migration.txt (captured 2026-10-24); SNAPSHOT.md | None |
| 7 | B16 | CI on the author's webapp runs tests on pull requests. | PASS | github.com/Priyesh-Modi/webapp .github/workflows/ci.yml (on: pull_request) | Corrected from 'every push' |
| 8 | B16 | The author already has Python, FastAPI, Streamlit, Supabase and CI/CD. | EXEMPT | Author's statement. CI/CD: Priyesh-Modi/webapp. Supabase: Nuxt + Supabase projects (on the author's machine, not yet public). Python/FastAPI/Streamlit: co-op work, proprietary, not linkable | Stated as such in PROJECT-BRIEF.md section 7 |
| 9 | B14 B15 | Eval-question risk; start at 30; 'I don't know yet' how many are enough. | EXEMPT | PROJECT-BRIEF.md section 6 | A plan, stated as one |
| 10 | BDEFS BOUT | Definitions, title and name. | EXEMPT | make_sheet.py | None |
