# MainQuest

The Goku (Main Quest) card, served by GitHub Pages from `index.html`.

It reads its state from the Quest Engine (Cloudflare Worker, `rdecaste/quest-engine`) at `GET /mainquest` (front) and `GET /hero` (back); hero HP and heals come from `GET /boss`. `data.json` and `hero.json` here are the last files Make published (27 Sep 2026) and are no longer updated. `overlay-test.html` is a layout test page. How it works: Notion page "⚙️ Quest Engine (Cloudflare Worker)" under Quest log.
