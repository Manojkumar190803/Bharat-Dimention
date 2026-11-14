# Functional Requirements Document

## Bharat Dimention

| Document detail | Value |
| --- | --- |
| Project | Bharat Dimention |
| Document | Functional requirements |
| Status | Describes the current static website |
| Source of truth | `index.html` and `style.css` |

## 1. Purpose

Bharat Dimention is a small, browser-based atlas of India. Visitors can choose a state or Union Territory on the map and read a profile shown beside it. The page is intended for casual geographic reference and exploration.

This document records what the current page does. It does not describe planned features such as map zooming, animated camera movement, or a slide-out drawer; those behaviors are not present in the current HTML and CSS.

## 2. Scope

### Included

- An India map with links for 28 states and 8 Union Territories.
- An overview showing the administrative-unit count and a population figure.
- A profile for each of the 36 map links.
- Profile information covering some or all of capital, formation date, area, languages, administration, demographics, geography, and state symbols.
- Fragment-based navigation: selecting a map area changes the URL and reveals the matching profile.
- CSS styling for the map, profile layout, hover and keyboard-focus states, and a narrow-screen layout.

### Not included

- Live or regularly refreshed data.
- User accounts, saved places, search, or filtering.
- GPS, route planning, map panning, or map zoom.
- External APIs or server-side data storage.
- A content-management interface.

## 3. Users and primary flow

The page is for visitors who want to browse the map and look up basic information about an Indian state or Union Territory.

1. The visitor opens the page and sees the India overview, map, and summary figures.
2. The visitor selects a map region by clicking it or reaching it with the keyboard and pressing Enter.
3. The URL fragment identifies the selected profile, which appears in the information column.
4. The visitor uses “Back to India overview” or the browser’s Back button to return to the overview or a previously selected profile.

## 4. Functional requirements

### Map and overview

- **FR-01:** The page shall display an India map with a separate link for each of the 28 states and 8 Union Territories.
- **FR-02:** Each map link shall have an accessible label identifying the associated territory.
- **FR-03:** The initial page state shall show an India overview with the displayed administrative-unit count and population figure.
- **FR-04:** Hovering over a map region or focusing its link by keyboard shall visibly distinguish that region.

### Territory profiles

- **FR-05:** Selecting a map link shall update the URL fragment and show the profile associated with that link.
- **FR-06:** The selected profile shall show its territory name and the details available for it in the page content. These may include its capital, formation date, area, languages, districts, demographic figures, geography, and state symbols.
- **FR-07:** A selected profile shall provide a “Back to India overview” link that returns the visitor to the page’s root fragment.
- **FR-08:** Returning to a previous fragment with the browser’s Back button shall restore the corresponding page state.

### Layout and operation

- **FR-09:** On wider screens, the map and information area shall appear in a two-column layout.
- **FR-10:** At viewport widths of 800 pixels or less, the layout shall switch to one column and keep the map within its available width.
- **FR-11:** The page shall work as a static website without requiring client-side JavaScript.

## 5. Non-functional requirements

- **NFR-01 — Browser delivery:** The page shall render using standard HTML and CSS in a modern browser.
- **NFR-02 — Responsive layout:** The map and profile content shall remain usable when the layout changes to one column on narrow screens.
- **NFR-03 — Keyboard access:** Map links and overview links shall be reachable and usable with a keyboard. Focused map regions shall receive a visible style.
- **NFR-04 — Data clarity:** The page shall not imply that its figures are live. Where the source is stated in the page, it should remain visible alongside the relevant figure.
- **NFR-05 — Maintainability:** Territory links and their profile targets shall use matching URL fragments so that content can be updated without introducing a scripting dependency.

## 6. Content and data notes

Profile details are written directly into `index.html`; they are not fetched from an external data source. The page identifies some figures as Census 2011 data and cites other sources for some entries. The content is therefore a snapshot, and sources and reference dates are not uniform across every profile.

Before using the figures for formal, official, or time-sensitive purposes, the content should be checked against current authoritative sources. This FRD makes no claim that every figure has been independently verified.

## 7. Acceptance checks

| ID | Check | Expected result |
| --- | --- | --- |
| AC-01 | Open the page without a URL fragment. | The map and India overview are visible. |
| AC-02 | Count the map links and profile targets. | There are 36 territory links, each pointing to a matching profile. |
| AC-03 | Select a territory on the map. | Its URL fragment is set and its profile appears. |
| AC-04 | Use the profile’s overview link. | The URL returns to the root fragment and the India overview appears. |
| AC-05 | Use Tab to reach a map link and press Enter. | The focused territory can be selected and the matching profile appears. |
| AC-06 | Resize the viewport to 800 pixels wide or less. | The layout becomes a single column and the map fits its container. |
| AC-07 | Open the page with JavaScript disabled. | The map, links, overview, and profiles remain usable. |

## 8. Project files

- `index.html` contains the page structure, embedded SVG map, territory links, overview, and profile content.
- `style.css` controls colors, layout, map styling, focus and hover states, and the responsive breakpoint.
- `Assets/favicon.png` is the page favicon.
- `Assets/india.svg` is an additional map asset in the project; the current page contains its map inline in `index.html`.
