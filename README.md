# A4A UTM Link Builder

A tiny, self-contained tool for building standardized UTM tracking links for HubSpot campaigns. One HTML file, no build step, no dependencies, no data sent anywhere (everything runs in the browser).

**Live tool:** https://katiebethbrown.github.io/a4a-utm-link-builder/

## What it does

- **Dependent dropdowns:** the source options change based on the medium you pick, so you can only choose valid combinations.
- **Auto-formatting:** every value is lowercased and hyphenated as you type, so `Booth_Signage` becomes `booth-signage` on its own.
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

Edit, commit, and the live site updates automatically. Keep every value lowercase with hyphens.

## Deploying with GitHub Pages

1. In the repo, go to **Settings > Pages**.
2. Under **Source**, choose **Deploy from a branch**.
3. Set the branch to **main** and the folder to **/ (root)**, then **Save**.
4. Wait a minute or two. The tool publishes at the live link above.

Because the file is named `index.html`, it serves directly at the repo root URL with no extra path.

## Files

- `index.html` — the link builder
- `utm-naming-standard.md` — the naming convention the tool enforces
