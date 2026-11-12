# 🔄 AI RELAY BOARD (跨 AI 传话筒与进度报告)
> **Rule for All AIs**: Read the latest entry below before starting. When finished, append a new timestamped block at the top so the founder can copy-paste it to the next AI.

---
### 🟢 [2026-11-12] From: Muse (Systems Architect) ➡️ To: Founder & Next AI
- **Deploy status (GitHub Pages path)**:
  1. GitHub Pages enabled on `JoyceWay/roastprep` (source `main`, `/`) — live at https://joyceway.github.io/roastprep/ (HTTP 200, Guru hub title verified).
  2. Custom domain set via API: `cname: roastprep.com`, `html_url` now http://roastprep.com/ (status: building at time of set).
  3. **Remaining step = DNS only.** `roastprep.com` is at Cloudflare (registrar Cloudflare, Inc.; nameservers KEVIN/RAYNE.NS.CLOUDFLARE.COM; current A `198.18.81.175` serves nothing). In Cloudflare DNS (Puchiing account): replace the apex A record with GitHub Pages' four IPs — `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` — and add `www` CNAME → `joyceway.github.io`. GitHub then provisions HTTPS automatically. Blocked on the Puchiing Cloudflare password (saved one confirmed wrong); founder to re-enter it or paste the records herself.
  4. Note: `game.html` on the github.io URL now 301-redirects to the custom domain (expected once cname is set).

---
### 🟢 [2026-11-12] From: Muse (Systems Architect) ➡️ To: Founder & Next AI
- **What Was Done** (closes items 1 + 3 from the previous Muse block; domain bought — see below):
  1. Received Gemini's `index.html` + `game.html` **v3.2** from the founder and copied them into the stack as `index.html` / `game.html`. Nav was already wired both ways in v3.2 (sticky dock → `./game.html`, `./PROJECT_BRAIN.md`, `./ai_vault/01_AI_RELAY_BOARD.md`; `game.html` top-left `🧭 Guru Hub` → `./index.html`) — verified, no changes needed.
  2. **3 surgical fixes to `game.html`** (Python heredoc, exact anchors, assert counts):
     - Check 1: `stage-chat` was missing `overflow-y-auto` and used `max-h-[78vh]` → now `min-h-[520px] max-h-[82vh] overflow-y-auto` like the other three stages.
     - Check 2 + 6: the smoke-test assertion was **self-defeating** — `document.body.innerHTML.includes("Mocchi")` always trips because `innerHTML` includes the `<script>` block's own source text. Rewrote it to `innerText` + a dynamically built string (so the literal never appears in the file; `Mocchi` count in `game.html` is now **0**), aligned the log to the protocol's exact `✅ ALL QA CHECKS PASSED`, and extended the test to walk stages 1→4.
     - Episode codes were wrong: `S02E01` / `S03E01` → renumbered `S01E02` / `S01E03` (S01E01 unchanged).
  3. Extracted the 3 seed episodes into `data/s01_seed.json` (replaces the skeleton): S01E01 Versailles, S01E02 Galileo, S01E03 Pompeii — 6 vocab words each, **18 total**, valid JSON, 0 `Mocchi`. `${PETS.*}` placeholders preserved literally; the loader interpolates them from the 5-pet squad config.
  4. **Aligned `ai_vault/03_GEMINI_CONTENT_FACTORY.md` to the REAL game schema** — the doc's example schema was invented and did not match `game.html`. Real schema now documented verbatim: `vocab` is an object keyed by word; `chat` = 6 messages with `en`/`zh` twins; `boss.options` = exactly 2; `sat.choices` = exactly 4 (A–D). The batch prompt now points at the real schema.
  5. **Verification — static: all 6 QA checks green** (stage classes, scrollIntoView in both handlers, `Mocchi` = 0, lens toggle + `?lens=zh` + zh twins in all 3 episodes, pet modal + URL params + copy link, TTS buttons ×4, smoke test + `?test=1` + exact log string, all relative links resolve). **Live browser (Playwright, `?test=1`): `✅ ALL QA CHECKS PASSED`, 0 page errors, 0 QA FAIL assertions.**
  6. **Pushed to GitHub: `JoyceWay/roastprep`, commit `2539111`, 11 files, branch `main`.** Repo page verified live (HTTP 200).
- **Known Gaps (not blocking launch)**:
  1. Tailwind CDN + Google Fonts did not load in the sandbox browser (proxy `ERR_TUNNEL_CONNECTION_FAILED`), so the **styled look is unverified here** — the screenshot shows correct content/logic in unstyled fallback. Check the design in a real browser or after deploying to roastprep.com.
  2. `story_hook` / `savage_roast` / `root` have no Chinese twins yet — the vocab drawer shows the English hook even with the lens ON. M4 follow-up: add `*_zh` fields when batch-generating.
  3. Season word-count question: seed episodes carry 6 words each, but the 300-word season target implies 10/episode for episodes 4–30. Founder / Gemini to confirm: pad the seed episodes to 10, or revise the season total to 180.
  4. `roastprep.com` is bought but has **no site yet** — the repo push alone does not put it online. Next step: Cloudflare Pages project (or GitHub Pages) pointed at this repo. Blocked on the Puchiing Cloudflare password (confirmed wrong) until the founder re-enters it.
- **Immediate Action Required from Next AI**:
  1. M4 (Nov 16–20): batch-generate Season 1 episodes 4–30 per the **aligned** factory doc §2–§3, then hand each batch to Muse for fact-checking before it enters `game.html`.
  2. Deploy the repo to `roastprep.com` once the founder clears the Cloudflare access, then verify the styled render in a real browser.

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
