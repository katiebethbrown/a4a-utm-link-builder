# UTM Naming Standard

A shared convention for building tracking links, so campaign data stays clean and comparable in HubSpot. Follow this every time you tag a link.

## Why this exists

UTM values are case-sensitive and matched literally. `Event`, `event`, and `events` become three separate rows in reporting even though they mean the same thing. A fixed vocabulary and consistent formatting keep every link rolling up correctly.

## Global rules (apply to every value)

1. **Lowercase, always.** `linkedin`, never `LinkedIn`.
2. **Hyphens as the only separator.** `booth-signage`, never `booth_signage` or `booth signage`.
3. **No spaces or special characters.** Letters, numbers, and hyphens only.
4. **Spell things the exact same way every time.** Consistency within a field matters more than the specific wording.

The one exception is `utm_campaign` on campaigns created before October 16, 2026. Copy those exactly as HubSpot shows them, capitals included (see below).

## The five parameters

| Parameter | What it answers | How it is set |
|-----------|-----------------|---------------|
| `utm_campaign` | Which campaign or initiative | The HubSpot campaign's UTM value (`hs_utm`), copied exactly |
| `utm_medium` | The channel category | Fixed list below (pick exactly one) |
| `utm_source` | The specific origin within that channel | Per-medium vocab below |
| `utm_content` | The specific placement or variant | Descriptive pattern, lowercase-hyphen |
| `utm_term` | Paid keywords | Free text, paid ads only (usually auto-filled) |

The key idea: **medium is the bucket you compare against email, social, and paid.** Source is the specific origin inside that bucket. Campaign is the initiative. Keep each field doing its own job and never repeat the same value across two fields.

## utm_campaign (comes from HubSpot)

`utm_campaign` is the HubSpot campaign's UTM value (the `hs_utm` property on the campaign). HubSpot matches it literally, so copy it from HubSpot. Don't retype it or make up your own version.

- Campaigns the A4A Toolkit creates from October 16, 2026 get a lowercase `hs_utm`, for example `2026q4-new-york`. A UTM typed into the toolkit form is lowercased too.
- Older campaigns keep their mixed-case `hs_utm`, for example `2026Q4-New-York`, because live links and booth pages already use it. Copy it exactly.
- Find it on the campaign in HubSpot (Marketing > Campaigns). The toolkit also posts it in its hand-off comment on the Linear issue.
- For a new event, the lowercase value is also the Leads Event Name option. Use that exact value when you add a branch for the event to the Event Lead Capture - Form Processing workflow.

## utm_medium (fixed list, pick exactly one)

- `email`: any email you send
- `social`: organic social posts
- `paid-social`: paid social ads
- `cpc`: paid search
- `display`: banner / display ads
- `event`: in-person or offline events
- `partner`: co-marketing or partner referrals
- `referral`: another site linking to you
- `sms`: text messages
- `a4a-dashboard`: links in the A4A dashboard (promo banners, cards, in-product CTAs)

Guard this list tightly. Never invent a new medium on the fly. If something genuinely does not fit, add it to this standard deliberately so everyone uses the same word.

## utm_source (approved values per medium)

Source is a small approved set *per medium*, not one universal list. It names the specific origin within the channel.

- **email** → `newsletter`, `product-update`, `sales-outreach`, `lifecycle`
- **social** / **paid-social** → `linkedin`, `x`, `facebook`, `instagram`, `youtube`
- **cpc** → `google`, `bing`
- **display** → the ad network, e.g. `google-display`, `stackadapt`
- **event** → the placement or mechanism, e.g. `booth`, `booth-qr`, `session-slide`, `badge-scan`, `printed-flyer`
- **partner** → the partner's name, e.g. `wpengine`, `cloudways`
- **referral** → the referring domain, e.g. `techcrunch`
- **sms** → `broadcast`, `lifecycle`
- **a4a-dashboard** → the placement in the dashboard, e.g. `overview`, `marketplace-pressable`

Note for events: the event itself lives in `utm_campaign` (the HubSpot campaign), so do not repeat the event name in source. Use source for the specific placement instead.

## utm_content (pattern, not a fixed list)

Use it to tell apart multiple links that point to the same place. Lowercase, hyphens, consistent spelling.

Examples: `hero-cta`, `footer-cta`, `signage-a`, `qr-v1`, `founder-post`.

## utm_term (paid keywords only)

Free text, and usually populated automatically by the ad platform. Rarely set by hand.

## Worked examples

**In-person event (this one):**

```
https://agencies.automattic.com/signup?utm_campaign=2026-digital-summit-minneapolis&utm_source=booth-qr&utm_medium=event&utm_content=signage-a
```

Campaign = the event, medium = `event` (rolls up all events over time), source = `booth-qr` (the placement), content = `signage-a` (which sign).

**Email newsletter:**

```
https://agencies.automattic.com/signup?utm_campaign=2026-agency-onboarding&utm_source=newsletter&utm_medium=email&utm_content=header-cta
```

**Organic LinkedIn post:**

```
https://agencies.automattic.com/signup?utm_campaign=2026-agency-onboarding&utm_source=linkedin&utm_medium=social&utm_content=founder-post
```

**Partner referral (A4A partner program):**

```
https://automattic.com/for-agencies/?utm_campaign=a4a-partners&utm_source=evolvedigital&utm_medium=partner&utm_content=homepage-badge
```

Campaign = the shared, evergreen `a4a-partners` HubSpot campaign, not one per partner, medium = `partner`, source = the partner's own name, content = which placement on their site.

**A4A dashboard promo banner:**

```
https://agencies.automattic.com/signup?utm_campaign=2026q3-pressablehosting&utm_source=overview&utm_medium=a4a-dashboard
```

Medium = `a4a-dashboard` (rolls up every dashboard placement), source = where the banner sits. Only add `content` when one placement has two CTAs. Links that stay inside the dashboard don't need UTMs.

## Quick decision guide

- **What channel is this?** → that is your `medium` (from the fixed list).
- **Where specifically did it come from inside that channel?** → that is your `source`.
- **Which campaign is it part of?** → copy the `campaign` from HubSpot.
- **Do I have more than one link to the same page?** → use `content` to tell them apart.
