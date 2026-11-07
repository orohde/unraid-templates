# Unraid templates by orohde

[Community Applications](https://ca.unraid.net) templates for:

| App | What it does | Image | Support |
|---|---|---|---|
| **[Ordnung!](https://github.com/orohde/Ordnung)** | Document archive on your existing folders: full-text search, OCR, inbox for scans, rules learnt from your folder structure, PDF editor, areas and accounts | `ghcr.io/orohde/ordnung` | [Issues](https://github.com/orohde/Ordnung/issues) |
| **[CutStock](https://cutstock.app)** | Cut optimisation for bars and panels with stock management, cut plans and labels | `ghcr.io/orohde/cutstock` | [Issues](https://github.com/orohde/CutStock/issues) |

## Install

Search for *Ordnung* or *CutStock* in the **Apps** tab of your Unraid server.

Before the templates are listed there, you can add this repository by hand:
*Docker → Template repositories*, add `https://github.com/orohde/unraid-templates`, save,
then *Add Container* and pick the template.

### Ordnung!

| Field | Container | Notes |
|---|---|---|
| WebUI port | 8000 | default host port 8440 |
| Archive | `/archiv` | the share with your documents, e.g. `/mnt/user/Dokumente`; each top-level folder becomes an area |
| Data | `/data` | index, settings, accounts, trash; back it up |
| Inbox (scanner) | `/eingang/scanner` | optional; add it as an inbox in the settings |
| Administrator name / password | | only used for the first account |

The app runs as `nobody:users` (PUID 99, PGID 100), the owner Unraid uses for shares; empty folders created on install are handed over to it, existing ones are left alone.
Advanced settings: PUID/PGID/UMASK, API token, OCR on/off and languages, rescan interval, starter template.

### CutStock

| Field | Container | Notes |
|---|---|---|
| WebUI port | 8000 | default host port 8420 |
| Data | `/data` | SQLite database and settings |

The web interface has no login. Keep it inside your network or put it behind a reverse proxy with authentication.

## Check the templates

```bash
python3 scripts/validate-template.py --check-urls ca_profile.xml templates/*.xml
```

`scripts/validate-template.py` comes from the [unraid-apps starter](https://github.com/unraid-apps/template) (MIT).

## License

The templates in this repository are MIT licensed. The apps have their own licenses:
Ordnung! is AGPL-3.0, CutStock has its own license (see its repository).
