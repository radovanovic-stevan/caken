# Cakhenn

*Putting the "scroll" into side-scrolling.*

A side-scrolling beat 'em up in the spirit of Streets of Rage, played by **scrolling**.

Pick a level from the menu, then scroll down (mouse wheel, trackpad, or swipe on a phone) and the
fight plays out. Scroll up to rewind. Beat a level and you're taken back to the menu with the next
one unlocked. Progress is saved in your browser.

| Level | Where | Set-piece | Boss |
|---|---|---|---|
| 1 | Neon Street | Rainy street brawl | Big Mo |
| 2 | Subway | A gang pours out of an arriving train; you board it and fight on while it brakes and lurches | Volt |
| 3 | Harbor | Container ambush; the boss throws barrels (dodge one, kick one back) | Anchor |
| 4 | Rooftop | Boss rush of every earlier boss, then a helicopter drop onto the helipad | Mr. Kane |

There's an 8-bit soundtrack too: a menu theme, a track per level, boss music and a victory jingle.
It starts on your first tap or click (browsers block sound until then), and the **♫ ON/OFF**
button in the corner mutes it.

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
- The music is synthesized live with the Web Audio API (pulse-wave lead and arpeggios, triangle
  bass, noise drums). Songs are written in the `SONGS` table, one token per 16th note.
- Rain, lightning, passing trains and blinking lights run on real time, so the scene stays alive
  when you stop scrolling.
