# Specificația paginii de vânzare Creierul Afacerii

Sursa de adevăr pentru copy-ul și structura paginilor de pe creierulafacerii.ro. Portată din pasul de copy al liniei engleze (The Founders' Brain, 15.07.2026). Orice modificare de copy pe pagini pornește de aici.

## Cumpărătorul

Fondatorul-expert solo. Consultant, coach, expert care își vinde priceperea; firma e el, iar el e memoria firmei. Copy-ul îi vorbește LUI. Fondatorul cu echipă mică se regăsește singur; invers nu funcționează.

## Traficul

Cald și călduț: recomandări, conținut propriu, oameni care au vorbit deja cu Razvan. Nimeni rece nu nimerește pagina în faza asta. Consecință practică: oferta, cei trei pași și filtrul de potrivire urcă în pagină; educația (temelia, modulele) coboară. Pagina completă e o suprafață de credibilitate, nu o mașină de convertit trafic rece.

## Promisiunea

Nu mai ești tu memoria afacerii.

## Mecanismul, numit: Memorie Proprie

Memoria structurată care stă în Notion-ul clientului, nu pe platforma noastră. Pleci mâine și rămâne a ta.

Testul concurenței: „un AI care ține minte afacerea ta" poate fi spus de oricine peste un an; „iar memoria stă la tine" nu poate fi spus de aproape nimeni. Raportul de la 7:00 rămâne artefactul zilnic vizibil; Memorie Proprie e motivul pentru care promisiunea se ține.

## Regula lui Unu

- O idee: afacerea ta are în sfârșit o memorie care nu ești tu.
- O emoție: răsuflarea ușurată, cineva competent a preluat.
- O acțiune: un singur email.

## Titlul

Blocat: „Nu mai fi memoria afacerii tale."

Variante ținute pentru A/B când există trafic:

- Varianta B: „Afacerea ta are, în sfârșit, o memorie care nu ești tu."
- Varianta D (fosta, martor): „Afacerea ta, cu un creier al ei."

## Ordinea secțiunilor (pagina completă)

`hero → problem → isnt → core → start → gate → day → foundation → modules → trust → founder → faq → finale`

Întrebările de cumpărare (cum funcționează, cum începem, pentru cine nu e) stau înaintea celor de curiozitate (temelia, modulele). Corect pentru trafic cald; se rejudecă dacă apare trafic rece.

## Planul de dovezi

- Toate dovezile sunt reale: parcursul lui Razvan (21 de ani în marketing și vânzări, 11 în pharma) plus rezultatul firmei din New York (zile de muncă manuală devenite ore per client). Dovada cea mai tare stă în fâșia de dovadă din hero, deasupra fold-ului.
- ZERO testimoniale de clienți pe pagină, fiindcă încă nu există. Când primii clienți done-with-you termină, testimonialele intră după secțiunea `day`.
- Nu se inventează NICIODATĂ dovezi.

## Ce e lăsat deliberat pe dinafară

- Fără secțiune de preț: e o lucrare 1-on-1, prețul se discută în conversație.
- Fără formular de captură de email: conversație-întâi, CTA-ul e un singur email.

## Starea emailului (verificată 15.07.2026)

`dig +short MX creierulafacerii.ro` întoarce GOL: domeniul nu are rutare de email, cutia contact@creierulafacerii.ro nu primește mesaje. De aceea toate CTA-urile din `pagina-completa.html` (6 apariții: nav, hero, core, start, finală x2, inclusiv textul vizibil al butonului-fantomă din finală) folosesc `razvan@smartfreedomstrategies.com`, adresa pe care pagina „în curând" o folosea deja public.

Regula de revenire: în ziua în care cutia contact@creierulafacerii.ro există (Email Routing în Cloudflare, treabă de operator, cca 5 minute), toate aparițiile se schimbă înapoi pe contact@ și se face redeploy.

## Decizia de structură (cine stă la rădăcină)

Pagina „în curând" (`index.html`) RĂMÂNE la rădăcina domeniului cât ține faza de conversații calde cu Anna. Pagina completă e piesa de arătat direct în conversații, la `/pagina-completa.html`. Mutarea ei în față e o decizie viitoare a operatorului, condiționată de finalul fazei cu Anna și de existența cutiei contact@.
