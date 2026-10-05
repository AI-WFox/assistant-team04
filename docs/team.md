# Team Roster & Roles — Team 04

CSC10014 — Smart Virtual Assistant, HCMUS.

`TBD` marks information that has not yet been supplied or confirmed. Replace it
with each member's actual full name, student ID, and GitHub username before
final submission. The documentation lead's display name is supplied by the
contributor; confirm its full spelling for the official roster.

| No | Full Name | Student ID | GitHub Username | Role |
|:---|:---|:---|:---|:---|
| 1 | TBD | TBD | TBD | Project Manager / Config |
| 2 | TBD | TBD | TBD | Backend Engineer |
| 3 | TBD | TBD | TBD | DevOps / Tooling |
| 4 | TBD | TBD | TBD | Data Specialist |
| 5 | TBD | TBD | TBD | QA / Test Engineer |
| 6 | TBD | TBD | TBD | UI/UX Designer |
| 7 | Tam K. Pham | TBD | [@AI-WFox](https://github.com/AI-WFox) | Documentation Lead |

## Branches and ownership

| Member | Branch | Assigned files |
|:---|:---|:---|
| 1 | `feat/config` | `.gitignore`, `requirements.txt`, `pyproject.toml` |
| 2 | `feat/backend` | `src/assistant/__init__.py`, `src/assistant/rules.py`, `src/assistant/__main__.py` |
| 3 | `feat/scripts` | `scripts/check_env.py` |
| 4 | `feat/data` | `data/offices.csv`, `data/README.md` |
| 5 | `feat/tests` | `tests/test_smoke.py` |
| 6 | `feat/ui` | `ui/README.md` |
| 7 | `feat/docs` | `README.md`, `docs/README.md`, `docs/team.md` |

This table records the assignment. Files such as `.gitignore` and
`data/README.md` still need to be added by their respective owners.

## Review and milestone responsibilities

Each member opens a PR from their branch into the team repository's `main`.
A teammate or the project manager reviews the change before merging. The
recommended merge order is config, backend, scripts, data, tests, UI, then docs.
After all seven PRs are merged and setup checks pass, Member 1 creates and
pushes the `v0.1-setup` tag.
