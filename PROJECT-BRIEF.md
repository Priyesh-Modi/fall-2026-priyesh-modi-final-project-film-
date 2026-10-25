# Project brief — Pinned Docs, Cited Answers

**Priyesh Modi** · INFO 7375 · Fall 2026 · written 2026-10-24
**Target role:** AI engineer / applied LLM engineer
**Stack (planned):** Python, Claude API, BM25 retrieval, `venv` + `pip`, pytest, GitHub Actions

**1. What is it?**
- An agent that answers coding questions from a library's official docs, pinned to the version you're using, and checks its own answers. It quotes the section it used, runs any code against that version, and refuses when the docs don't cover the question.
- When it's done, it will be a public GitHub repository with a command-line agent, a snapshot loader that works on any docs repo at a version tag, a citation checker, and an eval set and log. Pydantic is the first library it will be tested on.

**2. Why would anyone care?**
- Coding assistants answer from training data that can be a version behind. Pydantic's v2 migration guide renames `dict()` to `model_dump()` (`docs/migration.md:142`), and an assistant that learned v1 can hand you the old name.
- I compared GitHub Copilot and Cursor. Both answer fast in the editor, but neither told me which version an answer was for, or quoted the official docs.
- Mine quotes the docs word for word, runs the code against the pinned version, and publishes a scored comparison. **It saves a coder the step of checking whether an AI's answer matches their installed version.**
- Context7 is on my list to evaluate next.

**3. Who opens it, and what do they do?**
The reader is a coder working against a specific library version. In the first sixty seconds they:
1. read the dated results table at the top of the README,
2. run one command ("what replaced `dict()` in v2?") and get a quoted, checked answer,
3. open the eval log, including what it got wrong.

**4. What does it prove about me?**
- **Source grounding:** every claim quotes a named version's docs.
- **Prompt contracts:** each answer has one quote per claim and at most one runnable snippet, or is a refusal.
- **Verification:**
  - a quote checker that doesn't trust the model,
  - code run in a fresh environment, where an error or `DeprecationWarning` fails the answer,
  - a blind hand-check of 20 answers to test the checks themselves.
- **Evaluation:** a dated comparison against a plain model.

The evidence will be the eval log and the results table. It won't prove the tool works on docs formats I haven't tested.

**5. In, out, first**
- **In:** versioned snapshots, version detection from `requirements.txt` / `pyproject.toml`, quoted answers, the quote and code checks, refusals, the eval set, the baseline table.
- **Out:** it won't write or fix your project or read live web pages; no private docs; a second library only if time allows.
- **First:** the quote checker, run on hand-written answers with deliberately broken quotes. You'll know it ran from a dated log row showing whether it caught every broken one.

**6. What could sink it?**
- **The risk:** easy self-written questions would make the table meaningless.
- **What I'll do:**
  - take questions from Pydantic's `HISTORY.md` and migration guide, where the answers are written down,
  - add trap questions (a function that doesn't exist; a v2-only feature asked about v1),
  - add real GitHub issues.
- I don't know yet how many questions are enough. I'll start with 30 and check whether the scores hold. Every run records the model ID, snapshot hash and date.

**7. Why this project?**
- A mix, mostly learning, on a problem I've hit myself.
- **New:** evaluation sets, agent loops, prompt contracts.
- **Already have:**
  - CI/CD: `github.com/Priyesh-Modi/webapp`, with GitHub Actions running tests on pull requests and a Packer AMI build.
  - Supabase: `nuxt-database-demo` and `nuxt-photo-storage` (Nuxt 3 + Supabase; on my machine, not yet public).
  - Python, FastAPI, Streamlit: used during my co-op. The code belongs to the employer, so it isn't linked here.
- In this course's job-triage recipe (2026-10-11) I caught a scorer marking all 55 postings "Apply". That's a habit of verification, not proof that I can build an eval harness.

**Exists today (2026-10-24)**
- Pydantic v2.14.1 docs snapshot (commit `b2212c787fb5`, 91 Markdown pages), cloned 2026-10-24; see `SNAPSHOT.md`.
- This brief, the beat sheet and the film.

**Will exist**
1. Quote checker and tests (first)
2. Snapshot loader and manifest
3. Prompt contract
4. Retrieval, agent CLI and version detection
5. Run-the-code check
6. Eval set (about 30 questions plus traps)
7. Baseline comparison, eval log and README table
8. `FAILURES.md`
9. Stretch: a second library and a Context7 row
