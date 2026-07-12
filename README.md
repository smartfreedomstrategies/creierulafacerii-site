# CreierulAfacerii.ro — site static

Pagina-erou a Creierului Afacerii. Un singur fișier, `index.html`, autonom. Font Satoshi din Fontshare (CDN). Fără build, fără dependențe locale, fără panou. Plain file.

Deploy pe **Cloudflare Pages**, din Git, exact ca `razvanpopescu-site`. Orice push în `main` → Cloudflare republică automat.

## Ce e în pachet
- `index.html` — pagina întreagă (HTML + CSS + JS inline, iconițe SVG inline)
- `DEPLOY-cloudflare-pages.md` — pașii de deploy pe Cloudflare Pages
- `DNS-checklist-cloudflare.md` — șablon de verificare DNS înainte de a lega domeniul
- `README.md` — fișierul ăsta
- `.gitignore`

## Sursa de adevăr
Fișierul `index.html` de aici e **versiunea live** a paginii. Originea de design e `the-business-brain.html` din repo-ul de dezvoltare `creierul-afacerii` (umbrelă), dar de acum editările pentru site se fac AICI și se dau push. Cloudflare republică singur.

---

## Pasul 1 — GitHub (gata)

Repo-ul `creierulafacerii-site` există deja pe `smartfreedomstrategies`, cu fișierele în `main`. Nimic de făcut aici.

*(De editat de acum: schimbi textul în `index.html`, `git add`, `git commit`, `git push`. Cloudflare republică singur.)*

---

## Pasul 2 — Cloudflare Pages

1. Intri pe dash.cloudflare.com → **Workers & Pages → Create → Pages → Connect to Git**.
2. Autorizezi GitHub, alegi repo-ul `creierulafacerii-site`.
3. Setări build:
   - **Framework preset:** None
   - **Build command:** lasă gol
   - **Build output directory:** `/` (rădăcina)
4. **Save and Deploy.** În ~30 de secunde ai un link `creierulafacerii-site.pages.dev` live.

Orice push nou în GitHub → Cloudflare republică automat.

---

## Pasul 3 — Domeniul (creierulafacerii.ro)

1. În proiectul Pages → **Custom domains → Set up a domain** → scrii `creierulafacerii.ro`.
2. Cloudflare îți spune ce record DNS să pui. Detaliile complete + plasa de siguranță pentru email sunt în `DEPLOY-cloudflare-pages.md` și `DNS-checklist-cloudflare.md`.
3. HTTPS se activează singur.

---

## De pus tot pe domeniul ăsta (pași următori, în afara scopului „doar index" de acum)

Domeniul `creierulafacerii.ro` e și infrastructura ecosistemului de plugin-uri. Când ajungi acolo, tot aici (în repo) vor sta:
- **`updates.json`** — fișierul de descoperire a update-urilor, servit la `creierulafacerii.ro/updates.json`. Se generează cu `genereaza-updates-json.sh` din repo-ul umbrelă (niciodată de mână) și se copiază aici la fiecare release.
- **`_redirects`** — redirect-urile stabile Cloudflare Pages: `/template` → linkul Notion al Template-ului v2.0.0 (și viitorul `/instalare`). Format Cloudflare Pages: o linie `/template  https://…notion…  302`.

Astea deblochează pașii rămași din `versiuni.md` (pointarea redirect-urilor + endpoint-ul de update). Nu-s incluse acum, intenționat — pagina e „doar index" până creștem site-ul.

## Pre-lansare
CTA-urile din `index.html` pointează la `contact@creierulafacerii.ro`. Cutia poștală trebuie să existe înainte de lansare, altfel emailul de instalare sare în gol.
