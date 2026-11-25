# Atlassian (Jira & Confluence) Plugin

Wtyczka do integracji z produktami Atlassian (Jira oraz Confluence) poprzez serwer MCP `mcp-atlassian`.

## Instalacja

```bash
/plugin install atlassian --marketplace Olaf-Koziara/claude-marketplace
```

## Możliwości

- **Jira**: obsługa zgłoszeń (issues), sprintów, tablic, logowania czasu pracy (worklogs) i załączników.
- **Confluence**: przeglądanie i edycja stron, przestrzeni, wyszukiwanie oraz komentarze.
- **Skill**: `atlassian:atlassian-usage` wspomagający poprawne dobieranie narzędzi.

## Konfiguracja (`userConfig`)

Wtyczka wspiera uwierzytelnianie dla wersji Atlassian Cloud oraz Atlassian Server / Data Center:

- **Jira Cloud**: `jira_url`, `jira_username`, `jira_api_token`
- **Jira Server / DC**: `jira_url`, `jira_personal_token`
- **Confluence Cloud**: `confluence_url`, `confluence_username`, `confluence_api_token`
- **Confluence Server / DC**: `confluence_url`, `confluence_personal_token`
- **Read-only**: `read_only_mode` (opcjonalny tryb tylko do odczytu)
