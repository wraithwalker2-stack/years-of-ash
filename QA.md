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
- Reputation changes now retain faction, signed delta, source, and campaign day in the save-backed reputation log; older saves migrate to an empty log.
- Campaign now surfaces the latest dated standing changes from that authoritative log.
- The faction catalog now has packet-aligned profiles for every campaign faction, including seat, leader, summary, perk, and penalty metadata.
- Campaign now renders those faction profiles as a political dossier alongside standing and history.
- Battlefield benchmark metadata records every authored stage as an 8 × 6, 48-tile modular field and compares it honestly with a 12 × 10, 120-tile FFT-style reference footprint (0.40 tile ratio); this is a current-slice measurement, not a claim of parity.
- Campaign stage cards now show each battlefield’s measured footprint and FFT reference ratio before deployment.
- Tactical benchmark data now produces a reusable stage briefing combining objective, dimensions, modular scene status, and FFT comparison.
- Tactical battle now exposes a tested opening-briefing contract for deployment logs, keeping combat entry aligned with the measured stage data.
- Stage manifest validation now checks authored cells against the 8 × 6 bounds and rejects terrain overlap or missing manifests.
- Stage preparation now refuses invalid or missing manifests before routing into combat.
- Manifest validation also enforces the 8 × 6 dimensions, minimum deployment capacity, and deployment-cell bounds/overlap rules.
- Capture and escort manifests now require an in-bounds, non-blocked objective cell.
- Trusted sponsors now increase contract payout by 10% with deterministic rounding; hostile sponsors block the claim button and shared-state action.
- Ashen Observatory and Mosslight now use packet-authored SVG scene layers behind the logical tactical grid; the SVG assets are published as text files alongside the Pages build.
- Version label advanced to Milestone 97 · v0.97.0 Objective Validation.
- Automated QA: `pnpm exec vitest run` — 28 test files, 94 tests passing; `pnpm run build` — production build completed.
- Tactical combat now exposes an explicit selector for every living guild unit, making five-member manual control visible and deterministic.
- Reagent Burst now resolves ally healing before enemy targeting, so the learned active skill is usable in the tactical UI.
- Stage victories now grant 20 JP to every roster member and recalculate job level atomically with gold, loot, and forging material.
- Campaign preparation now uses the same location unlock gates as the World Map and labels inaccessible stages instead of allowing bypass.
- Tactical units now inherit all five authoritative saved roster identities; this is covered by an encounter regression test.
- Tactical units now also inherit saved equipment, so Ledger weapon and armor changes feed combat calculations.
- Tactical stages now route music, impact, healing, and victory cues through the audio manager with autoplay-safe handling.
- Enemy turns now prioritize the nearest living guild target deterministically, with regression coverage for authored multi-enemy rosters.
- Enemy phases now resolve every living enemy in deterministic nearest-target order; each hostile attacks when in range or advances toward its target, with the battle log summarizing the full phase.
- Battle header now surfaces the full living-enemy action queue rather than hiding the additional hostile intents behind the first target.
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

 - Packet-authored music and SFX binaries are now copied into the static `public/audio` bundle; the build includes the referenced audio files for GitHub Pages playback.
- Packet-authored Greenway, Mosslight, Ashen Observatory, and Hollow Sepulcher scene images now back the corresponding tactical boards instead of placeholder SVG layers.
- Packet-authored Floodworks, Southgate, and Veilwake scenes now back the expanded tactical stages as well.
- Tactical terrain tiles now use translucent overlays so authored stage scenes remain visible beneath the readable logical grid.

 - Version label advanced to Milestone 85 · v0.85.0 Reputation Bounds for contract standing clamped to −100…+100 with tested bounds, off-hand, hands, legs, and two accessory item families with slot coverage tests, packet equipment slots including hands, legs, two accessories, and off-hand with migration merging, tested JP progression that preserves prior job levels while advancing the active job, enforced multi-job advanced-class requirements backed by per-job level history, safe migration, and job-change persistence; legacy saves retain parent-based fallback behavior; explicit multi-job advanced-class requirements with compatibility parent tags, complete base and first-evolution starter-skill catalog coverage, all nine packet first-evolution jobs at Job Level 3 with parent-job checks, effective cast range in the battle log, shared live objective progress in the tactical header, tested fallback handling of migrated unknown job IDs, centralized job unlock requirements, deterministic counter resolution only when the defender survives, explicit battle-log feedback when enemy attacks are blocked by cover, obstacle-aware enemy attacks using the shared LOS rule, deterministic enemy step ranking that prefers safer terrain when progress is tied, high-ground cast-range bonuses on long skills, consistent hazard damage across guild and enemy movement, water traversal through obstacle-aware pathing rules, terrain movement costs, corrected stage dimensions, reaction mitigation, counter damage, shared target classification, targeting-driven area actions, and separate skill range rules.

## Commands

`pnpm test` — 25 test files, 91 tests passing.

`pnpm build` — passing.

## Public build

The static build is published at https://wraithwalker2-stack.github.io/years-of-ash/; the repository index points to the latest verified hashed assets. A fresh public browser loaded the shell, version label, navigation, Guild Hall, five-member roster, calendar, and readable layout on 2026-11-14.

## Remaining scope

The restart packet’s later milestones still require richer enemy AI, deeper hazards/elevation behavior, complete class/skill/equipment progression, fuller art archive integration, and explicit FFT-scale battlefield benchmark evidence. Those are not being claimed complete.

## Tactical benchmark

- Current slice: 8 × 6 = 48 logical tiles, fixed 4:3 board ratio, CSS-rendered tile buttons, 3 px inter-tile gaps, four terrain classes, and explicit obstacle cells. Eight stage manifests are covered by automated tests.
- Current modularity: stage identity, terrain presets, authored scene layers, encounter composition, movement, attack, AI turn, and reward persistence are separate data/state concerns.
- FFT comparison target: preserve a readable isometric/tactical playfield with at least 48 logical tiles, at least 3 meaningful elevation/terrain states, and stage data that can swap encounters without rewriting the renderer. The current slice meets the tile-count and modular-data targets, but does not yet match FFT’s isometric art, sprite resolution, animation density, or multi-height map complexity.

