# Relay Protocol

Relay Protocol is an open protocol project exploring a user-controlled digital presence that exists independently of the applications used to interact with it.

The repository contains the protocol design notes, editorial and requirements-engineering programme, and the source for the public website at `relay-protocol.org`.

## Project status

Relay is under active development. The v0.1 specification is not yet stable, and design decisions, terminology, and protocol structures may change before the first specification release.

## Repository structure

- `design-notes/` — conceptual protocol models
- `rem/` — requirement extraction matrices and reviews
- `editorial/` — editorial audits and canonical requirements catalogues
- `src/`, `public/` — Astro source for the public Relay Protocol website

## Website

The website is built with Astro as a static site.

```bash
npm install
npm run dev
```

Production build:

```bash
npm run build
```

The generated static site is written to `dist/`.
