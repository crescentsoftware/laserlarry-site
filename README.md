# Laser Larry website

One static page (`index.html`) with everything Apple asks for:

- Marketing URL: `https://<site>/`
- Support URL: `https://<site>/#support` (contact email + FAQ)
- Privacy Policy URL: `https://<site>/#privacy`

No build step, no cookies, no analytics, no third-party requests (fonts are self-hosted: Aldo the Apache, the display font from the game, and Nunito, OFL licensed, for body text).

## Before launch, fill in the orange placeholders

Search `index.html` for `TODO(Gregory)` and `class="todo"`:

1. Support email is info@laserlarrygame.com: set up forwarding for it before launch.
2. Privacy policy effective date is November 26, 2026; update it whenever the policy changes.
3. App Store link on the download button, and swap in Apple's official badge.
4. Smart App Banner app id (commented out in `<head>`).
5. Confirm the privacy policy matches what 2.0 ships: Unity Ads/Analytics child-directed settings (#92), Sentry/Unity retention periods, and that it matches the App Store privacy labels.
6. Optional: add real gameplay screenshots or the trailer.

## Deploy on GitHub Pages

1. Put these files at the root of the repo (keep `.nojekyll` and `CNAME`).
2. Repo Settings > Pages > Source: Deploy from a branch > `main` / root.

## Custom domain: laserlarrygame.com

`CNAME` already contains `laserlarrygame.com`.

1. Register `laserlarrygame.com` if you haven't (any registrar; Cloudflare and Porkbun sell at cost, about US$10-12/year).
2. Verify the domain first, so nobody else can claim it on GitHub: GitHub org `crescentsoftware` > Settings > Pages > Add a domain. GitHub shows a TXT record (`_github-pages-challenge-crescentsoftware.laserlarrygame.com`); add it at your registrar and click Verify.
3. Add these DNS records at your registrar:

   | Type | Name | Value |
   | --- | --- | --- |
   | A | `@` | 185.199.108.153 |
   | A | `@` | 185.199.109.153 |
   | A | `@` | 185.199.110.153 |
   | A | `@` | 185.199.111.153 |
   | AAAA | `@` | 2606:50c0:8000::153 |
   | AAAA | `@` | 2606:50c0:8001::153 |
   | AAAA | `@` | 2606:50c0:8002::153 |
   | AAAA | `@` | 2606:50c0:8003::153 |
   | CNAME | `www` | `crescentsoftware.github.io` |

   If you use Cloudflare DNS, set these records to "DNS only" (grey cloud) so GitHub can issue the certificate.
4. Repo Settings > Pages > Custom domain: `laserlarrygame.com` > Save. Wait for the DNS check to pass (minutes to a few hours), then tick **Enforce HTTPS**. `www.laserlarrygame.com` then redirects to the bare domain.
5. Email: set up forwarding for `info@laserlarrygame.com` (the support address on the site) to your inbox. Most registrars include free email forwarding, as do Cloudflare Email Routing and ImprovMX.

Apple URLs once live:

- Marketing URL: `https://laserlarrygame.com/`
- Support URL: `https://laserlarrygame.com/#support`
- Privacy Policy URL: `https://laserlarrygame.com/#privacy`

Images come from the Unity project (`Assets/Media/icons`, `TexturesV2.1/UI`, `docs/Larry Assets - 01-07-18`). No Tardis or Death Star art is used.
