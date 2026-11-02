---
"@callstack/repack": patch
---

Fix the dev server ignoring Ctrl+C and the `r`/`d`/`j`/`a` shortcuts when stdin was paused before it started. Raw mode delivers Ctrl+C only as stream data, and a stdin paused earlier in the process delivers nothing: Node's `Readable.unpipe()` pauses its source, which is how CLI prompt libraries close a prompt. `setupInteractions` now resumes stdin after entering raw mode, the way `@rock-js/plugin-metro` does.
