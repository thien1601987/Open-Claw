User: Nguyễn Thanh Thiện, FP&A & Planning Manager @ VGSI PILE, 14+ years experience. Expertise: FP&A, Power BI, SAP (PP/MM/SD), S&OP, working capital optimization, digital transformation. Works with PHC pile pricing (A350-65, A400-65); uses Google Drive.

§
AI providers: ClinePass (api.cline.bot, primary), 9Router (localhost:20128, fallback), OmniRoute (localhost:20129, backup), OpenRouter (cloud). Uses free-tier when available.

§
Backup: tar.gz ~/.hermes → Google Drive "Open-claw-Hermes-setup" (ID: 1Eg4f-Zf76XSAo5xqYzkIu5nq_VuxoQWx). Token: ~/.hermes/google_token.json (auto-refresh). OAuth mobile fails - restore from backup.

§
GitHub Memory repo: https://github.com/thien1601987/Open-Claw/tree/main/Memory (contains MEMORY.md, USER.md, 5S-PRINCIPLES.md). When starting new session, after reset/restart, after model change, or after gateway restart: clone/pull repo, read Memory files to restore context. Use: `git clone https://github.com/thien1601987/Open-Claw.git /tmp/Open-Claw && cat /tmp/Open-Claw/Memory/MEMORY.md /tmp/Open-Claw/Memory/USER.md`

§
Communication: Vietnamese, concise (<100 words), rich text (icons, bold, bullets). Proactive: find tools instead of asking direction, self-correct when errors occur. Data retrieval: codebase-memory-MCP/grep > chat history.

§
RAM: 2GB RAM thật + 1GB swap. Khi RAM vượt 1GB → bổ sung swap ngay để tránh OOM. Kill task gây phình RAM. Ưu tiên Hermes + model đang chạy là tối thượng. ZRAM đã bật (1GB, priority 100, persistent): module trong /etc/modules-load.d/zram.conf, udev rule /etc/udev/rules.d/99-zram.rules tự setup + swapon khi boot.