# Below the Dead v53 — additional memory optimization

## Change
- Converted eager white hit-flash canvas generation into on-demand generation. At startup, sprite sheets no longer allocate a second full-resolution canvas solely for the white flash effect.
- The flash is still drawn from the original decoded pixels; no sprite was resized or recompressed.
- Retained the five split boss sheets, earlier asset restoration, offline and safety fixes, help system, countdown, and food/save improvements.
- Updated service-worker cache key so a new deployment will refresh the app.

## Checks completed
- Game JavaScript and service-worker JavaScript syntax: passed (Node --check).
- 132 frame rectangles for five split sprite sheets fit inside the appropriate split texture.
- All 208 WebP files decode successfully.
- All 208 WebP files are byte-identical to the previous v52 candidate.
- ZIP integrity: checked after packaging.

## Remaining tests before publishing
- Browser-based visual smoke test for bosses, hit flashes, transitions, offline reload and sprite rendering.
- Eight-chapter progression and older-save compatibility.
- Mobile FPS, memory and touch control tests; this optimization is a memory-allocation improvement, not a measured FPS result.
- Real payment and ad integrations are not enabled.

## Suggested quick test tomorrow
1. Open the test build in a fresh browser profile.
2. Start Maya stage 1, shoot zombies and confirm white hit flashes look normal.
3. Test Ben with auto-aim and compare Medium/Hard.
4. Test the five split-sheet enemies/bosses (Ironhide, Manager, Barnacle, Ringmaster, Mother) and watch for missing frames.
5. Export your save, test import and restore on a separate test profile.
6. Check the game on an Android or iPhone, especially after 10 minutes of continuous combat.
