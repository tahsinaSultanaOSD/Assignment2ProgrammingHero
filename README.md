# 🎬 MovieExplorer

A responsive Movie Explorer built with React, Tailwind CSS, and the [TVMaze API](https://www.tvmaze.com/api). Browse shows, search by title, and open a details modal for ratings, genres, and summaries.

## Features

- **Home page** — sticky navbar with brand, nav links, and a watchlist counter; a hero banner with a gradient headline and two CTAs; a "Tonight's Trending Spotlights" strip pulling the top-rated live titles.
- **Movie listing page** — a search bar that queries TVMaze's `search/shows` endpoint (debounced, live-updating grid), a genre filter chip row, a sort dropdown (rating / newest / A–Z), and a result-count pill. Falls back to `shows` (sorted by rating) when the search is empty.
- **Movie details modal** — backdrop image, title, rating, premiere date, genres, network, summary, and a watchlist toggle. Closable via the ✕ button, the Close button, the backdrop, or the Escape key.
- **Watchlist** — bookmark any title from its card or the modal; saved titles persist in `localStorage` and appear on a dedicated `/watchlist` page with a live counter badge in the navbar.
- Fully responsive: 2-column grid on mobile, up to 4 columns on desktop.

## Tech stack

- React 18 + React Router
- Vite
- Tailwind CSS
- lucide-react (icons)
- TVMaze API (no key required)

## Getting started

```bash
npm install
npm run dev
```

The app runs at `http://localhost:5173` by default.

### Build for production

```bash
npm run build
npm run preview
```

## Deploying

This is a static Vite build, so it deploys to any static host:

**Vercel**
1. Push this repo to GitHub.
2. Import it at [vercel.com/new](https://vercel.com/new).
3. Framework preset: Vite. No environment variables needed.

**Netlify**
1. Push this repo to GitHub.
2. New site from Git at [app.netlify.com](https://app.netlify.com).
3. Build command: `npm run build`, publish directory: `dist`.

**GitHub Pages**
1. `npm install -D gh-pages`
2. Add `"homepage": "https://<username>.github.io/<repo>"` to `package.json` and a `"deploy": "gh-pages -d dist"` script.
3. Run `npm run build && npm run deploy`.

## Project structure

```
src/
  components/
    Navbar.jsx
    Footer.jsx
    HeroBanner.jsx
    TrendingSpotlights.jsx
    MovieCard.jsx
    MovieModal.jsx
  context/
    WatchlistContext.jsx
  lib/
    api.js
  pages/
    HomePage.jsx
    MovieListingPage.jsx
    WatchlistPage.jsx
  App.jsx
  main.jsx
  index.css
```

## Notes on data

TVMaze's `search/shows` endpoint returns TV shows (not films) but is used here per the assignment's example. Ratings, images, and summaries are not available for every title — the UI falls back gracefully with "N/A" or "No image available" where data is missing.
