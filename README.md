# Claude Marketplace

Katalog wtyczek dla Claude Code oraz OMP.

## Struktura katalogu

```
.
├── .claude-plugin/
│   └── marketplace.json    # Główny rejestr katalogu
├── plugins/                # Katalog na przyszłe wtyczki (lub referencje)
├── marketplace.json        # Korzeń dla wstecznej kompatybilności
└── README.md
```

## Rejestracja marketplace

### Claude Code / OMP

Aby dodać ten marketplace do swojej konfiguracji:

```bash
claude plugin marketplace add Olaf-Koziara/claude-marketplace
```

lub w OMP:

```bash
omp plugin marketplace add Olaf-Koziara/claude-marketplace
```

Aktualizacja listy wtyczek:

```bash
omp plugin marketplace update claude-marketplace
```

## Dodawanie wtyczek

Aby dodać wtyczkę do tego marketplace, dodaj wpis do tablicy `plugins` w `.claude-plugin/marketplace.json`:

```json
{
  "name": "nazwa-wtyczki",
  "source": "./plugins/nazwa-wtyczki",
  "description": "Opis wtyczki",
  "version": "1.0.0",
  "author": {
    "name": "Autor",
    "url": "https://github.com/autor"
  },
  "license": "MIT"
}
```
