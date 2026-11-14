# Years of Ash — Current QA

## Verified locally

- Vite + TypeScript + React static build with relative GitHub Pages asset paths.
- Unified, namespaced `GameState` with save/reset, theme, audio toggle, founder setup, roster, inventory, contracts, reputation, equipment, campaign completion, gold, JP, and job-level progression.
- Equipment restrictions enforced by allowed job data.
- Job Board rewards persist gold, JP, completed contracts, and faction reputation.
- Contract JP advances every roster member’s job level at 100-JP thresholds, capped at job level 10.
- Market purchases persist gold and inventory; older saves receive starter supplies during migration.
- Tactical slice supports deterministic movement, terrain restrictions, attacks, enemy turns, victory, and persistent battle loot claims.
- Campaign stages now consume eight explicit 8 × 6 manifests with deployment cells, water, high-ground, hazards, and elimination/capture/escort objectives.
- Tactical slice supports stage-specific enemy rosters, nearest-target enemy AI, explicit player target selection, replay, and selected-target feedback.
- Tactical slice supports manual five-member deployment, capture objectives, obstacle-aware movement and line of sight, stage-specific loot, persistent result summaries, and replay reset.
- Equipment ownership is save-backed: equipping consumes one owned copy, swapping returns replaced non-starter gear, and stage claims cannot duplicate rewards.
- Claimed stage rewards now clear the active stage and return the authoritative route to the Guild Hall, preventing stale battle sessions after victory.
- Save migration is directly tested for missing stage and inventory fields.
- Campaign entries connect to the tactical route and reflect cleared-stage state.
- Calendar state is save-backed, advances from completed contracts, and is surfaced in the Guild Hall header.
- Active and reaction skill learning is JP-backed and surfaced in the character ledger.
- Stage manifests carry music references for a later audio-manager pass; no binary audio is claimed as published.
- Faction standing now has explicit Hostile/Neutral/Trusted/Allied tiers with visible consequences on the job board.
- Trusted sponsors now increase contract payout by 10% with deterministic rounding; hostile sponsors block the claim button and shared-state action.
- Ashen Observatory and Mosslight now use packet-authored SVG scene layers behind the logical tactical grid; the SVG assets are published as text files alongside the Pages build.
- Version label advanced to Milestone 54 · v0.54.0 Enemy Phases for authored terrain rules and bounded pathing.
- Tactical combat now exposes an explicit selector for every living guild unit, making five-member manual control visible and deterministic.
- Reagent Burst now resolves ally healing before enemy targeting, so the learned active skill is usable in the tactical UI.
- Stage victories now grant 20 JP to every roster member and recalculate job level atomically with gold, loot, and forging material.
- Campaign preparation now uses the same location unlock gates as the World Map and labels inaccessible stages instead of allowing bypass.
- Tactical units now inherit all five authoritative saved roster identities; this is covered by an encounter regression test.
- Tactical units now also inherit saved equipment, so Ledger weapon and armor changes feed combat calculations.
- Tactical stages now route music, impact, healing, and victory cues through the audio manager with autoplay-safe handling.
- Enemy turns now prioritize the nearest living guild target deterministically, with regression coverage for authored multi-enemy rosters. Enemy phases resolve every living enemy in order; each hostile attacks in range or advances toward its target, and the battle log summarizes the phase.
- Battle UI now surfaces the prioritized enemy intent before the player ends the turn.
- Battle log now exposes the measurable 8 × 6 / 48-tile battlefield benchmark during deployment.
- Authored signature enemies now have distinct deterministic base damage values, covered by combat regression tests.
- Retainer assignment state now rejects unknown characters and unsupported roles before persisting.
- Save migration now removes invalid legacy retainer assignments while preserving valid roles.
- Save migration now clamps malformed inventory counts to non-negative integers.
- Save migration now clamps malformed Common forge material counts to non-negative integers.
- High-ground tiles now reduce incoming enemy damage by one, with deterministic combat coverage.
- Hazard tiles now reduce outgoing attack damage by one, complementing movement hazard damage.
- Enemy pathing now clamps proposed steps to the authored 8 × 6 board bounds.
- Shared player movement validation now rejects off-board coordinates before occupancy and distance checks.
- Enemy pathing now treats authored water cells as blocked while preserving their terrain rendering.
- Stage manifests now expose a shared deduplicated obstacle-plus-water blocker set, covered across the data layer and tactical renderer.
- The authored Steady Hands passive now adds one outgoing damage, using the saved roster passive collection.
- The authored Opportunist reaction now deals one counter damage when its bearer is struck.
- Reaction counter damage is now centralized in the combat-effects data layer and directly tested.
- Floodworks 2, Southgate, and Veilwake now use authored enemy rosters instead of the Greenway fallback; encounter tests cover their signature enemies.
- Expanded stages now have deterministic reward mappings instead of falling back to generic tonic loot.
- World travel now advances by the displayed route duration and recalculates the saved season consistently.
- First-time stage claims now advance the calendar exactly once alongside rewards and return flow; duplicate claims do not advance it.
- Campaign political powers now display live saved reputation standings, matching the Job Board’s faction consequences.
- Forge now supports salvaging owned crafted equipment into Common material through the same save-backed inventory transaction.
- Retainers are now save-backed role assignments for Apothecary, Scavenger, and Miner, with roster-driven selectors in Guild Services.
- Retainer assignments now have deterministic effects: Miner on travel, Apothecary on contracts, and Scavenger on stage claims.
- Save migration now normalizes missing character skills, passives, reactions, and equipment collections for older saves.
- Market stock now rotates deterministically for Sunmarket Jubilee and Veilwake instead of remaining a fixed list.
- Audio references now run through a single cue manager with music/SFX buses, volume metadata, and autoplay-safe failure handling.
- Forge now exposes save-backed Common material recipes with gold/material gating and inventory results.
- Stage completion now grants one Common forging material exactly once, closing the reward-to-crafting loop.
- World travel now persists the current location, advances the calendar, and only offers direct travel along unlocked roads.
- Location unlocks are now derived from completed contracts and stages instead of static presentation flags.
- Calendar holiday windows are deterministic and tested for First Thaw, Sunmarket Jubilee, Harvest Remembrance, and Veilwake; the active holiday now appears in the app header.

- Battle header now surfaces the full living-enemy action queue rather than hiding the additional hostile intents behind the first target.

- Enemy ordering and defeated-unit filtering now use one shared `enemyQueue` data helper with direct regression coverage.

Packet-authored Greenway, Mosslight, Ashen Observatory, and Hollow Sepulcher scene images now back the corresponding tactical boards instead of placeholder SVG layers.

Packet-authored Floodworks, Southgate, and Veilwake scenes now back the expanded tactical stages as well.

Character Ledger now exposes gated job changes at Job Level 2; switching applies the new job starter skill/passive and clears incompatible reactions through one save-backed action.

Job-change eligibility and starter-kit behavior now have direct data-layer regression tests; the suite is 24 files / 61 tests passing.

Version label advanced to Milestone 56 · v0.56.0 Specialist Combat for the gated job-change ledger flow.

Tactical terrain tiles now use translucent overlays so authored stage scenes remain visible beneath the readable logical grid.

Tactical movement now triggers the packet footstep cue through the shared audio manager.

Legacy stage music identifiers are normalized at the tactical data boundary to the two packet tracks actually hosted in `public/audio`, with direct coverage.

Job changes now atomically return newly incompatible equipped gear to inventory; equipment ownership tests cover the transition.

Job growth is now stat-bearing: contract and stage JP rewards use one helper that raises authored growth stats at each job-level threshold, covered by direct tests.

Advanced specialist catalog slice: Sentinel, Runeblade, Ninja, Summoner, Assassin, Monk, Paladin, Warlock, and Engineer now have packet-aligned parent metadata, Job Level 4 gates, growth profiles, and starter kits. Parent-job equipment compatibility is tested. Full specialist skill trees and multi-job prerequisites remain open.

Specialist skill-tree slice adds 18 authored active/reaction skills across the nine advanced jobs; the existing JP shop discovers them by job identity, covered by the 24-file / 66-test suite.

Specialist active-skill damage bonuses now resolve through the tactical combat-effects layer, with direct coverage for Runic Slash, Crushing Palm, and Blast Mine.

Specialist starter passives Iron Fists, Runic Edge, and Field Machinery now contribute authored outgoing power through the shared combat-effects layer, with direct tests.

Specialist reactions now contribute authored counter power through the shared reaction helper, with direct coverage for Iron Rebuke, Arcane Reprisal, and Opportunist.

Specialist healing now includes Lay on Hands at 6 HP, with the battle log naming the selected healing skill and direct combat-effects coverage.

Specialist unlocks now enforce both Job Level 4 and the authored parent job family, with invalid-parent regression coverage.

Sacred Armor and Merciful Hands now add authored healing power to Lay on Hands and Reagent Burst through the shared healing resolver, with direct coverage.\n\nMilestone 56 specialist combat now includes skill-specific actions, Blast Mine area targeting, Summon Spirit Wolf allied summons, Soul Leech defeat healing, Withering Hex weakening, explicit reaction counterattack logs, wounded-target tie breaking for enemy AI, and a high-ground attack advantage. A shared skill-targeting contract now classifies area, ally, self, enemy, and reaction actions, and area resolution consumes that classification.\n\nMerciful Hands has direct healing regression coverage.

## Commands

`pnpm test` — 25 test files, 81 tests passing.

`pnpm build` — passing.

## Public build

The static build is published at https://wraithwalker2-stack.github.io/years-of-ash/; the repository index points to the latest verified hashed assets. A fresh public browser loaded the shell, version label, navigation, Guild Hall, five-member roster, calendar, and readable layout on 2026-11-14.

## Remaining scope

The restart packet’s later milestones still require richer enemy AI, deeper hazards/elevation behavior, complete class/skill/equipment progression, fuller art archive integration, and explicit FFT-scale battlefield benchmark evidence. Those are not being claimed complete.

## Tactical benchmark

- Current slice: 8 × 6 = 48 logical tiles, fixed 4:3 board ratio, CSS-rendered tile buttons, 3 px inter-tile gaps, four terrain classes, and explicit obstacle cells. Eight stage manifests are covered by automated tests.
- Current modularity: stage identity, terrain presets, authored scene layers, encounter composition, movement, attack, AI turn, and reward persistence are separate data/state concerns.
- FFT comparison target: preserve a readable isometric/tactical playfield with at least 48 logical tiles, at least 3 meaningful elevation/terrain states, and stage data that can swap encounters without rewriting the renderer. The current slice meets the tile-count and modular-data targets, but does not yet match FFT’s isometric art, sprite resolution, animation density, or multi-height map complexity.

