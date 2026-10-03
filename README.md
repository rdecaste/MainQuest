# MainQuest

The Goku (Main Quest) card, at https://mainquest.quest-engine.workers.dev
(Cloudflare, behind Roy's Cloudflare Access login), from `index.html`.

It reads its state from the Quest Engine (Cloudflare Worker,
`rdecaste/quest-engine`) at `GET /mainquest` (front) and `GET /hero` (back);
hero HP and heals come from `GET /boss`. How it works: `docs/quest-engine.md`
in rdecaste/quest-engine.

What the card shows:
- **Front:** Goku's clip, level, HP (with the ki shield in blue after it) and
  XP. During a 6-hour week the card glows Senzu green and shows the Senzu
  banner once. Nothing else goes on the front (Roy: keep the animation clear).
- **Back:** Scouter (a reading, the power level with the long-term and
  short-term load chart, gravity, this week, records), Moves, Forms, Log, Lore.
- **Log:** the last 14 days, one row each (Success, workouts, HP, XP). Tap a
  day to see what happened: every habit, heal and hit with its time and
  effect (`events` per day in `GET /hero`; today's taps come live from `GET /boss`).
- **Tap a metric for its meaning:** Level, HP and XP on the front, and the
  power level, loads, form, gravity, this week and records on the Scouter tab
  open a short explanation (`INFO` in `index.html`). The rest of the front
  still flips the card.
- **Moves are a surprise:** only unlocked moves show (tile, name, mark, the
  dashed line on the chart). Moves still to come have no tile, name or mark
  anywhere on the card; the Moves tab only says more are waiting. Don't
  mention them in chat either.
- **Move tiles:** tap to play the clip. The tile's picture is the clip's first
  frame, cropped the same way, so the clip starts without a jump (the move
  image is 2:3, the clip 9:16 with its sides cut off).

A push to `main` deploys it to Cloudflare (Workers Builds); by hand: `npx wrangler deploy`. Only the pages are published (`.assetsignore`). The old `rdecaste.github.io` address forwards here until GitHub Pages is switched off.
