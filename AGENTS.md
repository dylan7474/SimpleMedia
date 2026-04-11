# AGENTS.md

Guidance for future AI coding agents working in this repository.

## Project overview

- This project is a **single-file static web app** centered around `index.html`.
- There is no framework build pipeline; prefer lightweight, dependency-free changes.
- `deploy.sh` is used to build and run a Docker image that serves static files.

## Working conventions

- Keep UI touch-friendly: large controls, high contrast, minimal interaction complexity.
- Avoid introducing heavy toolchains (bundlers/transpilers) unless explicitly requested.
- Favor clear, readable HTML/CSS/JS with descriptive function names.
- Preserve accessibility-minded behavior where possible.

## Docs and operations

- Keep `README.md` in sync with actual run/deploy behavior.
- If changing deploy/runtime behavior, update both `README.md` and `deploy.sh` together.
- For licensing changes, update `LICENSE` and reference the change in PR notes.

## Validation checklist

Before finalizing work:

1. Run shell checks for scripts when edited (e.g. `bash -n deploy.sh`).
2. Ensure docs instructions are copy/paste runnable.
3. Confirm repo remains runnable as a static site.
