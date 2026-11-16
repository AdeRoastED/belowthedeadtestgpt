# Below the Dead — sprite-safe candidate (not a certified release)

## Sprite quality and compatibility
- Five over-wide boss/enemy WebP sprite strips were divided at **existing animation-frame boundaries**, into 16 smaller lossless WebP images (maximum 2,048 pixels wide per segment).
- Their original image data was not resized. Reassembling every strip from the segments produces **pixel-identical RGBA pixels** to the original decoded artwork (verified programmatically).
- The JavaScript sprite loader, frame renderer, comic renderer, flash silhouettes, tint handling, and service-worker prefetch list were updated to support split sheets.
- All WebP images in the candidate now have a maximum dimension of 4,096 pixels. This is a conservative compatibility target, not a measured GPU guarantee.
- All referenced service-worker sprite paths exist in the package, and all WebP files decode.

## Prior fixes retained
- Restored 23 previously absent assets.
- Food charge deferred until a run launches; free training/defense and reduced replay prices.
- Save import validation and import backup/restore.
- Repeatable help screens, training-room tutorial replay, safe-house floor countdown.
- Dead enemies excluded from separation; offline fallback corrected; prototype purchases and rewarded ads disabled.

## Not yet verified
- Actual gameplay rendering and boss animation after sprite splitting on Chrome, Safari and Android devices.
- End-to-end chapter/boss progression, touch responsiveness, FPS and graphics memory.
- Legacy v44/v49/v51 save imports and interrupted-storage scenarios.
- Difficulty balancing and payment/ad-provider integration.

## Suggested smoke test before publishing
1. Clear the test site's service-worker cache or use a fresh browser profile.
2. Start a campaign stage and confirm enemies render and take damage.
3. Check General Stompwell/Ironhide, Manager, Barnacle, Ringmaster, Mother: walk, attacks, hit flashes, death, and comic scenes.
4. Test offline reloading and a previously cached stage.
5. Export a save, import into a separate test profile, then restore the backup.
6. Repeat on a lower-end Android phone and an iPhone.
