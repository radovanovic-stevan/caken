# Scroll of Rage

A tiny side-scrolling beat 'em up in the spirit of Streets of Rage, played entirely by **scrolling**.
There are no controls: scroll down (mouse wheel, trackpad, or swipe on a phone) and the hero walks
the neon street, brawls through three waves of punks, smashes a barrel for a roast turkey, and takes
down the boss at Dock 9. Scroll up to rewind.

Everything is a single self-contained `index.html` with no assets, libraries or build step. The
pixel art, backgrounds and font are all drawn in code on a `<canvas>`.

## Run locally

Open `index.html` in a browser.

## Host on GitHub Pages

1. Merge this into your default branch (e.g. `main`).
2. In the repo, open **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, pick `main` and `/ (root)`, then save.
4. After a minute it's live at `https://<your-user>.github.io/<repo>/`.

## How it works

- The scroll position maps to a "story time" `t`. The whole game is a pure function of `t`, so
  scrolling backwards plays it in reverse.
- The fight choreography (walks, combos, jump kicks, knockdowns, the boss fight) is scripted once
  at load time into keyframed timelines in the `SCRIPT / CHOREOGRAPHY` section of `index.html`.
  To change the fight, edit the calls such as `attack(...)`, `enemyAttack(...)`, `jumpKick(...)`
  and `special(...)`.
- Rain, breathing and blinking lights run on real time, so the scene stays alive when you stop
  scrolling.
