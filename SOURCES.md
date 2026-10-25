# Sources: what I used, what I made, what Claude contributed

## What I used

| Item | What it is | Licence / terms |
|---|---|---|
| Pydantic repository, tag v2.14.1, commit `b2212c787fb5` | The docs snapshot the project is built on, cloned 2026-10-24. Beat B02 shows five real rows of the `docs/migration.md` table (lines 140–145), and beat B13 shows the snapshot's real record. Both were captured at 21:28 into `pinned-docs-pitch/evidence/snapshot-and-migration.txt`. | MIT (repository `LICENSE`). Five table rows are quoted; the docs are not redistributed. |
| brutalist.art toolkit, commit `a99b5323` (2026-10-23) | `show-tell` skill: `iso_kit.py` projection and palette, the 25 approved original props (`iso_originals_25.py`), the Remotion scenes `BrutalistHesitantWriter`, `ClaudeDefinitions` and `ShowTellCard` (two `focus` cards), and the gates. Its `ClaudeTitleOutro` was not used, because it hardcodes the instructor's handle; the outro is my own drawn card | Course toolkit (github.com/nikbearbrown/brutalist.art). Its README has no licence file; used as the course directs. |
| Kokoro TTS (kokoro-onnx, voice `am_onyx`) | Local synthetic narration of my script. No paid service, no key. | Kokoro-82M model weights, Apache-2.0 |
| EB Garamond, Lato (bundled with the toolkit) | On-screen type | SIL Open Font License (`runtime/fonts/EB_Garamond/OFL.txt`, `runtime/remotion/public/fonts/Lato-OFL.txt`) |
| Manim Community v0.20.1, Remotion, ffmpeg, faster-whisper | Rendering, compositing, and the transcript check of the narration | Open source (MIT / Remotion licence / LGPL / MIT) |
| My earlier course submission, `boston-funded-sponsor-triage` (2026-10-11) | The source for the claim in brief §7 (the scorer marked all 55 postings Apply) | My own work |
| `github.com/Priyesh-Modi/webapp` (CSYE6225, Spring 2025) | Evidence for the CI/CD skill named in B16 (`.github/workflows/ci.yml`, `on: pull_request`) | My own work |

There are no third-party images, music or stock footage. The outro has no jingle.

## What I made

- The project idea (version-aware answers from official docs, for coders whose assistants suggest older APIs), and the answers to the seven questions in `PROJECT-BRIEF.md`.
- The comparison with GitHub Copilot and Cursor, from my own use.
- The decisions on which library to use, which alternatives to compare, which skills are new to me, and the risk.
- The choice to narrate with a synthetic voice and to say so in the first beat.

## What Claude contributed (Claude Code, model Claude Opus 5.5, session of 2026-10-24)

Claude drafted most of the text and all of the build code from my project description and answers. I reviewed it and remain responsible for it:

- drafted `PROJECT-BRIEF.md`, the narration in `beat_sheet.json`, and this folder's Markdown files, then revised them at my direction as the scope changed (see `FRICTIONAL.md`);
- gave an assessment of how strong the idea was, and suggested the additions I chose (quote check, running the code, changelog-based eval questions, a plain-model baseline);
- wrote `make_sheet.py`, `scene_body.py`, `build_reel.py` and the copied helpers (`finish_audio.py` and `preflight.py`, adapted from the toolkit's examples);
- checked factual claims against the snapshot and my repos (migration-guide lines, page count, commit hash, the CI trigger) and recorded them in `pinned-docs-pitch/FACTCHECK.md`; it caught its own "every push" error against `ci.yml`;
- transcribed the narration with faster-whisper and reworded three lines that Kokoro mispronounced;
- ran the toolkit's gates and recorded the results.

The film shows no Claude responses. The definitions card and the two `ShowTellCard` focus cards are the toolkit's templates. The rows on the focus cards are real data from my snapshot, not invented.
