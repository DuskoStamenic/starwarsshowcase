# Star Wars Showcase

A small, static showcase of the nine Skywalker-saga Star Wars films, powered by [TMDB](https://www.themoviedb.org/). Vanilla HTML, CSS, and JavaScript — no build step.

## Pages

- `index.html` — poster grid of all nine films (oldest → newest), with rating pills.
- `movie.html?id={tmdb_id}` — backdrop hero, poster, overview, director, top-billed cast, and embedded YouTube trailer.

## Deploy to GitHub Pages

1. Push this folder to a new GitHub repo.
2. In the repo settings → **Pages**, set source to the `main` branch, root (`/`).
3. Open `https://<your-username>.github.io/<repo-name>/`.

Pages serves over HTTPS, so all features (including trailer playback) work without further configuration.

## Configuration

The TMDB v3 API key is hardcoded at the top of each page's `<script>` block:

```js
const TMDB_API_KEY = "...";
```

This is fine for a personal showcase, but the key is visible to anyone who views source. If you fork this for public use, **rotate the key in your TMDB account settings** and replace it before deploying.

## Data sources

- `GET /collection/10` — the official Star Wars Collection (nine saga films).
- `GET /movie/{id}` — title, runtime, overview, genres, backdrop.
- `GET /movie/{id}/credits` — cast and crew (director picked from `crew[].job === "Director"`).
- `GET /movie/{id}/videos` — first official YouTube trailer; falls back to teaser if no trailer is returned.

## File layout

```
star-wars-showcase/
├── index.html       # grid
├── movie.html       # detail view
├── styles.css       # shared theme
└── README.md
```
