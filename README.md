# Table Aids — board game setup, teach and FAQ

A small static site: one landing page plus one page per game. Each game page combines
**Setup**, **How to play** and **FAQ** into sticky tabs, with a quick-reference tab for
mid-game lookups. Built for reading on an iPad at the table.

Unofficial and player-made throughout. Each game's official rulebook wins any disagreement.

## Games covered

| Game | Publisher | Players |
|---|---|---|
| Forest Shuffle | Lookout Games | 2–5 |
| World Wonders | Arcane Wonders | 1–5 |
| Heat: Pedal to the Metal | Days of Wonder | 1–6 |
| Nemesis: Lockdown | Awaken Realms | 1–5 |
| Skull | Lui-même · Space Cowboys | 3–6 |
| Magical Athlete | CMYK Games | 2–6 |
| Faraway | Catch Up Games | 2–6 |
| Sub Terra II: Inferno's Edge | Inside the Box (ITB) | 1–6 |
| Long Shot: The Dice Game | Perplext | 1–8 |
| King of Tokyo: Monster Box | IELLO | 2–6 |

## Files

Every file goes in the **root of the repository**. There are no folders and no build step —
each page is fully self-contained (HTML, CSS, JavaScript and artwork all inline), so it works
offline and can be opened directly from the Files app.

```
your-repo/
├── index.html               ← the landing page
├── forest-shuffle.html
├── world-wonders.html
├── heat.html
├── nemesis-lockdown.html
├── skull.html
├── magical-athlete.html
├── faraway.html
├── sub-terra-2.html
├── long-shot.html
├── king-of-tokyo.html
└── README.md
```

Do not rename the HTML files — the pages link to each other by these exact filenames.

## Hosting on GitHub Pages

1. Create a repository (public is fine; GitHub Pages needs a paid plan for private repos).
2. Drag all the `.html` files plus this README into the repo. GitHub's web uploader accepts
   a whole folder dragged at once and preserves it.
3. Go to **Settings → Pages**, set the source to your branch (usually `main`) and the folder
   to `/ (root)`, then save.
4. After a minute GitHub publishes at `https://yourname.github.io/reponame/`.

**Gotcha:** never share a *raw* GitHub file link — anything from clicking a file in the repo
browser, or a `raw.githubusercontent.com` URL. Those serve the file as plain text and you'll
see HTML source instead of the working page. Always use the GitHub Pages URL.

## On the iPad

Open the Pages URL in Safari, tap the Share icon, then **Add to Home Screen**. It launches
full screen with no browser chrome, which is what you want on a crowded table.

Everything works offline once loaded, so you can also AirDrop the files to the Files app
and tap `index.html` — the links between pages work identically.

## What's in each page

- **Setup** — a one-time bagging pass with tappable checkboxes, then parallel setup lanes so
  five people build the game at once. Player-count tables and a teardown routine.
- **How to play** — a teach script. Bold lines are written to be read aloud; italics are notes
  to the teacher. Includes a "defer these" list of what *not* to explain up front.
- **FAQ** — searchable and filterable by topic. Type two or three words and matching entries
  open automatically with the ruling highlighted.
- **Quick ref** — turn order, the handful of rules that break games, plus a per-game tool:
  a Winter tracker for Forest Shuffle, a Loan ledger for World Wonders, a corner-check
  calculator for Heat, an Event Phase caller for Nemesis: Lockdown, a bid-ceiling counter for Skull,
  a race tracker for Magical Athlete, a round counter for Faraway, a keys/artifact tracker for
  Sub Terra II, a finish-line counter for Long Shot, and a three-roll counter for King of Tokyo.

## Editing content later

Each page has its FAQ in a single `FAQ_DATA` array near the bottom of the file, in this shape:

```js
{ c: "Category name", items: [
  { q: "The question",
    r: "The one-line ruling shown in the coloured box",
    a: "<p>The longer explanation, as HTML.</p>" }
]}
```

Everything else — setup lanes, teach script, quick reference — is plain HTML in the body of
the page. The shared look comes from CSS variables at the top of each file; changing
`--accent` re-themes a whole page.

Both a dark and a light theme are built in. The toggle is in the top-right of every page and
the choice is remembered per device.

## Sources

Every ruling on these pages has been checked line by line against the publisher's own
rulebook:

- **Forest Shuffle** — Lookout Games English rulebook (rev. 260209) and the publisher FAQ
  on lookout-spiele.de.
- **World Wonders** — Arcane Wonders English rulebook (rev. 1).
- **Heat: Pedal to the Metal** — Days of Wonder base Rules booklet, plus the Advanced Play
  and Championship System booklet (Advanced Rules v1.1).
- **Nemesis: Lockdown** — Awaken Realms English rulebook and the official Lockdown FAQ
  (25 March 2022).
- **Skull** — Lui-même / Space Cowboys English rules (Skull & Roses).
- **Magical Athlete** — CMYK Games English rulebook (2025 edition, updated by Richard Garfield).
- **Faraway** — Catch Up Games English rulebook (designers Johannes Goupy & Corentin Lebrat).
- **Sub Terra II: Inferno's Edge** — Inside the Box (ITB) English rulebook and scenario sheets, plus the
  Typhaon Wakes expansion rules. Scenario-specific values (starting health, volcano-track length,
  guardian and key counts) are deliberately left to the rulebook rather than fixed on the page.
- **Long Shot: The Dice Game** — Perplext English rulebook (designer Chris Handy). Horse special powers and
  payout odds depend on which horse-card sets are in play, so they're described in general rather than listed.
- **King of Tokyo: Monster Box** — IELLO English rulebooks for the base game (2nd edition), the Power Up!
  expansion (Evolution cards) and the Halloween collector pack (Costume cards). Individual monster, Evolution
  and Costume card wording takes precedence over the summaries on the page.

Anything that could not be confirmed from an official source is flagged in place on the page
rather than stated as fact. There are currently two such flags, both on the Forest Shuffle
page and both about tree Saplings — the rulebook never states whether playing one costs
cards or whether it triggers the usual "flip a card into the Clearing" rule.
