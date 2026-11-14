# Years of Ash — Current QA

## Verified locally

- Milestone 183: the tactical battle log now uses a polite live region so new movement, attack, and outcome messages can be announced accessibly.
- Milestone 184: tactical grid cells now expose selected and targeted focus through `aria-pressed`, keeping keyboard and assistive-technology state aligned with the visual highlight.
- Milestone 185: tactical cells now provide a high-contrast keyboard focus ring and a matching pressed-state outline for reliable navigation on the battlefield.
- Milestone 186: the tactical battlefield now exposes grid semantics and each authored cell exposes the gridcell role for structured assistive-technology navigation.
- Milestone 187: tactical grid cells now expose one-based row and column indices, making the authored battlefield geometry available to assistive technology.
- Milestone 188: tactical grids now expose their authored row and column totals, completing the battlefield dimension metadata for structured navigation.
- Milestone 182: tactical board buttons now expose complete accessible cell labels, including coordinates, terrain, occupants, HP, objectives, and legal movement affordances.
- Milestone 181: tactical cells now expose accessible coordinate, terrain, occupant, objective, and movement-preview labels.
- Milestone 180: reachable movement cells now have a visible tactical highlight style, completing the movement-preview feedback loop.
- Milestone 179: tactical boards now mark legal movement destinations from the shared reachable-cell calculation while a guild unit is active.
- Milestone 178: reachable-cell coverage now verifies terrain costs, including water consuming two movement points.
- Milestone 177: movement now exposes one tested reachable-cell enumerator built on shared obstacle, occupancy, board-bound, and terrain-cost rules.
- Milestone 176: AI attack planning now uses the shared line-of-sight rule, so covered targets produce an advance plan instead of an impossible attack.
- Milestone 175: Field Tonic is classified as a self-targeting skill in the shared targeting data, matching its combat execution and log semantics.
- Milestone 174: Field Tonic now resolves as a usable self-heal for its starter Alchemist skill, restoring 3 HP with deterministic coverage.
- Milestone 173: Quickstep now performs a real obstacle-aware one-tile reposition toward the selected or nearest enemy, consumes the action, and applies authored hazard damage.
- Milestone 172: Guard Stance is now a visible tactical action that reduces the next incoming hit by 2, consumes the unit action, breaks when struck, and has direct combat-effect coverage.
- Milestone 143: AI end-turn selection now uses the shared attack/advance planner and records the proposed action before manual confirmation.
- Milestone 144: actor, target, and attack/advance choice now come from one tested AI turn-plan helper.
- Milestone 145: AI advance planning now has a deterministic unoccupied step helper with tie-breaking coverage.
- Milestone 146: tactical AI advance previews now include the chosen destination cell from the shared step helper.
- Milestone 147: AI advance planning now rejects authored obstacle cells, with deterministic fallback coverage.
- Milestone 148: AI advance planning now enforces authored battlefield bounds, with edge-case regression coverage.
- Milestone 149: AI advance planning prefers safe terrain over hazards when progress is tied, with deterministic coverage.
- Milestone 150: AI battle-log planning now uses a shared tested label for attack and advance destinations.
- Milestone 151: the `M` shortcut now ignores content-editable elements as well as inputs and textareas.
- Milestone 152: AI control now executes a deterministic advance plan before the enemy phase; manual control remains unchanged.
- Milestone 153: AI control now resolves a deterministic basic attack when its planned target is in range and visible.
- Milestone 154: AI attacks now award the same deterministic 25g per downed enemy as manual attacks.
- Milestone 155: AI now advances toward an in-range target when line of sight is blocked, instead of silently stalling.
- Milestone 156: AI attack eligibility is centralized and tested for range, living targets, and line of sight.
- Milestone 157: centralized AI attack eligibility now rejects stale plans involving downed actors or targets.
- Milestone 158: centralized AI attack eligibility now covers the exact range-2 boundary and rejects range-3 targets.
- Milestone 159: AI battle logs now accurately distinguish automatic execution from plans with no legal automatic action.
- Milestone 160: automatic AI attack logs now explicitly report when their target is downed.
- Milestone 161: tactical replay logs now restate the persisted Manual/AI control mode.
- Milestone 162: AI attack-versus-advance resolution is centralized and tested against line of sight.
- Milestone 163: centralized AI resolution now returns no action for downed actors or targets.
- Milestone 164: centralized AI resolution now has regression coverage for configurable attack ranges.
- Milestone 165: AI tactical logs now prefer readable unit names over internal IDs.
- Milestone 166: AI turn-plan coverage now verifies configurable attack range propagation.
- Milestone 167: AI turn planning now returns no plan when no living target exists.
- Milestone 168: AI turn planning now returns no plan when every guild actor is down.
- Milestone 169: configurable AI turn planning now covers the out-of-range advance boundary.
- Milestone 170: AI target selection now returns no target when every enemy is down.
- Milestone 171: Settings copy now describes the current unified save instead of stale Milestone 2 wording.
- Milestone 142: tactical combat now shows the persisted Manual/AI control mode beside an in-place switch, while retaining the tested `M` shortcut.
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
- Reputation changes now use one bounded transition helper that always records signed delta, source, and campaign day.
- Stage validation now accepts arbitrary imported manifest objects, with malformed-data coverage in tests.
- Stage validation now requires a music reference and a supported eliminate/capture/escort victory mode.
- Objective rules now have a tested evaluator for eliminate, capture, and escort completion, including enemy-clearance requirements.
- Battle outcome rules now provide one tested active/victory/defeat contract with defeat precedence.
- Equipment now has a centralized nine-slot schema normalizer and duplicate-loadout validator.
- Save migration now applies the nine-slot equipment normalizer to every restored character.
- Save migration coverage now asserts all nine equipment keys for an older character record.
- Stage music references now pass through a deterministic local published-track mapper with explicit legacy-name handling.
- The audio manager now exposes one safe music-cue lookup with a deterministic default fallback.
- Tactical battle now routes stage music through the shared audio cue lookup and manager.
- The stage catalog test now requires every campaign entry to have a valid manifest; missing stage data cannot be silently skipped.
- Stage validation now cross-checks mapped music against the published local audio cue catalog.
- Tactical capture and escort victory now matches the authoritative rule: reach the objective only after all enemies are cleared.
- The live tactical screen now derives victory/defeat from the shared battle-outcome contract.
- Capture and escort battle descriptions now explicitly communicate the clear-then-reach requirement.
- Objective validation now rejects capture/escort cells unreachable from deployment under water/obstacle blocking.
- Deployment validation now rejects guild start cells blocked by water or obstacles.
- Runtime deployment validation now reports authored obstacle overlap, keeping the combat entry guard aligned with manifest validation.
- Runtime placement now refuses water and obstacle cells before confirmation, matching the manifest guard during manual deployment.
- Deployment eligibility is now centralized in one data-layer rule shared by the tactical placement flow and deployment validation.
- Stage validation now requires exactly five deployment cells, matching the authoritative five-member guild roster and runtime deployment contract.
- Stage validation now rejects duplicate deployment coordinates so five authored slots always represent five usable positions.
- Tactical encounter construction now places all five authoritative guild members directly on the stage manifest’s authored deployment cells.
- Published music mapping now explicitly covers every authored stage-family reference and documents the packet’s two-track fallback without inventing missing audio.
- Tactical roster placement is now regression-tested against every authored campaign manifest, not only the opening stage.
- The unused duplicate tactical combat component has been removed; `TacticalBattleScreen` is now the sole combat route, with `TacticalBattle.tsx` limited to shared encounter and terrain helpers.
- The Battle route now refuses to invent a default encounter when no stage is prepared and instead directs the player back to Campaign.
- Trusted sponsors now increase contract payout by 10% with deterministic rounding; hostile sponsors block the claim button and shared-state action.
- Ashen Observatory and Mosslight now use packet-authored SVG scene layers behind the logical tactical grid; the SVG assets are published as text files alongside the Pages build.
- Version label advanced to Milestone 171 · v3.38.0 Current Save Copy.
- QA counts now match the latest 33-file, 118-test verification run.
- Tactical control mode now has a tested manual/AI toggle contract as the foundation for the next combat UI pass.
- AI control now has a tested nearest-living-enemy selector with deterministic id tie-breaking.
- AI control now has a tested attack-or-advance planner that returns an action instead of stalling when a target is out of range.
- Battle control mode is now part of the authoritative save state and older saves migrate safely to manual control.
- Tactical battle briefing now reads and displays the authoritative saved control mode.
- Settings now exposes a Manual guild control / AI guild control toggle backed by the same saved GameState field.
- In AI mode, ending the turn selects the deterministic next guild actor and nearest living target using the shared AI planner, while preserving manual confirmation of the action.
- Save migration coverage now proves both the manual default for older saves and preservation of an explicitly saved AI mode.
- AI end-turn actor/target selection is now centralized in the tested battle-control data layer.
- Tactical combat now switches the persisted Manual/AI control mode in place with the `M` key and advertises that control in the opening log.
- The `M` shortcut ignores focused input and textarea elements, preventing accidental mode changes while typing.
- Package metadata now reports version `3.8.0`, matching the visible build release label.
- The project now exposes one `pnpm qa` command that runs the complete test suite and production build sequentially.
- Battle-entry readiness is now a tested data-layer contract shared by the tactical screen, preventing an unprepared route from entering combat.
- Automated QA at the current release: `pnpm exec vitest run` — 33 test files, 118 tests passing; `pnpm run build` — production build completed.
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

`pnpm test` — 33 test files, 118 tests passing.

- The published QA ledger reports the current 33-file, 120-test verification counts.

`pnpm build` — passing.

## Public build

The static build is published at https://wraithwalker2-stack.github.io/years-of-ash/; the repository index points to the latest verified hashed assets. A fresh public browser loaded the shell, version label, navigation, Guild Hall, five-member roster, calendar, and readable layout on 2026-11-14.

## Remaining scope

The restart packet’s later milestones still require richer enemy AI, deeper hazards/elevation behavior, complete class/skill/equipment progression, fuller art archive integration, and explicit FFT-scale battlefield benchmark evidence. Those are not being claimed complete.

## Tactical benchmark

- Current slice: 8 × 6 = 48 logical tiles, fixed 4:3 board ratio, CSS-rendered tile buttons, 3 px inter-tile gaps, four terrain classes, and explicit obstacle cells. Eight stage manifests are covered by automated tests.
- Current modularity: stage identity, terrain presets, authored scene layers, encounter composition, movement, attack, AI turn, and reward persistence are separate data/state concerns.
- FFT comparison target: preserve a readable isometric/tactical playfield with at least 48 logical tiles, at least 3 meaningful elevation/terrain states, and stage data that can swap encounters without rewriting the renderer. The current slice meets the tile-count and modular-data targets, but does not yet match FFT’s isometric art, sprite resolution, animation density, or multi-height map complexity.

