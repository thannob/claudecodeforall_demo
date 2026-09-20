# AGENTS.md

This file provides guidance to AI coding agents when working with code in this repository.

## Project overview

Thai Food Recommender — a static, single-page site that suggests a random Thai dish and lets the visitor keep a personal list of favorites. Plain HTML/CSS/JS, no build step, no package manager, no backend.

## Running / testing

There is no build, lint, or test tooling in this repo. To check changes, open `index.html` directly in a browser, or serve the directory with any static file server (needed for the `image/` path and consistent `localStorage` behavior across reloads). There is no automated test suite — verify UI changes manually in a browser.

## Architecture

- `dishes.js` — the single source of truth for content: a `DISHES` array of objects (`name`, `emoji`, optional `image`, `category`, `desc`, `ingredients`). Both `index.html` and `detail.html` load this file via `<script src>` and read `DISHES` directly (no modules, no bundler).
- `index.html` — the main page: inline `<style>` and `<script>` implementing the random-pick card, the favorites list, and the full menu grid (with search/category filter). All dish rendering goes through `dishVisual(dish, size)`, which prefers `dish.image` and falls back to `dish.emoji`.
- `detail.html` — reads a `?dish=<name>` query param, looks up the matching entry in `DISHES`, and renders its `ingredients` list. Linked from both the random-pick card and each menu item via `detailUrl(dish)`.
- `image/` — dish photos referenced by the optional `image` field on a `DISHES` entry.
- Favorites are the only persisted state: stored in `localStorage` under key `thaiFoodFavorites` as an array of `{name, emoji}`, keyed by dish `name`. `index.html` and `detail.html` do not share state beyond this key — there is no other client-side storage or server.

## Domain language

`CONTEXT.md` is the authoritative glossary (Dish, Category, Today's Pick, Favorite, Menu) — read it before renaming concepts or adding new ones, and keep it in sync with any vocabulary changes. `task.md` tracks feature-level progress as a checklist.
