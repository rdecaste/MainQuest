# MainQuest

The Goku (Main Quest) card, at https://mainquest.quest-engine.workers.dev
(Cloudflare, behind Roy's Cloudflare Access login), from `index.html`.

It reads its state from the Quest Engine (Cloudflare Worker,
`rdecaste/quest-engine`) at `GET /mainquest` (front) and `GET /hero` (back);
hero HP and heals come from `GET /boss`. How it works: `docs/quest-engine.md`
in rdecaste/quest-engine.

A push to `main` deploys it to Cloudflare (Workers Builds); by hand: `npx wrangler deploy`. Only the pages are published (`.assetsignore`). The old `rdecaste.github.io` address forwards here until GitHub Pages is switched off.
