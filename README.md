# mm-doctor-widget

JotForm custom widget that calls `mm-doctor-api` and renders an "Is this your doctor?" dropdown with photo + NPI for each candidate.

## How it works
1. JotForm calls the widget's `change` event whenever any field on the page changes.
2. We read the doctor first/last name, phone, clinic, and state fields by their JotForm question names.
3. We debounce 400ms, POST to `mm-doctor-api` `/api/lookup-candidates`, and render candidates.
4. When the user picks one, the widget pushes a JSON blob `{npi, displayName, clinic, address, phone}` into its own hidden field — which JotForm routes to the Monday.com DTC Intake Board (`18392794310`).

## Widget settings (configurable in the JotForm builder)
- `apiBase` — default `https://mm-doctor-api.up.railway.app`
- `firstNameField` / `lastNameField` / `phoneField` / `clinicField` / `stateField` — the JotForm question **names** (not IDs) for those fields

## Hosting
Hosted as static HTML on GitHub Pages (or Railway static). JotForm requires HTTPS.

## Register with JotForm
JotForm's "Build your own widget" → add iframe URL pointing to the `gh-pages` deployment of this repo → ship.
