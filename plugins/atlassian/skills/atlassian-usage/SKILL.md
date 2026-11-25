---
name: atlassian-usage
description: Guidance for the Atlassian plugin's Jira and Confluence MCP tools - picking the right tool, auth modes, and read-only behavior. Use when working with Jira issues, sprints, boards, worklogs, or Confluence pages, spaces, and search.
---

# Atlassian (Jira & Confluence) tool usage

Tools come from the `atlassian` MCP server (upstream project:
[sooperset/mcp-atlassian](https://github.com/sooperset/mcp-atlassian)), launched via
`uvx mcp-atlassian`. Names follow `{service}_{action}`.

## What is available depends on configuration

- Jira tools load only when a **Jira URL** plus auth (username + API token for Cloud,
  or a personal access token for Server/DC) is configured in the plugin settings.
- Confluence tools load only when a **Confluence URL** plus auth is configured.
- **Read-only mode** (plugin setting) removes every write tool: no
  `jira_create_issue`, `jira_update_issue`, `confluence_create_page`, etc.

If a tool you expect is missing, check `/config` → plugin `atlassian` settings first.

## Common picks

| Need | Tool |
| :- | :- |
| Find issues by JQL | `jira_search` |
| One issue with details | `jira_get_issue` |
| Create / update / transition | `jira_create_issue`, `jira_update_issue`, `jira_transition_issue` (write) |
| Sprints and boards | `jira_get_sprints_from_board`, `jira_get_board_issues` |
| Worklogs | `jira_get_worklog`, `jira_add_worklog` (write) |
| Search Confluence content | `confluence_search` (supports CQL) |
| Read a page | `confluence_get_page` (by id, title+space, or URL) |
| Page tree / children | `confluence_get_page_children` |
| Comments | `jira_get_issue_comments`, `confluence_get_comments` |
| Attachments | `jira_get_issue_attachments`, `jira_download_attachment` |

## Notes

- Cloud URL shapes: Jira `https://your-domain.atlassian.net`, Confluence
  `https://your-domain.atlassian.net/wiki`.
- Prefer CQL in `confluence_search` (e.g. `text ~ "term" and space.key = "ENG"`).
- Prefer JQL in `jira_search` (e.g. `project = ENG AND status != Done`).
- Paginated tools take `start_at`/`max_results` or `limit`/`cursor`; don't fetch
  everything at once.
