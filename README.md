# wedding-camping

One page, in Portuguese, for the friends camping around Maeli & Marieke's wedding at Vakantiepark Callassande, Callantsoog, Wed 26 to Fri 28 August 2026.

Live: **https://aboutcollab.github.io/wedding-camping/**

Made by Helena (+31 6 8640 9404), a friend of the couple, to organise the camping trip. Sign-ups go through a Google Form; the list lives in a private Sheet.

## Rules for this repo

- **No guest data in this repo, ever.** No phone numbers except Helena's own, no surnames, no email addresses, no contact lists. The camping crew wall shows **first names only**, and only of people who signed up themselves.
- **Links to the coach page go one way only.** This page links out to the coach sign-up for people who don't want to camp. The coach page must never link back here: that side is a broad audience of near-strangers, and this side is a small private group.
- **No dashes in the copy.** Helena's rule: em dashes read as AI. Use commas, colons, full stops or brackets. Number ranges use a plain hyphen (26-28, €60-80).
- **It's the "camping crew", never bare "crew".**
- Short-lived: this repo gets deleted after the wedding.

## Files

| File | What |
|---|---|
| `index.html` | The whole page. Self-contained apart from Google Fonts. |
| `og.png` | 1200x630 share card, what WhatsApp shows when the link is pasted. |

## Updating the camping crew wall

The block between `<!-- CREW-WALL:START -->` and `<!-- CREW-WALL:END -->` in `index.html` is regenerated from the `Camping RSVP` sheet. Don't hand-edit it. Run the `/crew-wall` command in the working repo (`transport/camping-site/`) and push.
