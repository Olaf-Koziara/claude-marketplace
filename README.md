# claude-marketplace

Katalog wtyczek dla Claude Code oraz OMP.

## Struktura katalogu

```
.
├── .claude-plugin/
<<<<<<< HEAD
│   └── marketplace.json    # Główny rejestr katalogu
├── plugins/
│   └── atlassian/          # Wtyczka: Jira i Confluence (MCP)
│       ├── .claude-plugin/
│       │   └── plugin.json
│       └── skills/
│           └── atlassian-usage/
│               └── SKILL.md
├── marketplace.json        # Korzeń dla wstecznej kompatybilności
||||||| dc4231e
│   └── marketplace.json    # Główny rejestr katalogu
├── plugins/                # Katalog na przyszłe wtyczki (lub referencje)
├── marketplace.json        # Korzeń dla wstecznej kompatybilności
=======
│   └── marketplace.json    # Manifest katalogu marketplace
├── plugins/                # Katalog na lokalne wtyczki (lub referencje)
│   └── atlassian/          # Wtyczka: Jira i Confluence (MCP)
│       ├── .claude-plugin/
│       │   └── plugin.json
│       ├── .mcp.json
│       └── skills/
│           └── atlassian-usage/
│               └── SKILL.md
>>>>>>> 5d6448a0027297f7e2454709ecdf24d1318f63b2
└── README.md
```

## Rejestracja marketplace

Nazwa marketplace w katalogu to `koziara-plugins`.

Nazwa marketplace w katalogu to `olaf-marketplace`.

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
<<<<<<< HEAD
omp plugin marketplace update koziara-plugins
||||||| dc4231e
omp plugin marketplace update claude-marketplace
=======
omp plugin marketplace update olaf-marketplace
>>>>>>> 5d6448a0027297f7e2454709ecdf24d1318f63b2
```

## Wtyczki

### atlassian

Jira i Confluence przez serwer MCP `mcp-atlassian` uruchamiany przez `uvx`.
Wymaga zainstalowanego [`uv`](https://docs.astral.sh/uv/).

Instalacja:

```bash
/plugin install atlassian --marketplace Olaf-Koziara/claude-marketplace
```

Po instalacji Claude Code pyta o konfigurację (`/plugin` → atlassian). Podstawowa
ścieżka to URL + personal access token (PAT) dla każdego produktu:

| Produkt | URL | Token |
| --- | --- | --- |
| Jira | `jira_url` | `jira_personal_token` |
| Confluence | `confluence_url` | `confluence_personal_token` |

PAT tworzy się w profilu Atlassian (Profile → Personal Access Tokens) i jest
standardem dla Server / Data Center. Atlassian Cloud nie ma PAT — tam zamiast
tokena podaje się parę `jira_username` + `jira_api_token` (analogicznie
`confluence_username` + `confluence_api_token`). Wypełnia się tylko jeden
wariant; pozostałe pola zostawia się puste.

Puste `jira_url` lub `confluence_url` wyłącza narzędzia danego produktu, więc
jedna wtyczka obsługuje też wyłącznie Jirę albo wyłącznie Confluence.
`read_only_mode` ukrywa narzędzia zapisujące.

Na PAT dostępne są 96 narzędzi. Dwa narzędzia Jira Cloud — `jira_batch_get_changelogs`
i `jira_move_issue` — przy PAT nie są rejestrowane.

Narzędzia widoczne są jako `mcp__plugin_atlassian_atlassian__jira_*` oraz
`mcp__plugin_atlassian_atlassian__confluence_*` (np. `jira_search`,
`jira_get_issue`, `confluence_get_page`).

Jeśli w konfiguracji jest już ręcznie dodany serwer `mcp-atlassian` z tym samym
poleceniem (`uvx mcp-atlassian`), Claude Code wyłącza serwer z wtyczki jako
duplikat — to zamierzone zachowanie. Aby korzystać z wersji z wtyczki, usuń
ręczny wpis (`claude mcp remove mcp-atlassian`).

## Dodawanie wtyczek

<<<<<<< HEAD
Aby dodać wtyczkę do tego marketplace, dodaj wpis do tablicy `plugins` w
`.claude-plugin/marketplace.json` oraz w `marketplace.json` (oba pliki są
identyczne):
||||||| dc4231e
Aby dodać wtyczkę do tego marketplace, dodaj wpis do tablicy `plugins` w `.claude-plugin/marketplace.json`:
=======
Aby zarejestrować wtyczkę w tym katalogu, dodaj wpis do tablicy `plugins` w `.claude-plugin/marketplace.json`:
>>>>>>> 5d6448a0027297f7e2454709ecdf24d1318f63b2

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

<<<<<<< HEAD
Walidacja:

```bash
claude plugin validate --strict .
```
||||||| dc4231e
=======
Walidacja poprawności manifestu:

```bash
claude plugin validate .
```
>>>>>>> 5d6448a0027297f7e2454709ecdf24d1318f63b2
