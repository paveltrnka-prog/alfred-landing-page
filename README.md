# Alfred Landing Page

Prémiová jednostránková prezentace digitálního hotelového concierge Alfred od Previo.

Web převádí celý pobyt hosta do jednoho plynulého příběhu: online check-in, mobilní klíč, informace o hotelu a okolí, doplňkové služby, platba a recenze.

## Repozitáře a nasazení

Projekt je zrcadlený do dvou GitHub repozitářů:

- **Osobní** — [github.com/trnkapavel/alfred-landing-page](https://github.com/trnkapavel/alfred-landing-page) (`origin`)
- **Firemní** — [github.com/paveltrnka-prog/alfred-landing-page](https://github.com/paveltrnka-prog/alfred-landing-page) (`company`)

Live verze (GitHub Pages, firemní repo, branch `main`, root `/`):
**[paveltrnka-prog.github.io/alfred-landing-page](https://paveltrnka-prog.github.io/alfred-landing-page/)**

Nasazení je automatické přes GitHub Pages po pushi na `main` v firemním repu — žádný build krok, `index.html` se servíruje přímo. Push na oba remoty:

```bash
git push origin main
git push company main
```

## Lokální spuštění

Projekt nemá build krok ani runtime závislosti. Stačí spustit jednoduchý statický server:

```bash
python3 -m http.server 4173 --bind 127.0.0.1
```

Potom otevřete [http://127.0.0.1:4173](http://127.0.0.1:4173).

## Struktura

```text
.
├── index.html                         # Kompletní stránka, CSS a JavaScript
├── assets/
│   ├── film/lg, film/sm/             # Snímky úvodního filmu (135× WebP, 1600 a 900 px)
│   ├── alfred-hero.webp              # Fotografie recepce (sekce `.still`)
│   ├── alfred-arrival.webp           # Příjezd do hotelu
│   ├── alfred-mobile-key.webp        # Mobilní hotelový klíč
│   ├── alfred-services.webp          # Služby a objevování okolí
│   ├── app/                          # Obrazovky z návrhu aplikace (check-in, platba, klíč, tipy)
│   ├── alfred-logo.svg               # Původní dodané logo
│   └── alfred-logo-transparent.png   # Transparentní maska loga pro dynamické barvy
```

## Technické řešení

- čisté HTML, CSS a JavaScript bez frameworku,
- responzivní layout pro desktop a mobil,
- preloader a vstupní choreografie,
- úvodní filmový příběh „Příjezd“ (`.film`) — snímky filmu se přetáčejí scrollem na canvasu, do displeje telefonu se přes CSS `matrix3d` (homografie z naměřených rohů displeje) promítá živé HTML UI Alfreda a na konci kamera „vplave“ do obrazovky a předá stránku hero sekci; při `prefers-reduced-motion` se sekce skryje,
- hero s interaktivní replikou aplikace Alfred v telefonu — úkoly před příjezdem se postupně odškrtávají (nebo je odklikne návštěvník), po dokončení se odemkne pokoj a PIN, záložka Klíč otevře mobilní klíč; telefon se natáčí za kurzorem; za ním se otevře víko notebooku s webovou verzí Alfreda,
- sekce `.still` — fotografie recepce se při scrollu rozevře z ořezu (clip-path) na celou obrazovku,
- kinetické nadpisy — slova hlavních nadpisů vyjíždějí postupně zespodu,
- sekce „Přijeďte. Ubytujte se. Odemkněte. Užijte si.“ (`.mf`) — světlý „jízdní řád“ jednoho příjezdu: připnutá na scroll, slova se postupně dopisují, u každého řádku naskočí čas a poznámka, co Alfred zařídil, a na konci závěrečná věta,
- sekce „Aplikace zblízka“ (`.app`) — připnutý telefon se skutečnými obrazovkami z návrhu aplikace, které se scrollem střídají (clip-path), vlevo se zvýrazní odpovídající krok,
- scroll progress, reveal a parallax efekty,
- nekonečně smyčkovaný ticker pás (`.ticker`) — track se za běhu klonuje podle šířky viewportu, takže animace nikdy nevyjede do prázdna,
- sticky navigace a aktivní kapitoly,
- připnutá filmová sekce mobilního klíče,
- podpora `prefers-reduced-motion` (u tickeru i manifesto revealu),
- optimalizované WebP obrázky.

Google Fonts jsou načítány z CDN. Všechny ostatní soubory jsou součástí repozitáře.
