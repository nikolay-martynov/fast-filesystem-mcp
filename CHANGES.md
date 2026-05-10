# Local Modifications

This is a personal fork of [fast-filesystem-mcp](https://github.com/efforthye/fast-filesystem-mcp) with custom modifications.

See git history for details (`git diff upstream/main`).

## Changes

- Add `newline` parameter to write/edit/extract tools (`auto`/`exact` mode) for proper CRLF handling on Windows: auto mode normalizes `\n` → `\r\n` on writes and matches `\n` in old_text against `\r\n` in files for edits
- Add ZIP compress/extract support via `archiver` and `unzipper` (replaces "use tar instead" errors)
- Reduce default read chunk size from 900KB to ~20KB (5k tokens) for better LLM context management
- Fix regex search: remove `g` flag to avoid `lastIndex` issues with `.test()`
- Add ripgrep-based fast filename search (`rg --files` + filter) with 30s timeout on manual walk fallback
- Add file metadata (size, dates, permissions) in search results