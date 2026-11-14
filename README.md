# Bharat Dimention

Bharat Dimention is a static, interactive atlas of India. Choose a state or Union Territory on the map to open a short profile alongside it. The page uses HTML and CSS only; it does not need JavaScript, a server, or a package install.

## What’s on the page

- An SVG map with links for 28 states and 8 Union Territories.
- An India overview with summary figures.
- A profile for each territory, with details such as its capital, area, languages, demographics, geography, and state symbols.
- URL-fragment navigation, so a selected profile can be bookmarked and browser Back works.
- Hover and keyboard-focus styles for map regions.
- A one-column layout on screens 800 pixels wide or narrower.

## Open the page

You can open `index.html` directly in a modern browser. If you prefer to serve it locally, run a simple static web server from this folder, then open the local address it prints. No build step or dependency installation is required.

The main page depends on `style.css` and `Assets/favicon.png`. The map is embedded in `index.html`; `Assets/india.svg` is also included in the repository.

## Project files

```text
BharatDimention/
├── index.html       # Page content, inline SVG map, links, and territory profiles
├── style.css        # Layout, colors, map states, and responsive styles
├── FRD.md           # Functional requirements for the current page
└── Assets/
    ├── favicon.png
    └── india.svg
```

## Data note

Profile information is stored in the HTML rather than loaded from a live source. Some figures are labelled as Census 2011 data, and the page cites other sources for some entries. Sources and dates may vary by profile, so check the figures against current authoritative references before relying on them for formal or time-sensitive work.
