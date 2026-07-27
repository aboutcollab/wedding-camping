# wedding-camping

One page, in **Portuguese, English and Dutch**, for the friends camping around Maeli & Marieke's wedding at Vakantiepark Callassande, Callantsoog, Wed 26 to Fri 28 August 2026.

Live: **https://aboutcollab.github.io/wedding-camping/**

Made by Helena (+31 6 8640 9404), a friend of the couple, to organise the camping trip. Sign-ups go through a Google Form; the list lives in a private Sheet.

## Three languages, one copy table

Portuguese, English and Dutch, switched from the PT/EN/NL pills in the top bar. Same pattern
as the hub and the coach page:

- **`FACTS`** holds every hard fact once (dates, the deadline, the prices, the form URL).
  Change `FACTS.deadline` and all three languages follow. **Never retype a fact in `COPY`.**
- **`COPY`** holds the words, three languages on adjacent lines, with `{placeholders}` filled
  from `FACTS`.
- Portuguese is the original and the fallback. The language is picked from `?lang=` first
  (that is how the hub hands a visitor over), then what they chose before, then the browser,
  then Portuguese.
- **The crew wall is language-aware.** `/crew-wall` writes badge *tokens*, not words: see
  the crew wall section below.
- The outbound link to the coach page carries the current language, so nobody switches to
  Dutch here and lands on an English coach page.

## Rules for this repo

- **No guest data in this repo, ever.** No phone numbers except Helena's own, no surnames, no email addresses, no contact lists. The camping crew wall shows **first names only**, and only of people who signed up themselves.
- **Links to the coach page go one way only.** This page links out to the coach sign-up for people who don't want to camp. The coach page must never link back here: that side is a broad audience of near-strangers, and this side is a small private group.
- **No dashes in the copy.** Helena's rule: em dashes read as AI. Use commas, colons, full stops or brackets. Number ranges use a plain hyphen (26-28, €60-80).
- **It's the "camping crew", never bare "crew".**
- Short-lived: this repo gets deleted after the wedding.

## The design system

The page uses the wedding's own look, taken from the invitation, so the camping page,
the coach page and the hub all read as one thing:

- **Fonts:** Quicksand (display, headings, UI) and Open Sans (body). Both are the
  invitation's actual fonts, free on Google Fonts.
- **Palette:** `--blush #F5E7F0` · `--pink #F81878` (the wordmark pink) ·
  `--pink-deep #C4105E` (text and links) · `--pink-soft #FBD4E4` · `--ink #3A3739`.
- **`assets/`** holds the wordmark and the four blossom corners, lifted from the
  invitation PDF. Byte-identical to the copies in the hub and coach repos. If you
  change one, change all three.
- **The dune photo stays.** `praia.webp` is the hero background, kept at Maeli's
  request. It sits under a plum veil so the type stays legible and the photo reads
  warm rather than fighting the pink.
- **The hero blossoms are masked on purpose.** The blossom PNGs carry an opaque,
  almost-white background around the branches. On a white page that is invisible.
  Over the dark photo it shows as a lighter rectangle, so the two hero blossoms get a
  radial mask that dissolves them before their straight edge. Do not remove it, and do
  not "fix" it by editing the PNGs: they are shared with two other repos.

## Files

| File | What |
|---|---|
| `index.html` | The whole page. Self-contained apart from Google Fonts. |
| `assets/` | Wordmark and blossom corners, shared with the hub and coach sites. |
| `praia.webp` | The dune photo behind the hero. |
| `og-source.html` | Source for `og.png`. Editing it changes nothing until you re-render. |
| `og.png` | 1200x630 share card, what WhatsApp shows when the link is pasted. |

## The share card is a picture

The dates and the price are baked into `og.png` and do **not** follow `index.html`.
When one changes, edit `og-source.html`, re-render, and bump `?v=` in both `og:image`
and `twitter:image` so WhatsApp re-fetches:

```bash
cd transport/camping-site
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new \
  --disable-gpu --hide-scrollbars --force-device-scale-factor=1 \
  --window-size=1200,630 --virtual-time-budget=6000 \
  --screenshot=og.png og-source.html
```

## Updating the camping crew wall

The block between `<!-- CREW-WALL:START -->` and `<!-- CREW-WALL:END -->` in `index.html` is regenerated from the `Camping RSVP` sheet. Don't hand-edit it. Run the `/crew-wall` command in the working repo (`transport/camping-site/`) and push.
