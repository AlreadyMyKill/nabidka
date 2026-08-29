# Nabídka — interaktivní ukázka

Nabídka na vývoj privátního katalogu pro kamennou prodejnu, postavená jako **funkční PWA**.
Slouží zároveň jako živý prototyp nabízeného produktu — klient si ji přidá na plochu telefonu
a tím si osahá přesně tu aplikaci, o které nabídka mluví.

## Obsah

| Soubor | K čemu je |
|---|---|
| `index.html` | Celá aplikace — obsah, vzhled i logika v jednom souboru |
| `manifest.webmanifest` | Aby to šlo přidat na plochu jako aplikaci |
| `sw.js` | Service worker — offline provoz |
| `icons/` | Ikony na plochu (192, 512, 180 px) |

## Co je potřeba doplnit před schůzkou

V `index.html` jsou tři místa označená `[HRANATÝMI ZÁVORKAMI]`:

- `[NÁZEV PRODEJNY]` — v hlavičce aplikace
- `[TELEFON]` — v patičce

## Lokální spuštění

Service worker vyžaduje `http://` nebo `https://`, přes `file://` nefunguje.
Otevřením souboru přímo v prohlížeči se aplikace zobrazí, ale nepůjde přidat na plochu.
Pro plnou funkčnost nasadit na GitHub Pages (viz níže).

## Nasazení na GitHub Pages

1. Založit veřejný repozitář na GitHubu
2. `git remote add origin <URL>` a `git push -u origin main`
3. V repozitáři: **Settings → Pages → Source: Deploy from a branch → main / (root)**
4. Za minutu běží na `https://<uživatel>.github.io/<repozitář>/`

HTTPS je podmínkou pro service worker i pro přidání na plochu. GitHub Pages ho poskytuje automaticky.

## Editace obsahu

Všechny karty nabídky jsou v poli `POSTS` v `index.html`. Každá má:

```js
{
  id, cat, g, kicker,     // identifikátor, kategorie, barva pozadí, nadpisek
  pinned, sale,           // volitelné odznaky
  title, excerpt, body    // nadpis, shrnutí na kartě, HTML detailu
}
```

Kategorie ve filtru se berou z pole `CATS`.
