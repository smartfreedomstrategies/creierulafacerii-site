# Listă de verificare DNS — creierulafacerii.ro pe Cloudflare

⚠️ **Șablon, nu date live.** Spre deosebire de `razvanpopescu.com` (unde DNS-ul a fost citit din live), aici valorile NU sunt cunoscute. `creierulafacerii.ro` e domeniu nou, înregistrat recent. **Primul pas e să citești DNS-ul actual** la registrarul unde e domeniul și să completezi tabelele de mai jos înainte de „Continue to activation" în Cloudflare.

## De aflat întâi (completează tu)
- Registrar / unde e gestionat DNS-ul acum: **_______**
- Are domeniul email configurat? (ex. `contact@creierulafacerii.ro`) **DA / NU**
  - Dacă DA: pe ce serviciu? (Google Workspace / Zoho / cPanel / altul) **_______**
- Are deja un site live (înregistrare A spre un IP)? **DA / NU** → IP: **_______**

Dacă domeniul e complet gol (fără site, fără email), mutarea e simplă: adaugi domeniul în Cloudflare, muți nameserverele, legi Pages. Sari peste secțiunea „email" de mai jos.

---

## VITAL — dacă domeniul are email, astea trebuie să existe în Cloudflare

(Completează din DNS-ul actual. Dacă nu ai email pe domeniu încă, secțiunea nu se aplic_ decât după ce configurezi `contact@creierulafacerii.ro`.)

| Tip | Nume | Valoare | Proxy |
|---|---|---|---|
| MX | creierulafacerii.ro | `_______` (prioritatea `__`) | DNS only |
| TXT (SPF) | creierulafacerii.ro | `v=spf1 ... ~all` | DNS only |
| TXT (DMARC) | _dmarc | `v=DMARC1; p=none;` | DNS only |
| TXT (DKIM) | `*._domainkey` | cheia DKIM lungă | DNS only |

**ATENȚIE la DKIM:** scanarea Cloudflare ratează uneori cheia lungă `*._domainkey`. Verifică manual că apare. Dacă lipsește, emailul trimis poate ajunge la spam.

---

## SITE — după ce domeniul e în Cloudflare

NU edita A-ul manual. Mergi în Workers & Pages → **creierulafacerii-site** → tab **Custom domains** → **Set up a domain** → scrii `creierulafacerii.ro`. Cloudflare creează singur înregistrarea corectă spre proiectul Pages. Repetă pentru `www`.

| Nume | Țintă | Proxy |
|---|---|---|
| creierulafacerii.ro | proiect Pages `creierulafacerii-site` | Proxied (auto) |
| www | proiect Pages `creierulafacerii-site` | Proxied (auto) |

---

## Ordinea corectă a pașilor

1. **Citești DNS-ul actual** la registrar și completezi tabelele de mai sus.
2. **Adaugi domeniul în Cloudflare** (fluxul „Add a site" / Review DNS records).
3. **Verifici** în ecranul de review că nimic vital nu lipsește (MX/SPF/DMARC/DKIM, DACĂ ai email). Adaugi manual ce lipsește.
4. **Schimbi nameserverele** la registrar (cu cele 2 date de Cloudflare). Asta activează Cloudflare.
5. **Aștepți propagarea** (minute–ore).
6. **Workers & Pages → creierulafacerii-site → Custom domains → Set up a domain** → `creierulafacerii.ro` + `www`.
7. **Test:** deschizi site-ul; dacă ai email pe domeniu, îți trimiți un test.

## Plasă de siguranță
Dacă ceva nu merge, schimbi nameserverele înapoi la registrar și revii la starea de dinainte. Reversibil.
