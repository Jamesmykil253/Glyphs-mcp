<!-- 
  SUPPLEMENT to CLAUDE.md (Studio root).
  Brain hierarchy: CLAUDE.md (authoritative) → this file (project supplement) → AGENTS.md (session primer)
  This file provides Copilot-specific Glyphs-MCP details. CLAUDE.md is the primary brain.
  NOTE: This project also has its own CLAUDE.md at project root — load that for full project brain.
-->

# GitHub Copilot — Project Instructions

## Project: Glyphs-MCP — Font Design Pipeline

A Model Context Protocol (MCP) server bundled as a Glyphs 3 plugin. Exposes GlyphsApp APIs as JSON-RPC tools over the MCP Streamable HTTP transport on port 9680.

---

## Key Paths

| Area | Path |
|---|---|
| MCP source | `src/glyphs-mcp/` |
| Plugin bundle | `src/glyphs-mcp/Glyphs MCP.glyphsPlugin` |
| Documentation | `Documentations/` |
| Install scripts | `scripts/` |
| Project brain | `CLAUDE.md` (project-level — load for full context) |
| Codex reference | `CODEX.md` |
| MCP protocol docs | `MCP.md` |

## Ignored Paths (Do Not Search)

`glyphs-build-env/`, `__pycache__/`, `*.pyc`, `node_modules/`

---

## Workflow Rules

1. **Ask before editing.** Get explicit user approval before modifying files.
2. **No secrets.** Never expose API keys, tokens, or credentials.
3. **Verify after edits.** Confirm MCP server starts cleanly and tools respond.
4. **Keep changes small.** Glyphs plugin changes require plugin reload in Glyphs 3.

## Critical Constraints

- **MCP transport:** Streamable HTTP (SSE) on `http://127.0.0.1:9680/mcp/` — loopback ONLY
- **Python runtime:** Uses Python from Glyphs 3 (`~/Library/Application Support/Glyphs 3/Scripts/site-packages`)
- **Dependencies install path:** `~/Library/Application Support/Glyphs 3/Scripts/site-packages`
- **Plugin location:** `~/Library/Application Support/Glyphs 3/Plugins/Glyphs MCP.glyphsPlugin`
- **Start server:** Glyphs 3 → Edit → Start MCP Server
- **Session header:** Preserve `Mcp-Session-Id` header in all requests
- **Never expose beyond localhost.** Add auth before exposing the transport.
- **Read before mutate:** Always call `get_selected_font_and_master` + glyph reads before any edit.

## MCP Tools Available

| Category | Tools |
|---|---|
| Font info | `list_open_fonts`, `get_font_masters`, `get_font_instances` |
| Glyph inspection | `get_glyph_details`, `get_glyph_paths`, `get_glyph_components`, `get_selected_glyphs` |
| Glyph editing | `create_glyph`, `delete_glyph`, `copy_glyph`, `add_component_to_glyph`, `add_anchor_to_glyph` |
| Metrics | `update_glyph_metrics`, `update_glyph_properties`, `set_kerning_pair`, `save_font` |
| Scripting | `execute_code`, `execute_code_with_context`, `get_selected_font_and_master` |
| Documentation | `docs_search`, `docs_get` |

## Tech Stack

- **Application:** Glyphs 3 font editor
- **Plugin type:** Glyphs 3 Python plugin
- **MCP protocol:** Streamable HTTP (SSE), port 9680
- **Python:** Glyphs embedded Python
- **IDE:** VS Code + GitHub Copilot

## Studio Brain Cross-Reference

| Resource | Location |
|---|---|
| Master routing | `/Users/nsa/Studio/CLAUDE.md` |
| Session primer | `/Users/nsa/Studio/AGENTS.md` |
| Domain skills | `/Users/nsa/Studio/.github/skills/` |
| Agent definitions | `/Users/nsa/Studio/.github/agents/` |
| Error log | `/Users/nsa/Studio/.learnings/ERRORS.md` |
| Creator corrections | `/Users/nsa/Studio/.learnings/CORRECTIONS.md` |
| Creator voice profile | `/Users/nsa/Studio/.memory/creator-profile.md` |
| System docs (ground truth) | `~/Documents/AI/Studio-System-Docs/` |
