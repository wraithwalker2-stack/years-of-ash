# Years of Ash — Game Loop Contract

Years of Ash is a browser-based tactical guild RPG about building a company in a recovering world.

## The player loop

1. **Prepare** — name the founder and guild, review the five-person roster, assign jobs, skills, equipment, and retainers.
2. **Choose work** — read contracts, weigh faction standing and encounter pressure, then select a campaign stage.
3. **Travel** — move between unlocked locations; time advances and retainers produce small recovery benefits.
4. **Deploy** — place the guild on a tactical battlefield, read terrain and enemy intent, and choose manual or AI control.
5. **Resolve** — move, attack, use skills, manage hazards and blocked terrain, then survive the enemy phase.
6. **Return** — claim gold, items, JP, reputation, and calendar changes; use the gains to shape the next expedition.

## Design pillars

- **Company before avatar:** the roster, jobs, equipment, and faction ties matter more than a single hero.
- **Small authored fields first:** the current tactical slice uses 8 × 6 logical tiles (48 tiles), compared with a 12 × 10 / 120-tile FFT-style reference footprint; the benchmark is intentionally explicit so fields can expand without losing cohesion or modularity.
- **Consequences persist:** contracts affect reputation, travel advances the calendar, and battle rewards feed back into preparation.
- **Readable decisions:** every stage reports objective, threat mix, terrain, enemy intent, and measurable field benchmarks before the campaign grows wider.
- **Resource tension:** physical skills spend stamina; magic spends MP based on spell power, and stronger spells may require charge time that opponents can punish.

## Current foundation

The live build has the unified save state, founder setup, roster/job systems, guild services, world and campaign routes, deterministic tactical slice, manual deployment, movement, attacks, terrain, hazards, enemy AI, battle log, victory/defeat flow, loot, and GitHub Pages delivery.

The next development emphasis is making these systems feel like one connected loop: clearer preparation choices, stronger return-from-battle feedback, resource-aware magic with charge timing, and more authored stages using the same data-driven contracts.

