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
└── README.md
```

Do not rename the HTML files — the pages link to each other by these exact filenames.

## Hosting on GitHub Pages

1. Create a repository (public is fine; GitHub Pages needs a paid plan for private repos).
2. Drag all five `.html` files plus this README into the repo. GitHub's web uploader accepts
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

Everything works offline once loaded, so you can also AirDrop the five files to the Files app
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
  calculator for Heat, and an Event Phase caller for Nemesis: Lockdown.

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

- **Forest Shuffle** — Lookout Games English rulebook and publisher FAQ.
- **World Wonders** — Arcane Wonders English rulebook.
- **Heat: Pedal to the Metal** — Days of Wonder base Rules booklet, plus the Advanced Play
  and Championship System booklet.
- **Nemesis: Lockdown** — Awaken Realms English rulebook and the official Lockdown FAQ
  (25 March 2022).

Anything that could not be confirmed from an official source is flagged in place on the page
rather than stated as fact.
