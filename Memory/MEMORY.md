Router: 9router ~/9router svc :20129, dash admin/9router-admin; omni→OmniRoute :20128/v1, combo Work (omni/auto/cheap→best-fast→best-free→offline→best-coding→best-reasoning); streaming-only (502); NoAuth LLM died 2026; Hermes model.default=Work.
§
Tool order: DDG fast → web_fetch URL → Agent Reach/Jina → browser_navigate fallback → browser-harness (chỉ khi được yêu cầu). Search Google (không Bing); bị chặn → stealth/site-specific.
§
codebase-memory MCP: tên project phân biệt gạch nối/spaces (General-data ≠ General data); re-index cùng tên = update; index file lẻ: để trong .codebase-memory/ và trỏ repo_path vào đó.
§
Cron: disk watchdog 30m active (disk ≥85% báo TG, script disk_watchdog.sh); proxy-watchdog PAUSED → OmniRoute die phải chạy tay fix-omniroute.sh; context-watchdog disabled; SkillClaw :30000 retired (Option B, không restart).
§
Docs preprocessed (dediac, ## heading): labor.md, tcvn-9394/, tcvn-7888/ trong ~/.hermes/cache/documents/. Projects: General-data (quét toàn documents, 675 nodes — đã gộp hermes-cache-docs), Luat-lao-dong, TCVN-9394, TCVN-7888. Tra: grep / name_pattern→get_code_snippet; BM25 không index markdown.
§
TCVN 7888:2014 l2 = 'TCVN-7888'. Bảng 1 (Mcr A300-60=24,5kNm; C80≥80MPa): file cũ .codebase-memory/TCVN 7888.md (OCR mới mất số); Bảng 4 & Pmax≤80%Rnh: tra index.
§
GDrive: Tencent folder 1nkVBP75P1O6_kxVEZ; token.json + client_secret ĐÃ MẤT (7/2026) — cần user re-auth để phục hồi daily cache.
§
Template USER/MEMORY: ~/.hermes/memories/template.md.
§
PC bar demand: rate table trong documents/PC-bar-calculation.md (A300-70→7.1mm 0.0019t/m; A350→7.1mm 0.0022; A400→7.1mm 0.0032; A500→9.0mm 0.0045; A600→9.0mm 0.0060; B/C dùng 9.0/10.7mm). Forecast: doc_11830de9db2a_pc-bar-forecast.md (7.1mm Aug 150t thiếu ~20t; 9.0mm 50-60t đủ; tổng Aug 200t). KL = Rate×mét.
