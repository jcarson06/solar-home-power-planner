# Solar Home Power Planner

An interactive, single-page model for exploring what it takes to power a home
with solar panels and batteries — and what changes when you add heavy loads
like bitcoin mining or EV charging.

**Live:** https://solar-power-planner.netlify.app

Everything recalculates live as you adjust inputs. No build step, no
dependencies, no tracking, no server — one self-contained HTML file that runs
entirely in your browser.

## What it models

Set your loads, your climate, and your tolerance for cloudy days; the tool
sizes the system:

- **Daily energy** (kWh/day) across household baseline, mining, and EV charging
- **Peak simultaneous load** (kW) — what sets your inverter size
- **Solar array** (kW DC) — `daily kWh ÷ (effective peak sun hours × derate)`
- **Battery bank** (kWh usable) — daily kWh × days of autonomy, at 90% depth of discharge
- **Installed cost** — panels at ~$2.60/W, batteries at ~$998/kWh usable (Powerwall 3 class, 2026 pricing)

## Assumptions baked in

| Input | Default |
|---|---|
| Peak sun hours | 5.75 Sunbelt · 4.3 temperate · 3.5 northern (custom available) |
| Season multiplier | Winter −35% (default) · annual avg · summer +15% |
| System derate | 0.80 (adjustable 0.65–0.90) |
| Depth of discharge | 90% |
| Days of autonomy | 1.5 (adjustable 0.5–5) |
| Miner draw | 3,500 W each (Antminer S21) |
| EV consumption | 250 Wh/mile |

It defaults to **sizing for winter**, which is the conservative, off-grid-honest
choice — summer surplus is a bonus, not something to plan around.

## What it is not

This models a daily energy balance, not a minute-by-minute engineering
simulation. It does not account for roof orientation or shading, inverter
clipping, panel degradation over time, local code, or utility interconnection
rules.

**Treat every number as a starting point for a conversation with a licensed
solar installer, not a final design.**

## Running locally

Open `index.html` in any browser. That's the whole thing.

## Sources

- [EIA — average household electricity use](https://www.eia.gov/tools/faqs/faq.php?id=97&t=3)
- [Unbound Solar — peak sun hours by state](https://www.unboundsolar.com/solar-information/sun-hours-us-map)
- [EnergySage — Powerwall 3 specs & pricing](https://www.energysage.com/energy-storage/best-home-batteries/tesla-powerwall-battery-complete-review/)
- [EnergySage — 2026 solar cost per watt](https://www.energysage.com/local-data/solar-panel-cost/)
- [WattBunker — appliance wattage chart](https://wattbunker.com/blog/appliance-wattage-chart)

## License

MIT — see [LICENSE](LICENSE).
