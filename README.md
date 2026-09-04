# Fog & Friction

*Pilot a B-52 through Clausewitzian fog.*

A tiny browser arcade game that pokes fun at Air University's Air Command and Staff College and the theory it teaches. One HTML file, no dependencies, no build step. Runs anywhere Safari or Chrome does, including your phone.

**Play it:** https://YOUR-USERNAME.github.io/au-arcade/

## How to play

Tap, click, or press space to climb. Gravity does the rest.

- Fly the B-52 through the gaps in the stacks of assigned reading. Each stack you clear is one **objective**.
- Every 5 to 10 seconds the **fog** rolls in and you fly blind for a moment. The further you get, the longer it lasts.
- Watch the FOG lamp in the top-left. It flickers half a second before the whiteout so you can line up.
- Every so often **friction** gusts the plane up or down. It is a nudge, not a wall.
- Every five objectives, Clausewitz interrupts with a slide. You cannot dismiss it. This is faithful to the source material.

When you crash, you receive a post-mission assessment on the AU grading scale. Most people get an F. Most people did not do the reading.

## Files

```
index.html   the whole game: markup, styles, and script in one file
README.md    this
```

## Running it locally

Opening the file directly on a phone won't work: iOS previews HTML without running JavaScript. On a computer, double-clicking the file is fine. To test on a phone, either publish it (see below) or serve it from your computer:

```
python3 -m http.server 8000
```

then open `http://<your-computer's-IP>:8000` on the phone while both are on the same Wi-Fi.

## Publishing with GitHub Pages

1. Put the game in the repo as `index.html`.
2. Settings → Pages → Source: *Deploy from a branch*, branch `main`, folder `/ (root)`.
3. Wait a minute or two. The site appears at `https://<username>.github.io/<repo>/`.

Commits to `main` redeploy automatically.

## Tuning

Everything worth adjusting lives near the top of `update()` and in the content arrays at the top of the script.

| What | Where | Default |
|---|---|---|
| Fog interval | `nextFog = t + rnd(5, 10)` | 5–10 s |
| Base fog length | `0.7` in `fogDur = clamp(0.7 + score * 0.06, 0.7, 2.6)` | 0.7 s |
| Fog growth per objective | `0.06` in the same line | +0.06 s |
| Longest fog | `2.6` in the same line | 2.6 s |
| Friction gust interval | `nextFriction = t + rnd(9, 16)` | 9–16 s |
| Gap between book stacks | `const gap = 165` | 165 px |
| Scroll speed | `150 * dt` (appears twice) | 150 px/s |
| Theorists on the spines | `THEORISTS` array | 12 names |
| Interrupting quotes | `QUOTES` array | 9 quotes |
| Post-mission grades | `GRADES` array | A through F |

## Adding more games

Give each game its own folder with its own `index.html`:

```
au-arcade/
  index.html            landing page (optional)
  fog-and-friction/
    index.html
  turabian-run/
    index.html
```

Each is then live at `https://<username>.github.io/au-arcade/<folder>/`.

## Credits and disclaimers

Quotes are Clausewitz, mostly. One is Moltke. A couple are not anyone's.

Not affiliated with Air University, the U.S. Air Force, or the Department of Defense. Obviously.
