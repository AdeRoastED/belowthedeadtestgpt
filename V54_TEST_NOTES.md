# Below the Dead v54 — test jump candidate

## Added
- Visible Test Mode toggle in Settings → Game (no secret seven-click gesture).
- Chapter and stage selectors for all eight chapters and five stages each.
- PLAY STAGE activates test mode, applies existing settings save handler, and opens survivor selection for the chosen stage.
- Test mode already bypasses stage locks, chapter release dates, and food charges.
- Offline service-worker cache key bumped to avoid reusing v53 HTML.

## Important limitations
- Test mode does not isolate gameplay saves: rewards/progress earned in test mode may still be saved. Export a save code first, and restore it after testing if desired.
- Automated checks cover JS syntax, service worker syntax, ZIP CRC, and structural presence of the new controls. No real browser/mobile playthrough was completed.
- Purchases and rewarded ads remain disabled prototypes.

## Suggested playtest
1. Export your save code from Settings → Game.
2. Enable Test Mode; jump to chapter 8 stage 5, select Ben and try the final boss.
3. Try chapters 5–8 boss fights, checking split sprite animations.
4. Try a normal early stage on Medium and Hard with Maya and Ben.
5. Turn Test Mode off when finished; restore your backup if testing changed your save.
