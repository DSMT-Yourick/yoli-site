# yoli.be

De website van Yoli: gewone HTML-bestanden, geen build nodig. Lettertypes (OFL) en afbeeldingen staan
in deze map; de site laadt niets van andere servers en gebruikt geen cookies.

| Pagina | Waarvoor |
|---|---|
| `index.html` | Startpagina voor kantoren |
| `privacy.html` | Privacyverklaring (ook voor de App Store) |
| `voorwaarden.html` | Algemene voorwaarden |
| `support.html` | Support en veelgestelde vragen (ook voor de App Store) |
| `bevestigd.html` | Waar de links in de mails van Yoli op uitkomen |

Gele markeringen (`class="invullen"`) zijn gegevens die nog ingevuld moeten worden: juridische naam,
ondernemingsnummer, adres, termijnen, prijs. Laat privacyverklaring en voorwaarden nalezen.

## Lokaal bekijken

```bash
python -m http.server 8090 -d site
```

## Online zetten (Cloudflare Pages)

1. Cloudflare → Workers & Pages → Create → Pages → Connect to Git → repository `yoli`.
2. Build command: leeg. Build output directory: `site`.
3. Custom domain: `yoli.be` en `www.yoli.be`. Cloudflare toont welk DNS-record er bij Versio moet
   komen; de records voor Microsoft 365 en Resend blijven staan.

Daarna:

- Supabase → Authentication → URL Configuration: **Site URL** `https://yoli.be/bevestigd.html`.
- `scripts/mails/bouw-mails.mjs`: `LOGO` naar `https://yoli.be/img/yoli-mail-logo.png`, mails opnieuw
  bouwen en in Supabase zetten.
- App Store Connect: privacy-URL `https://yoli.be/privacy.html`, support-URL `https://yoli.be/support.html`.
