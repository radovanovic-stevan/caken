# Cakhenn

A side-scrolling beat 'em up in the spirit of Streets of Rage, played by **scrolling**.

Pick a level from the menu, then scroll down (mouse wheel, trackpad, or swipe on a phone) and the
fight plays out. Scroll up to rewind. Beat a level and you're taken back to the menu with the next
one unlocked. Progress is saved in your browser.

| Level | Where | Boss |
|---|---|---|
| 1 | Neon Street | Big Mo |
| 2 | Subway | Volt |
| 3 | Harbor | Anchor |
| 4 | Rooftop | Mr. Kane |

Everything is a single self-contained `index.html` with no assets, libraries or build step. The
pixel art, backgrounds and font are all drawn in code on a `<canvas>`.

## Run locally

Open `index.html` in a browser.

## Deploying

`.github/workflows/pages.yml` publishes the site to GitHub Pages on every push to `main`, and can
also be run by hand from the Actions tab.

## How it works

- The scroll position maps to a "story time" `t`. Each level is a pure function of `t`, so
  scrolling backwards plays it in reverse.
- Each level's fight is scripted in the `LEVEL SCRIPTS` section of `index.html` with calls such as
  `attack(...)`, `enemyAttack(...)`, `jumpKick(...)`, `throwE(...)`, `special(...)` and
  `pickup(...)`. Its scenery comes from a theme in the `THEMES` section.
- Rain, lightning, passing trains and blinking lights run on real time, so the scene stays alive
  when you stop scrolling.
