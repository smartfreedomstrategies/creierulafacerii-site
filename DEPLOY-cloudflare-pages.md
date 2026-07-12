# Deploy pe Cloudflare Pages — creierulafacerii.ro

Site static, un singur `index.html`. Deploy din Git, ca la `razvanpopescu.com`. Orice push în `main` → Cloudflare republică singur.

**Înainte de orice:** verifică unde e înregistrat `creierulafacerii.ro` și dacă are deja DNS/email configurat. Dacă e domeniu nou, fără site și fără email încă, mutarea e curată (muți nameserverele pe Cloudflare și gata). Dacă are deja email (ex. `contact@creierulafacerii.ro`), NU strica înregistrările MX/SPF/DKIM/DMARC — vezi `DNS-checklist-cloudflare.md`.

---

## Pasul 1 — Conectează repo-ul la Cloudflare Pages

1. Cloudflare → **Workers & Pages → Create → Pages → Connect to Git**
2. Autorizezi GitHub (dacă cere) și alegi repo-ul **creierulafacerii-site**
3. Setări build:
   - Framework preset: **None**
   - Build command: **(gol)**
   - Build output directory: **/**
4. **Save and Deploy**
5. În ~30 sec ai un link `https://creierulafacerii-site.pages.dev`
6. **Testează acolo întâi.** Deschide-l și verifică:
   - diacriticele („Vânzări", „Țesut de memorie", „ține minte")
   - contoarele din hero (7, 25, 4) se animează la scroll; „7:00" e fix
   - toate secțiunile apar la scroll (problema, temelia, nucleul întunecat, module, FAQ, final)
   - comutatorul de limbă „EN" duce la businessbrainpro.com
   - butoanele „Instalează Creierul" deschid un email către `contact@creierulafacerii.ro`
   - favicon-ul în tab
   Dacă arată bine → mergi mai departe.

---

## Pasul 2 — Leagă domeniul (Custom domain)

1. În proiectul Pages → tab **Custom domains** → **Set up a domain**
2. Scrie `creierulafacerii.ro` → Continue
3. Cloudflare îți arată **exact** ce înregistrare DNS să adaugi. De obicei:
   - dacă domeniul e DEJA pe Cloudflare (nameservere Cloudflare): se face cu un click, Cloudflare creează singur înregistrarea corectă spre proiectul Pages
   - dacă NU e pe Cloudflare: îți dă un CNAME (spre `creierulafacerii-site.pages.dev`) sau un A (spre un IP), pe care le adaugi la registrarul/DNS-ul actual
4. Repetă pentru `www.creierulafacerii.ro` dacă vrei să meargă și cu www (un CNAME spre `creierulafacerii-site.pages.dev`).
5. HTTPS se activează singur.

---

## Pasul 3 — Redirect-urile ecosistemului (când ajungi acolo)

Domeniul ăsta servește și infrastructura de plugin-uri. Adaugă un fișier `_redirects` în rădăcina repo-ului (format Cloudflare Pages, o regulă pe linie):

```
/template   https://<linkul-Notion-al-Template-v2.0.0>   302
```

Și copiază `updates.json` (generat cu `genereaza-updates-json.sh` din repo-ul umbrelă) în rădăcină, ca să fie servit la `creierulafacerii.ro/updates.json`. Vezi `README.md` → „De pus tot pe domeniul ăsta".

---

## Ce să NU atingi dacă domeniul are deja email

Dacă `contact@creierulafacerii.ro` (sau orice adresă pe domeniu) e deja funcțională, lasă neatinse:
- **MX** (primirea emailului)
- **TXT**: SPF (`v=spf1...`), DKIM (`*._domainkey`), DMARC (`_dmarc`)
- subdomeniile de mail/webmail/autoconfig/autodiscover

Detaliile în `DNS-checklist-cloudflare.md`.

---

## Verificare finală

- Propagarea DNS: de la minute la câteva ore.
- Verifică `creierulafacerii.ro` în browser (hard refresh: Cmd+Shift+R).
- Dacă ai email pe domeniu, trimite-ți un test ca să confirmi că merge.

**Plasă de siguranță:** testezi întâi pe `*.pages.dev`. Legi domeniul doar după ce ești mulțumit. Dacă ceva nu merge, poți da înapoi înregistrarea DNS la valoarea de dinainte. Reversibil.
