<!-- Source: https://github.com/dragthelake/ambient-context — fetched 2026-09-25 for reference only; not written by me -->
# Ambient Context (dragthelake/ambient-context)

> "writes down what you work on during the day to give your AI assistant better context"

A macOS menu bar app that records what you work on through the day as plain markdown.

## Three daily files
1. **Context**: raw chronological record of screen activity with timestamps, app names, and URLs/file paths
2. **Knowledge Base**: six structured pages (People, Commitments, Threads, Products, Issues, Reading) with citations linked back to source blocks
3. **Notes**: human-readable daily summary with work sessions and outcomes, generated from the knowledge base

## Capture & processing
- Reads text from the focused window via the macOS Accessibility API every few seconds
- Deduplicates repeated pages across the day
- Filters UI noise (timestamps, view counts, navigation menus)
- Routes messages to a separate `messages.md`
- Generates knowledge and notes via connected AI agents (Claude Code, Cursor, Codex, or generic MCP clients)

## Architecture & stack
- Tauri (Rust backend, TypeScript/Vue frontend); dev needs Node.js, Rust, Xcode CLT
- Ships an MCP server, registered in Claude Code, Cursor, Zed, or Claude Desktop
- Flow: grant Accessibility permission, pick storage folder, capture runs, agent CLI turns the daily record into knowledge base and notes

## Platform
- macOS 14+, Apple Silicon; signed, notarized DMG on GitHub Releases; `npm run tauri dev`

## Privacy
> "The record is yours and it stays on your computer"
- Local-only: no uploads, accounts, or telemetry
- No screenshots or OCR, text only from the accessibility API
- Passwords skipped at source; credentials, API keys, card numbers redacted to `[redacted]`
- Per-app recording toggles, headings-only mode, custom redaction patterns
- Plain, portable markdown files

## License
MIT, bundled Funnel fonts under SIL OFL

## Known limitations
- Chromium/Electron apps (Chrome, Slack, VS Code) give thin capture in the first seconds
- GPU-rendered terminals (Kitty, Alacritty) expose little text; Terminal.app and iTerm2 work
- Depends on the completeness of the macOS accessibility tree
