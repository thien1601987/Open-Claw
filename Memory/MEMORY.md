User: Nguyễn Thanh Thiện, FP&A & Planning Manager at VGSI PILE, 14+ years experience in FP&A, Power BI, Power Automate, SAP, S&OP, working capital optimization, digital transformation.
§
Works with PHC pile pricing (A350-65, A400-65); uses Google Drive; needs AI assistance for pricing calculations, report automation, workflow optimization.
§
Expects assistant to self-correct and proactively find tools when encountering problems.
§
OmniRoute local on port 20129 (key sk-94e3..., combo auto/best-coding).
§
Prefers responses in Vietnamese.
§
Preference: When encountering issues, proactively find tools instead of asking for direction.
§
Preference: Concise responses (<100 words) with rich text formatting (icons, bold, italics, bullets).
§
Preference: Data retrieval via codebase-memory-MCP/grep > chat history.
§
9Router running locally on port 20128; combos: clinepass, free-gh, free-or; default: custom:9-router/clinepass.
§
Prefers configuring ClinePass directly via https://api.cline.bot/api/v1 with API key sk_... to bypass 9Router latency.
§
Backup procedure: Create tar.gz of ~/.hermes (config.yaml, memories/, skills/, plugins/, google_token.json, cache/documents/, channel_directory.json), upload to Google Drive folder "Open-claw-Hermes-setup" (ID: 1Eg4f-Zf76XSAo5xqYzkIu5nq_VuxoQWx) using google-workspace skill's google_api.py. Token location: ~/.hermes/google_token.json (auto-refreshes if has refresh_token). OAuth on mobile/headless fails - restore token from backup instead.
§
GitHub Memory repo: https://github.com/thien1601987/Open-Claw/tree/main/Memory (contains MEMORY.md, USER.md, 5S-PRINCIPLES.md). When starting new session, after reset/restart, after model change, or after gateway restart: clone/pull repo, read Memory files to restore context. Use: `git clone https://github.com/thien1601987/Open-Claw.git /tmp/Open-Claw && cat /tmp/Open-Claw/Memory/MEMORY.md /tmp/Open-Claw/Memory/USER.md`