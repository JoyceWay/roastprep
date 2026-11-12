# 🧠 GEMINI CONTENT FACTORY — Season & Episode Generation Spec
> Owner: Gemini (Chief Strategist) — batch-generates episode scripts. Consumer: `game.html` (`buildEpisodes()`) and `data/s01_seed.json`. Verifier: Muse (facts, numbers, links) — never ship an episode Muse has not fact-checked.
>
> ⚠️ **Schema source of truth**: this document was aligned to the REAL `game.html` v3.2 schema on 2026-11-12 (Muse). If the game changes, update this file first — a mismatch means new episodes will not load.

## 1. The 8-Season Matrix

| Season | Theme | Episodes | Words | Status |
|---|---|---|---|---|
| S01 | Time-Travel History (seed: Versailles, Galileo, Pompeii) | 30 | 300* | 🟢 Seed 3 done, 27 to generate |
| S02 | Science & Discovery | 30 | 300 | ⚪ Proposed slot — founder to confirm theme |
| S03 | Literature & Storytellers | 30 | 300 | ⚪ Proposed slot — founder to confirm theme |
| S04 | Geography & Civilizations | 30 | 300 | ⚪ Proposed slot — founder to confirm theme |
| S05 | Arts & Music | 30 | 300 | ⚪ Proposed slot — founder to confirm theme |
| S06 | Civics & Leadership | 30 | 300 | ⚪ Proposed slot — founder to confirm theme |
| S07 | Money & Everyday Life | 30 | 300 | ⚪ Proposed slot — founder to confirm theme |
| S08 | Mixed Review & Boss Rush | 30 | 300 | ⚪ Proposed slot — founder to confirm theme |

- *Word-count rule (decided by founder + Gemini, 2026-11-12): **10 words per episode, 30 episodes = 300 words/season**. Composition is **6 + 2 + 2**: words 1–6 are the Stage 1 chat sticker words; words 7–8 are the Stage 2 boss options (both, right + tempting-wrong); words 9–10 are the Stage 3 SAT correct answer + 1 high-frequency SAT choice. Chat stays at **6 messages** (90-second pace). All 10 words must be **distinct** — if a boss or SAT word already appears among the 6 chat words (e.g. E01 `candid`, E02 `corroborate`, E03 `dormant` / `ephemeral`), take the next high-frequency choice instead. Seed episodes S01E01–E03 were padded to 10 on 2026-11-12 (Muse) — 30 words total.
- S02–S08 themes above are **proposals, not decisions**. Founder confirms or renames each theme before Gemini generates it.
- Season 2 includes the Founding 50 NPC pet cameo (see PROJECT_BRAIN.md M5).

## 2. `EPISODES` Schema — the real one from `game.html`

One episode = one object inside the array returned by `buildEpisodes()`. Keys are the contract with the game — renaming a key breaks loading.

```json
{
"code": "S01E01",
"title": "Versailles VIP Group Chat (1788)",
"subtitle": "Plastic Cliques & Royal Drama",
"channel": "💬 1788_VERSAILLES_BESTIES",
"vocab": {
"ostentatious": {
"word": "ostentatious",
"pos": "adj. /ˌɑː.stenˈteɪ.ʃəs/",
"def_en": "Excessively showy and designed to flex or attract attention.",
"def_zh": "炫耀卖弄的；浮夸招摇的",
"root": "ostent (stretch out to view) → shoving your price tag in everyone's face.",
"story_hook": "Wearing a 3-foot solid gold sailboat on top of your wig just to eat cereal.",
"savage_roast": "Loud flexing with zero taste. Bringing a diamond-crusted Stanley cup to 1st-period math.",
"synonyms": ["flamboyant", "pretentious", "gaudy"]
}
},
"chat": [
{
"sender": "${PETS.c1}_Ivy_Cat",
"tag": "Chief Auditor",
"avatar": "😺",
"isPet": true,
"en": "Fascinating. I usually stay aloof from human nonsense...",
"zh": "真精彩。我向来对人类的蠢事保持……"
}
],
"boss": {
"headline": "Duke Orléans Tried to Frame ${PETS.c2} & ${PETS.d1}!",
"headline_zh": "奥尔良公爵想把偷吃蛋糕的锅甩给 ${PETS.c2} 和 ${PETS.d1}！",
"context": "The Duke knocked over the Queen's cake...",
"context_zh": "公爵打翻了王后的多层奶油蛋糕……",
"sentence": "“Drop the innocent act, Duke! Your apology is totally ______ …”",
"sentence_zh": "“收起你那套无辜演技吧公爵！你的道歉完全是……”",
"options": [
{ "word": "disingenuous", "zh": "虚伪狡诈的；假装无辜/不知情的", "desc": "Insincere; pretending to be more innocent than one really is", "correct": true},
{ "word": "ingenuous", "zh": "真正天真无邪的；坦率真诚的", "desc": "Truly innocent, artless, and candid; childlike honesty", "correct": false}
],
"wasted_title": "💀 VERBALLY WASTED // You Called the Scheming Duke a Pure Angel!",
"wasted_body": "<b>Ingenuous</b> means genuinely innocent!...",
"wasted_zh": "Ingenuous 是“真纯洁无瑕”！……",
"win_body": "BOOM! <b>Disingenuous</b>... exposed his act in front of the whole palace!",
"win_zh": "漂亮绝杀！Disingenuous（虚伪装无辜）当场戳破公爵的绿茶演技，全场贵族笑翻！"
},
"sat": {
"passage": "In the final decade before the French Revolution, memoirs from Versailles reveal... ______ allegiance...",
"passage_zh": "在法国大革命爆发前的最后十年里，凡尔赛宫回忆录揭示了……",
"choices": [
{ "letter": "A", "word": "gregarious", "zh": "爱交际的；合群的", "correct": false},
{ "letter": "B", "word": "perfidious", "zh": "背信弃义的；当面一套背后一套的", "correct": true},
{ "letter": "C", "word": "candid", "zh": "坦率直言的", "correct": false},
{ "letter": "D", "word": "austere", "zh": "简朴严厉的", "correct": false}
],
"hack_en": "Look at the colon (:)—everything after it defines the blank!...",
"hack_zh": "盯紧冒号（:）后面的同义解释！……"
}
}
```

Field rules (verified against the seed data, 2026-11-12):
- `code`: `S01E01` … `S01E30` — season + episode-in-season. (v3.2 shipped S02E01/S03E01 by mistake; Muse renumbered to S01E02/S01E03.)
- `vocab`: an **object keyed by the word itself** (not an array). **10 entries per episode: 6 chat sticker words + 2 boss-option words + SAT correct answer + 1 high-frequency SAT choice** (see §1). All 10 distinct — dedup against the chat words first (a boss/SAT word that duplicates a chat word does not count twice; take the next high-frequency choice). Every entry carries all 8 fields: `word`, `pos` (with IPA), `def_en`, `def_zh`, `root`, `story_hook`, `savage_roast`, `synonyms[]`.
- `chat`: 6 messages per seed episode. `sender` uses `${PETS.c1}`-style placeholders — never hard-code pet names. Every message has both `en` and `zh`.
- `boss.options`: exactly 2 — one `correct: true`, one `correct: false`. `desc` is the English definition shown after answering.
- `sat.choices`: exactly 4, letters A–D, one `correct: true`.
- Every English string that the player reads has a Chinese twin (`_zh` / `zh`). `story_hook`, `savage_roast`, and `root` are English-only in the seed — known gap, see §4.
- `wasted_title` / `wasted_body` / `win_body` render with HTML (`<b>` allowed). `wasted_zh` / `win_zh` are the Chinese twins.

## 3. Batch Prompt (copy-paste to Gemini, one batch = 5 episodes)

```
You are the head writer for RoastPrep, a gamified SAT vocabulary game for
North American teens (G5-G12) and bilingual Chinese families.

Write FIVE episodes as a JSON array following the EPISODES schema in
./ai_vault/03_GEMINI_CONTENT_FACTORY.md section 2. Do not change any keys.
Copy the key names and nesting exactly — the game loads them verbatim.

Season: S01 — Time-Travel History. Episodes: <N>–<N+4> — <historical scenes>.
Words: 10 per episode, SAT-level, composition 6 + 2 + 2 (see §1). The 6 chat
words appear as highlighted stickers in the 6 chat messages; the 2 boss words
are the two boss-battle options; the SAT words are the correct answer + 1
high-frequency choice. All 10 must be distinct — if a boss or SAT word already
appears among the 6 chat words, take the next high-frequency choice instead.

Voice rules:
- Poppy (cat1) roasts with deadpan academic precision. Mochi (cat2) is
chaotic and snack-obsessed. Luna (cat3) gossips. Boba (cat4) critiques
fashion and vibes. Buster (dog1) translates hard words into excited
dog logic.
- Funny first, accurate always. Historical facts must be true — if you are
unsure of a date or a quote, leave it out rather than inventing it.
- Chinese translations must read like natural spoken Chinese, not
translationese. Teen slang is welcome where it fits; never force it.
- Never hard-code pet names — use ${PETS.c1} / ${PETS.c2} / ${PETS.c3} /
${PETS.c4} / ${PETS.d1} inside strings.
- Spelling: the second cat is Mochi, never Mocchi.

Output: the JSON array only, no markdown fences, no commentary.
```

Batch size: 5 episodes per run. After each batch, hand the JSON to Muse for the fact check before it enters `game.html` or `data/`.

## 4. Hard Rules for Gemini

1. Never invent a historical fact, date, or quote. Omit what you cannot verify.
2. Never hard-code pet names — use `${PETS.c1}` / `${PETS.c2}` / `${PETS.c3}` / `${PETS.c4}` / `${PETS.d1}`.
3. Never write `Mocchi`. It is always `Mochi`.
4. Every player-facing `_en` field ships with its `_zh` twin in the same object.
5. SAT passages must read like real SAT words-in-context items (academic tone, one clear best answer, three plausible distractors).
6. Boss battle = 2 options (right vs. tempting-wrong). SAT = 4 choices (A–D).

## 5. Known Gaps (not blocking launch)

- `story_hook` / `savage_roast` / `root` have no Chinese twins yet — the vocab drawer shows the English hook even with the lens ON. M4 follow-up: add `story_hook_zh` / `savage_roast_zh` / `root_zh` when batch-generating, or accept English-only flavor lines.
