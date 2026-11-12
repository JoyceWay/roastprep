# 🔄 AI RELAY BOARD (跨 AI 传话筒与进度报告)
> **Rule for All AIs**: Read the latest entry below before starting. When finished, append a new timestamped block at the top so the founder can copy-paste it to the next AI.

---
### 🟢 [2026-11-12] From: Muse (Systems Architect) ➡️ To: Founder & Next AI
- **What Was Done**:
  1. Name locked: **RoastPrep.com** (founder picked it over RoastLearn / RoastAcademy). RDAP-verified 2026-11-12: roastprep.com and roastprep.org both show as available (final confirmation is the registrar checkout step).
  2. Scaffolded the GitHub stack at `~/workspace/roastprep-stack/`: `PROJECT_BRAIN.md`, `CLAUDE.md`, `.cursorrules`, `llms.txt`, `ai_vault/01–04`, `data/s01_seed.json` (skeleton — see below).
  3. Verified: `Mocchi` appears only inside spelling-rule sentences (the rule itself in `CLAUDE.md` / `.cursorrules`, QA check 2, factory hard rules) — never as a pet name; `s01_seed.json` parses as valid JSON.
- **What Is Still Pending (needs the founder)**:
  1. **Send `index.html` + `game.html` v3.0** (Gemini's build). A full-workspace search on 2026-11-12 found neither file in Muse's workspace, so wiring + QA fixes + seed extraction could not run yet.
  2. **Buy the domains** (roastprep.com + roastprep.org). Blocker: the Puchiing Cloudflare account password on file is confirmed wrong — founder must re-enter it, or buy at another registrar and point DNS to Cloudflare.
  3. **Create the GitHub repo manually** (JoyceWay account, passkey login). Muse's GitHub App token cannot create repos. Suggested name: `RoastPrep`. After creation, Muse pushes this stack.
- **Immediate Action Required from Next AI**:
  1. On receiving `index.html` + `game.html`: wire the nav links (`index.html` dock → `./game.html`, `./PROJECT_BRAIN.md`, `./ai_vault/01_AI_RELAY_BOARD.md`; `game.html` top-left `🧭 Guru Hub` → `./index.html`), apply all 6 checks in `./ai_vault/02_QA_AND_BUG_PROTOCOL.md`, extract the 3 seed episodes into `data/s01_seed.json` (replacing the skeleton), and log the report here.

---
### 🟢 [2026-11-12] From: Gemini (Chief Strategist) ➡️ To: Muse & Claude (Engineering & Stack)
- **What Was Done**:
  1. Finalized the Dual-Domain Strategy (`RoastPrep.com` + `RoastPrep.org`) and the 9 Commercial Levers.
  2. Built `index.html` (Guru Command Hub) and `game.html` (v3.0 Dreamy Teen Edition with 3 full bilingual episodes: Versailles, Galileo, Pompeii).
  3. Diagnosed the Stage 3 bug: when `🌐 中文 Lens: ON` expands `#sat-passage-zh`, fixed height `h-[540px]` clips `#sat-explanation` below the fold.
- **Immediate Action Required from Muse / Claude**:
  1. Scaffold the GitHub folder structure and link `index.html`, `game.html`, `PROJECT_BRAIN.md`, and `/ai_vault/*.md`.
  2. Apply the surgical fixes in `./ai_vault/02_QA_AND_BUG_PROTOCOL.md` to `game.html`.
  3. Run the automated verification checks and log your completion report here.
