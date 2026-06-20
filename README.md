# 0rt1

**A modular browser tool built for tech-savvy call center supervisors.**

![Version](https://img.shields.io/badge/version-0.1.0-3D8A70?style=flat-square)
![Status](https://img.shields.io/badge/status-early%20WIP-3D8A70?style=flat-square)
![Stack](https://img.shields.io/badge/stack-vanilla%20HTML%2FCSS%2FJS-3D8A70?style=flat-square)

## What It Is

0rt1 is a single-file, no-dependency web app built to take the manual math out of day-to-day call center / medical billing work. It's structured as a small "app shell" — header, sidebar of tools, main panel — so new tools can be dropped in without touching the rest of the app. Right now there's one tool live: the **CPT Calculator**.

## Current Tool: CPT Calculator

Given a patient name and a CPT code, it tells you how many visits/services are still allowed for the rest of the calendar year, and what that breaks down to per month.

- Looks up the code against a reference table covering:
  - Community Health Integration (CHI) — `G0019`, `G0022`
  - Principal Illness Navigation (PIN) — `G0023`, `G0024`
  - Office Visits — `99203`, `99204`
  - Chronic Care Management — `99487`, `99489`, `99490`
  - Psychiatric Collaborative Care — `99493`
- Reads the device clock to figure out how many months are left in the current year and what the year-end date is — no manual date entry, and it rolls over to the next year automatically.
- Calculates **Total Allowed = remaining months × per-month frequency** for the matched code.
- Flags codes that aren't in the table instead of failing silently.

## Tech Stack

No framework, no build step, no `node_modules`. The whole app is one `index.html` file:

- Vanilla HTML / CSS / JS
- [IBM Plex Mono](https://fonts.google.com/specimen/IBM+Plex+Mono) for the logo and numerals, [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk) for everything else — loaded via Google Fonts
- Styling driven by CSS custom properties (design tokens) at the top of the file, so the whole theme can be reskinned by editing one block of variables

## Design

Dark UI built around a deep forest-green accent (`#1D4238`). The wordmark substitutes letters for digits — `0` for the O, `1` for the I — with the `1` kept white to break up the two-tone logo. It's meant to feel like an internal ops tool rather than a consumer product: quiet, fast, and built for someone who's going to be looking at it for an 8-hour shift.

## Running It Locally

There's nothing to install.

```bash
git clone https://github.com/Euripidec/0rt1.git
cd 0rt1
open index.html   # or just double-click it
```

## Status & Roadmap

This is an early build (`v0.1.0`), and a few things are intentionally unfinished:

- 🏗️ **Over all functionality still needs work.** End eligibility date should be a field ect.
- ⚠️ **Per-month frequency values are placeholders.** Every code in the lookup table is currently hardcoded to `1` visit/month — these need to be swapped for real figures from the reference billing guide.
- 🚧 **History panel is UI-only.** The sidebar has a History section, but it isn't wired up to actually save past calculations yet.
- 🔭 **More tools planned.** The sidebar is built to hold more than one tool — CPT Calculator is just the first.


## Author

Built by **Euri** ([Archon](https://euripidecarpio.neocities.org)) @ DaemonSoftworks.
