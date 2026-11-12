# 🛠️ QA & BUG-FIX PROTOCOL FOR `game.html`
> Any AI inspecting or updating `game.html` MUST verify and pass all 6 checks below before returning code:

1. **Fix Stage 3 Viewport Clipping & Auto-Scroll (CRITICAL)**:
   - Replace fixed `h-[540px]` on `#stage-chat`, `#stage-boss`, `#stage-sat`, and `#stage-paywall` with `min-h-[520px] max-h-[82vh] overflow-y-auto`.
   - Inside `checkSATAnswer(isCorrect)` and `handleBossChoice(isCorrect, chosenWord)`, right after removing `.hidden` from `#sat-explanation` or `#boss-feedback`, trigger:
     `setTimeout(() => el.scrollIntoView({ behavior: 'smooth', block: 'end' }), 60);`
2. **Global Spelling Verification**:
   - Zero occurrences of `Mocchi`. Must be `Mochi` everywhere.
3. **Full-Stage Bilingual Lens (`🌐 中文 Lens: ON/OFF` & `?lens=zh`)**:
   - Toggling `zhLens` ON must display Chinese translations in Stage 1 (chat bubbles + vocab drawer), Stage 2 (boss headline, context, sentence, options, feedback), and Stage 3 (SAT passage translation, all 4 options, and Poppy's 10-second hack).
4. **5-Pet Squad Customizer Modal & URL Parameter Injection**:
   - Read `?cat1=...&cat2=...&cat3=...&cat4=...&dog1=...` from `window.location.search` (fallback to `localStorage`, then defaults: `Poppy, Mochi, Luna, Boba, Buster`).
   - Provide a top `🐾 Pet Squad` button opening a modal to edit the 5 pet names and copy a shareable custom link for classmates.
5. **Zero-Cost Pronunciation (`🔊`)**:
   - Add a `🔊` button on vocab cards and Stage 2/3 options calling `window.speechSynthesis.speak(new SpeechSynthesisUtterance(word))` (`en-US`).
6. **Built-In Smoke Test (`?test=1`)**:
   - Include `runAutomatedSmokeTest()` that logs `✅ ALL QA CHECKS PASSED` in the console when testing Stage 1->4 transitions and bilingual toggles.
