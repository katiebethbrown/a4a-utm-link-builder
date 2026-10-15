# A4A UTM Link Builder

A tiny, self-contained tool for building standardized UTM tracking links for HubSpot campaigns. One HTML file, no build step, no dependencies, no data sent anywhere (everything runs in the browser).

**Live tool:** https://a4a-utm-link-builder.view.fast/

## What it does

- **Dependent dropdowns:** the source options change based on the medium you pick, so you can only choose valid combinations.
- **Auto-formatting:** every value is lowercased and hyphenated as you type, so `Booth_Signage` becomes `booth-signage` on its own. The one exception is a campaign prefilled from a link (see below), which is kept exactly as given.
- **Live, copy-ready link:** the tracking URL builds in real time with a one-click copy button.
- **Campaign enforcement:** the campaign field is meant to match your HubSpot campaign name exactly, which is what makes attribution roll up correctly.

## Why it exists

UTM values are case-sensitive and matched literally, so `Event`, `event`, and `events` become three separate rows in reporting. This tool enforces one consistent format by construction. The full convention it follows is documented in [utm-naming-standard.md](./utm-naming-standard.md).

## How to use it

Open the live link above, fill in the fields, and copy the result. Or download `index.html` and open it locally in any browser. Nothing to install.

The generated link works as long as the destination page has the HubSpot tracking code installed and `utm_campaign` matches a HubSpot campaign name. HubSpot attributes traffic from UTM parameters whether or not the link was created inside HubSpot's own builder.

## Customizing the vocabulary

Open `index.html` and find the block near the top of the `<script>` marked:

```
/* EDIT YOUR VOCABULARY HERE */
```

Three plain lists control everything:

- `MEDIUMS` — the fixed list of channel categories
- `SOURCES_BY_MEDIUM` — the approved source values for each medium
- `KNOWN_CAMPAIGNS` — campaign names that autocomplete in the campaign field

Edit and commit, then republish `index.html` to Spacefast. The live site does not update on its own. Keep every value lowercase with hyphens.

## Prefilling from a link

You can open the tool with fields already filled in by adding query parameters to the URL:

https://a4a-utm-link-builder.view.fast/?campaign=2026Q4-WordCamp-Brasil

| Parameter | Alias | Fills | Rules |
|---|---|---|---|
| `campaign` | `utm_campaign` | Campaign | Kept exactly as given, case included, so it matches the HubSpot campaign's UTM value literally. |
| `medium` | `utm_medium` | Medium | Used only if it is in `MEDIUMS`. |
| `source` | `utm_source` | Source | Used only if it is listed in `SOURCES_BY_MEDIUM` for the selected medium. |
| `content` | `utm_content` | Content | Auto-formatted like typed input. |

Invalid medium or source values are ignored and the default is used. If you edit a prefilled campaign by typing, the field goes back to normal auto-formatting.

Example with everything: `https://a4a-utm-link-builder.view.fast/?campaign=2026Q4-WordCamp-Brasil&medium=event&source=booth-qr&content=signage-a`

## Hosting

The live copy is published to Spacefast at the live link above. Edits to `main` go live only after they are republished there. The old GitHub Pages copy (katiebethbrown.github.io/a4a-utm-link-builder) was turned off on 2026-10-15, so update any link that still points to it.

## Files

- `index.html` — the link builder
- `utm-naming-standard.md` — the naming convention the tool enforces
