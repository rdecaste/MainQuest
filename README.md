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
  short-term load chart, gravity, this week, the Ki box, records), Moves,
  Forms, Log, Lore.
- **📡 Transmissions** (Scouter tab, since 8 Oct 2026): the reading on top is
  often a message from Goku's allies about today's data. The cast follows the
  story: each character speaks only once Goku's level reaches the part of the
  story they join (`from` in `CAST`), with "First contact" the first time
  (recovery,
  form, load ratio, ki, this week, days off, bad habits, the hour). Gold =
  rare, purple = the scouter overloads (very rare). Tap the reading to rescan;
  three rescans in a minute and it overheats for 45 s. A first catch shows NEW;
  caught lines are counted in the browser. Only allies talk, and never about a
  form, move or boss still to come (`transmissions()` in `index.html`).
- **Load chart rows** (Scouter tab, since 5 Oct 2026): under the form strip,
  the load ratio (short ÷ long, `power.load.ratio`, with the optimal band
  0.8–1.3 in green and 1.5+ in red) and a recovery strip, one block per morning
  (`power.load.recovery`: Good to go, Go steady, Take it easy). Drag to read a
  day across all rows; tap a row title for its meaning.
- **🔥 Ki box** (Scouter tab, since 4 Oct 2026): the ki charge from
  `power.ki` in `GET /mainquest` (quest-engine `src/ki.js`). The charge now as
  5 bars with today's healing cap, and the last 28 days as a graph: one bar
  per day at its charge (peak glows, an empty charge is blue) and a blue ball
  per Fap tap. Drag on the graph to read a day; tap the header for the rules.
- **Log:** the last 14 days, one row each (Success, workouts, HP, XP). Tap a
  day to see what happened: every habit, heal and hit with its time and
  effect (`events` per day in `GET /hero`; today's taps come live from `GET /boss`).
- **Tap a metric for its meaning:** Level, HP and XP on the front, and the
  power level, loads, form, load ratio, recovery, gravity, this week, the ki charge and records on the Scouter tab
  open a short explanation (`INFO` in `index.html`). The rest of the front
  still flips the card.
- **Moves are a surprise:** only unlocked moves show (tile, name, mark, the
  dashed line on the chart). Moves still to come have no tile, name or mark
  anywhere on the card; the Moves tab only says more are waiting. Don't
  mention them in chat either.
- **Move tiles:** tap to play the clip. A dormant move doesn't play: it stays
  a still, greyed-out picture. The tile's picture is the clip's first
  frame, cropped the same way, so the clip starts without a jump (the move
  image is 2:3, the clip 9:16 with its sides cut off).

A push to `main` deploys it to Cloudflare (Workers Builds); by hand: `npx wrangler deploy`. Only the pages are published (`.assetsignore`). The old `rdecaste.github.io` address forwards here until GitHub Pages is switched off.
