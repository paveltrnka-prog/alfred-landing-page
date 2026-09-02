# Alfred Landing Page

Prémiová jednostránková prezentace digitálního hotelového concierge Alfred od Previo.

Web převádí celý pobyt hosta do jednoho plynulého příběhu: online check-in, mobilní klíč, informace o hotelu a okolí, doplňkové služby, platba a recenze.

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
│   ├── alfred-arrival.webp           # Hero a příjezd do hotelu
│   ├── alfred-mobile-key.webp        # Mobilní hotelový klíč
│   └── alfred-services.webp          # Služby a objevování okolí
```

## Technické řešení

- čisté HTML, CSS a JavaScript bez frameworku,
- responzivní layout pro desktop a mobil,
- preloader a vstupní choreografie,
- scroll progress, reveal a parallax efekty,
- sticky navigace a aktivní kapitoly,
- připnutá filmová sekce mobilního klíče,
- podpora `prefers-reduced-motion`,
- optimalizované WebP obrázky.

Google Fonts jsou načítány z CDN. Všechny ostatní soubory jsou součástí repozitáře.
