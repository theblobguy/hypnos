# Hypnos sleep

A sleep schedule and sleep-debt web app. No watch needed: you log each morning in about ten seconds.

## Put it on GitHub Pages

1. Create a new repository (for example `hypnos`) and upload every file in this folder to the root.
2. In the repo, go to Settings → Pages, set Source to "Deploy from a branch", branch `main`, folder `/ (root)`, and save.
3. After a minute, open `https://<your-username>.github.io/hypnos/` in Safari on your iPhone.
4. Tap Share → Add to Home Screen (leave "Open as Web App" on). Open it from the home screen icon from then on, so your data is kept with the installed app.

## Updating

Edit `index.html`, then bump `VERSION` in `sw.js` (for example `hypnos-v2`) so phones fetch the new version.

## Files

- `index.html`: the whole app (logic, styles, screens)
- `manifest.json`: name, colours and icons for the home screen
- `sw.js`: lets the app open offline
- `icon-*.png`: app icons

## How it works

- Sleep need starts from your age and free-day sleep, then adjusts by up to 15 minutes a week from nights you woke without an alarm and felt rested (only once debt is Low). It stays between 7 and 9.5 hours.
- Sleep debt: the last 14 nights, each night's shortfall weighted by 0.87^i (last night counts about 15%), scaled so the weights sum to 14. Extra sleep earns at most 2 hours of credit a night. It needs 5 logged nights; missing nights are filled with your median. Bands: Low under 2 h, Moderate 2 to 5 h, High over 5 h.
- Tonight's plan: lights out = wake anchor − (need + extra) − time to fall asleep. Extra is +30 min at Moderate and +60 min at High, and none while you're logging trouble sleeping.
- Chronotype and social jetlag use the Munich ChronoType Questionnaire formulas.
- Safety cards: the STOP-Bang breathing check (3 or more), trouble sleeping on 3 of 7 nights, drowsy driving, and feeling unrested with low debt.

Data lives only in the phone's browser storage. Use Download backup on the You tab now and then.

Hypnos is a wellness tool for adults, not a medical device.
