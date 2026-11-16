# Below the Dead — isolated candidate, 16 Nov 2026

This candidate builds on the earlier food-rule candidate. It is not a release-ready version and has not been tested through a full browser playthrough.

## Implemented
- Completed-stage replays cost 1 food; first-time normal and boss stages cost 2; training and defense cost 0.
- Updated food UI and fixed-price refund logic from the earlier candidate.
- Save-code imports now reject malformed or incompatible save structures (not just a bad checksum), including invalid currency, food, hero, upgrade fields, cleared flags, and dangerous object keys.
- Import asks for explicit confirmation, requires current progress to be saved, writes a pre-import backup, and verifies the newly written save before reloading. If verification fails, it attempts to restore the previous save.

## Tests performed
- All inline game JavaScript parsed with Node vm.Script.
- 15/15 targeted save-validation tests passed, including checksum round-trips, malformed save, negative currency, invalid hero, invalid food, invalid cleared flag, and prototype-pollution key.
- Previous food candidate had 13/13 isolated food-rule checks passing; these food rules were not modified in this pass.

## Important remaining limitations
- No full browser gameplay test, mobile FPS benchmark, or campaign playthrough has succeeded in this environment.
- Save validation is intentionally conservative and could reject an unusual legacy save; test import using actual exported saves from older builds before publishing.
- Import UI uses browser confirm; check appearance and behavior on mobile.
- Sprite-asset completeness, gameplay balancing, chapter pacing, tutorial relocation, reusable help, and floor countdown remain open.
- Purchases and rewarded ads are placeholders, not production-ready monetization.

Do not upload to production without testing with an exported copy of existing progress and checking all critical screens.

## Training Room relocation — additional isolated pass
- Removed tutorial replay control from Settings and its obsolete handler.
- Added a free Replay Tutorial control to the Training Range room alongside target practice.
- Reused the original tutorial-start logic for both the initial tutorial tile and the Training Range button; preserves Maya, stage 1-1, and the existing free-replay flag.
- Changed service worker cache identifier for this candidate to avoid retaining an old page on install.
- 10/10 targeted static assertions passed; main inline JavaScript and service worker pass Node syntax checks.
- Not yet verified through an interactive browser; do not treat this as a completed UI test.

## Contextual help — new candidate pass
- Added reusable, dismissible, reopenable help dialogs to main menu, level/stage selection, survivor selection, Hideout, Mini-Mart, missions, survivors, settings, purchases, kill map, zombie guide, and each Hideout room via its room panel.
- Help content uses textContent, not HTML injection. Closing does not persist a flag, so instructions remain available. Escape and backdrop click close the dialog.
- No gameplay balance, character stats, or story text changed in this pass.
- Node syntax check passed and targeted static wiring checks passed.
- IMPORTANT: browser visual/accessibility testing and room-by-room gameplay interactions still required before production deployment.


## Floor countdown candidate
- Added two-digit, seven-segment floor lamps just in front of the safe-house door during the hold phase.
- Reads `G.holdT` (same countdown used by `openSafe`), displaying 00 once the door opens.
- Uses deterministic low-frequency segment flicker and avoids new particles or timers.
- Needs visual testing at different zooms, chapter backgrounds and mobile sizes; not browser-verified.
