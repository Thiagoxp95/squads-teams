# Squads community teams

Ready-made teams for Squads. They appear in the app under **Templates → Explore**.

| Team | Members | What it does |
|---|---|---|
| [Product squad](teams/product-squad/README.md) | 6 | A full product team. You are the Product Manager. |
| [QA team](teams/qa-team/README.md) | 4 | Independent testing: strategy, automation, exploration, accessibility and performance. |
| [Head hunters](teams/head-hunters/README.md) | 5 | Find jobs in Canada, build your network there, and land the offer. |

## Adding a team

1. Add `teams/<slug>/<slug>.squadsteam.json` (a `squads.package` v2 file, e.g. from **Templates → Share** in the app), a `README.md` and its `skills/<name>/SKILL.md` files.
2. Add the team to `catalog.json`.

## Licenses

The starter skills are condensed and modified from MIT and Apache-2.0 sources; each `SKILL.md` names its source on its last line, and the license texts are in [LICENSES/](LICENSES/).

## OpenMausBot

The same teams in OpenMausBot's format (0.1.98 or later) are in [openmausbot/](openmausbot/). In OpenMausBot, open **Templates → Import → Load from GitHub** and paste a file's link.
