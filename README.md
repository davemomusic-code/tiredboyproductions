# Tired Boy Productions website

Live at **https://tiredboy.pro** (once the steps below are done).

A single self-contained page: all styles, photos, logos and video stills are built into `index.html`. No build step, no installs. GitHub Pages serves it as is.

## Files

| File | What it does |
| --- | --- |
| `index.html` | The whole website |
| `CNAME` | Tells GitHub Pages to serve the site at tiredboy.pro |
| `robots.txt` | Lets search engines crawl the site and points them to the sitemap |
| `sitemap.xml` | Lists the site for Google |
| `favicon.svg` | Browser tab icon (the tired boy mark) |
| `og-image.jpg` | Preview image when the link is shared on Instagram, iMessage, LinkedIn, etc. |

## 1. Put it on GitHub Pages

1. Create a new repository on GitHub (for example `tired-boy-productions`).
2. Upload every file in this folder to the root of the repository.
3. In the repository: **Settings → Pages**. Under "Build and deployment", choose **Deploy from a branch**, branch **main**, folder **/ (root)**, then **Save**.
4. Still on that page, the custom domain should already read `tiredboy.pro` (from the `CNAME` file). Tick **Enforce HTTPS** once it becomes available.

## 2. Point tiredboy.pro at GitHub

At your DNS provider for tiredboy.pro, add:

| Type | Name | Value |
| --- | --- | --- |
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | YOUR-GITHUB-USERNAME.github.io |

If you use Cloudflare for DNS, set these records to **DNS only** (grey cloud) so GitHub can issue the HTTPS certificate. DNS changes can take up to a day to settle.

## 3. Make hello@tiredboy.pro forward to your inbox

Using Cloudflare Email Routing (free):

1. Cloudflare dashboard → tiredboy.pro → **Email → Email Routing** → enable it.
2. Add your personal inbox as a **destination address** and click the confirmation link Cloudflare emails you.
3. **Create address**: custom address `hello`, action **Send to** your personal inbox.
4. Let Cloudflare add the MX and TXT records it suggests.

Your personal address is only stored in your Cloudflare account. It never appears on the website.

## 4. Turn on the contact form

The form sends through Web3Forms, so no server is needed.

1. Go to https://web3forms.com and create an access key **using your personal inbox** (that is where inquiries will land).
2. Open `index.html` and search for `YOUR_WEB3FORMS_ACCESS_KEY`.
3. Replace it with your key and commit the change.

The access key is safe to have in public code: it only lets people send messages *to* you. Your email address is stored with Web3Forms, not in the site.

Until the key is added, the form politely tells visitors it isn't connected yet and gives them hello@tiredboy.pro instead, so no inquiry is silently lost.

Each inquiry arrives with the subject "New inquiry: Name (Company)". Hit **Reply** and it goes straight to the person who filled in the form.

## Updating the site later

All content lives in `index.html`. For bigger changes (new videos, new photos), ask Claude to update the page and re-upload `index.html`.
