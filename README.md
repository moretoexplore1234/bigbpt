# Big B PT website

Live preview: https://moretoexplore1234.github.io/bigbpt/
Custom domain (after repointing): https://bigbpt.com

Single-page site: about, rates, photos, availability calendar, contact.
No build step — edit `index.html`, commit, and GitHub Pages updates in a minute or two.

## Updating availability (block off days)

In `index.html`, find the `blockedDates` list near the bottom of the file and add
dates as `'YYYY-MM-DD'`:

```js
var blockedDates = ['2026-11-15', '2026-11-20'];
```

Days listed there show crossed out on the calendar. Everything else shows open.
Open days link to WhatsApp so visitors message to confirm — this is an
availability display, not a reservation system, because the schedule shifts often.

## Adding photos

Replace the four `.photo-slot` placeholder boxes in the Photos section with
`<img>` tags pointing at image files added to this repo, e.g.:

```html
<img src="photo-1.jpg" alt="Training session" style="width:100%;border-radius:10px;">
```

## Pointing bigbpt.com at this site (domain repoint)

Do the GitHub side first, then the GoDaddy side.

### 1. GitHub side (repo owner)

1. In this repo: Settings → Pages.
2. Under "Custom domain", type `bigbpt.com` and Save. (This adds a `CNAME`
   file to the repo.)
3. Wait for the DNS check to pass, then turn on "Enforce HTTPS".

### 2. GoDaddy side (domain owner, bigbpt.com)

1. GoDaddy → My Products → Domains → bigbpt.com → DNS (or "Manage DNS").
   If the website-builder view doesn't show DNS settings, use the full
   GoDaddy account's domain DNS manager.
2. Delete the existing A records that point the site at GoDaddy's Website
   Builder, and any URL forwarding on the bare domain.
3. Add these four A records (Host `@`, one per line):

   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```
4. Optional, for www: add a CNAME record, Host `www`, Points to
   `moretoexplore1234.github.io`.
5. Save. DNS usually updates within a few hours, sometimes up to 48 hours.

Once DNS propagates, bigbpt.com serves this site, and the old GoDaddy-built
site stops serving (that is the point of the move). The preview URL keeps
working and redirects to bigbpt.com after the custom domain is set.

Note: the GoDaddy Website Builder copy of the site is separate — repointing
DNS does not delete it, it just stops the domain from reaching it.
