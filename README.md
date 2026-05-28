# OSRS F2P Calculator

A personal Old School RuneScape calculator for F2P players. Works out how long and how many actions it takes to reach your target level, with live data pulled from the OSRS hiscores and Grand Exchange.

## Features

- **Hiscores lookup** — type your username and your real levels are pulled automatically from the OSRS hiscores API
- **Username saving** — your username is remembered so it loads every time you open the page
- **14 F2P skills** — Attack, Strength, Defence, Ranged, Magic, Prayer, Woodcutting, Fishing, Firemaking, Mining, Smithing, Cooking, Crafting, Runecraft
- **Gear picker** — select your F2P weapon, armour, and ammo; XP/hr estimates adjust based on your attack and strength bonuses
- **Prayer bonuses** — toggle prayers like Burst of Strength, Eagle Eye, and Incredible Reflexes to see how they affect your rates
- **GP/hr** — shows whether a method is profitable or costs money, using live Grand Exchange prices
- **Drop tables** — combat methods show notable drops pulled live from the OSRS Wiki
- **Offline fallback** — if any API is unavailable, built-in static data is used instead

## Usage

Visit the live site and enter your OSRS username to get started. No account or login needed.

**[Open Calculator →](https://yourusername.github.io/osrs-calc)**

> Replace the link above with your actual GitHub Pages URL after setup.

## How XP/hr is calculated

For non-combat skills, XP/hr is a fixed estimate based on typical rates.

For combat skills, a simplified version of the OSRS combat formula is used:

```
effective level = skill level × prayer multiplier
max hit = floor(0.5 + effective level × (strength bonus + 64) / 640)
accuracy = min(97%, (effective level × 2 + attack bonus) / (enemy defence × 2 + 100))
avg hit = max hit × accuracy × 0.5
ticks per kill = (enemy HP / avg hit) × weapon speed
kills per hour = 3600 / (ticks per kill × 0.6)
XP/hr = kills per hour × XP per kill
```

Rates are approximate — real rates vary depending on click speed, respawn times, banking, and other factors.

## Data sources

| Data | Source |
|------|--------|
| Player levels | [OSRS Hiscores API](https://secure.runescape.com/m=hiscore_oldschool/overall) |
| GE prices | [OSRS Wiki Prices API](https://prices.runescape.wiki/api/v1/osrs/latest) |
| Drop tables | [OSRS Wiki API](https://oldschool.runescape.wiki/api.php) |

## Local use

You can also download `index.html` and open it directly in Chrome. Live API features (hiscores, GE prices, drop tables) require an internet connection but the calculator works offline with built-in fallback data.

## Notes

- F2P only — no members content, items, or methods
- XP/hr figures are estimates, not guarantees
- GE prices update roughly every 5 minutes via the Wiki API
- This is a personal tool, not affiliated with Jagex
