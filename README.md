# claude-marketplace

Katalog wtyczek dla Claude Code oraz OMP.

## Struktura katalogu

```
.
├── .claude-plugin/
│   └── marketplace.json    # Manifest katalogu marketplace
├── plugins/                # Katalog na lokalne wtyczki (lub referencje)
└── README.md
```

## Rejestracja marketplace

### Claude Code

```bash
claude plugin marketplace add Olaf-Koziara/claude-marketplace
```

### OMP

```bash
omp plugin marketplace add Olaf-Koziara/claude-marketplace
```

Aktualizacja listy wtyczek:

```bash
omp plugin marketplace update olaf-marketplace
```

## Dodawanie wtyczek

Aby zarejestrować wtyczkę w tym katalogu, dodaj wpis do tablicy `plugins` w `.claude-plugin/marketplace.json`:

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

Walidacja poprawności manifestu:

```bash
claude plugin validate .
```
