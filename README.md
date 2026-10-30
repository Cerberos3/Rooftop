# Rooftop Lineup — nasazení na Netlify

Statická stránka, jeden soubor. Nic se nebuilduje, nic se neinstaluje.

**Projekt už je na Netlify založený:**

- Název: `rooftop-lineup`
- Adresa: https://rooftop-lineup.netlify.app
- Site ID: `b4aaeed8-f045-406a-a5bf-59afccc19299`
- Správa: https://app.netlify.com/projects/rooftop-lineup

Zbývá do něj nahrát soubory. Adresa do té doby ukazuje prázdný projekt.

## Varianta 1 — příkazem (nejrychlejší, ~30 s)

Rozbal tuhle složku, otevři v ní terminál a spusť:

```shell
npx netlify-cli deploy --prod --dir . --site b4aaeed8-f045-406a-a5bf-59afccc19299
```

Poprvé si to vyžádá přihlášení — otevře prohlížeč, jedno kliknutí.

## Varianta 2 — přetažením v prohlížeči

1. Otevři https://app.netlify.com/projects/rooftop-lineup
2. Záložka **Deploys**
3. Dolů na **Drag and drop your site output folder here**
4. Přetáhni tam **celou rozbalenou složku** (ne zip, ne jen `index.html` —
   `netlify.toml` tam musí být taky)

Netlify chce složku, ne archiv. Zip je potřeba nejdřív rozbalit.

## Nová verze později

Úplně stejně, do stejného projektu. Adresa zůstane, obsah se přepíše.

## Co je ve složce

| Soubor | K čemu |
|---|---|
| `index.html` | Celá aplikace — lineup, nápady, tým |
| `netlify.toml` | Hlavičky a cachování; díky němu se nová verze projeví hned |
| `favicon.svg` | Ikona v záložce prohlížeče |

## Ochrana heslem

Adresa je veřejná pro každého, kdo ji zná. Na stránce nejsou žádné
osobní údaje, ale je tam vaše strategie a plán dílů.

Zkus v Netlify: *Project configuration → Access & security → Visitor access*.

- **Je tam Password protection** → nastav heslo a máš hotovo.
- **Není tam** → tvůj účet to na free tarifu neumí. Pak buď:
  - necháš adresu nezveřejněnou a spoléháš na to, že ji nikdo neuhodne
    (stránka má `noindex`, takže se nedostane do vyhledávačů), nebo
  - zkusíš odkomentovat `Basic-Auth` v `netlify.toml` — na starších
    účtech to funguje zdarma, na novějších ne.

## Důležité — data

Poznámky a změny se zatím ukládají **jen v prohlížeči toho, kdo je zapsal**.
Ondra, Kuba ani Míša tvoje poznámky neuvidí a ty jejich taky ne.
Každý uvidí stejný výchozí obsah a svoje vlastní úpravy.

Až na to bude databáze, mění se jediné místo: objekt `store`
na začátku `<script>` v `index.html`. Má dvě funkce, `load` a `save`,
obě async. Zbytek stránky zůstane beze změny.
