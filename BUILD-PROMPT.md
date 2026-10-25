# How to rebuild this film

## The prompt that started it (Claude Code, 2026-10-24)

I pasted the full assignment text into Claude Code, then answered three questions:

- **Project:** "Version-Aware Docs Q&A Agent — an agent that answers questions about one fast-changing library (e.g. LangGraph, FastAPI, or Pydantic) from a frozen, dated snapshot of its official docs, citing the exact doc page and section for each answer. It refuses when the docs don't cover the question."
- **Narration:** Kokoro voice, reading my script.
- **Skills:** evals and test sets are new; agent loops and prompt contracts are new.

Claude found the existing snapshot at `~/INFO7375/snap/pydantic-v2.14.1` and built a first cut with the toolkit's `show-tell` skill. It adapted the skill to use no instructor persona, handle or brand bug.

I then corrected the scope: "It is an agent that will answer questions about technical documentation from the official documentation. Python and Pydantic are just examples. The user is a coder who wants to read documentation to see the changes made in various versions, because LLMs like Copilot might hallucinate and refer to previous versions."

After an assessment of how strong the idea was, I asked for additions that are "simple to do but good". I chose the quote check, running code at the pinned version, changelog-based eval questions, and a plain-model baseline. Two beats (B02, B13) now show real snapshot data on `ShowTellCard` focus cards. The full sequence is in `FRICTIONAL.md`.

## Requirements

- The brutalist.art checkout at `~/INFO7375/brutalist.art` (commit `a99b5323`), set up with `./setup --install`.
- The toolkit's Python venv at `~/INFO7375/.venv`, which has kokoro-onnx, manim 0.20.1 and faster-whisper.
- ffmpeg and node (for Remotion).
- To check the facts: the Pydantic snapshot (see `SNAPSHOT.md`).

## Commands

```bash
source ~/INFO7375/.venv/bin/activate
cd final-project-film/pinned-docs-pitch
export ART_HOME=~/INFO7375/brutalist.art

python3 make_sheet.py                                            # 1. beat_sheet.json from the script
python3 $ART_HOME/runtime/scripts/generate_audio_kokoro.py .     # 2. narration (local Kokoro, $0)
python3 finish_audio.py                                          # 3. pad bookends, lock measured durations
python3 $ART_HOME/runtime/scripts/align.py .                     # 4. word clock (faster-whisper)
python3 make_sheet.py                                            # 4b. re-run: sets the focus-card cues from the word clock
python3 build_reel.py                                            # 5. self-contained scenes.py + FACTCHECK/SHOTLIST/PROMPTS
python3 preflight.py                                             # 6. static + layout audits, last-frame contact sheets in _qc/
$ART_HOME/art run   . --height 2160                              # 7. Gates F, A, B, V + review cut
$ART_HOME/art final . --height 2160 --out exports/landscape      # 8. GATE T + clean master
```

To check pronunciation after step 2, transcribe the beats with faster-whisper (`WhisperModel("small")`) and compare against `narration_text`. The script originally said "dict" and "AI engineer"; both were reworded because Kokoro voiced them wrongly (see `FRICTIONAL.md`).

If you edit a scene, move its clip in `manim/<BID>.mp4` (and `media/`) into `_superseded/` before re-running `art run`. Only missing clips are re-rendered.
