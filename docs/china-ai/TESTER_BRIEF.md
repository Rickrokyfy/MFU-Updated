# MFU China AI external test package

This is an uncommitted local prototype, not a verified balance release. No HOI4 launch or launch-environment repair was performed for this assignment. No gameplay effectiveness, loading, performance or multiplayer synchronization result is claimed.

## Install and isolate the comparison layers

`china-ai-tester-overlays.zip` is **not a complete playable mod**. It contains four mutually exclusive overlay choices, matching launcher descriptors, this brief and an optional loader descriptor for the required base. It contains no base map, graphics or other base assets.

Use the exact aircraft-adjusted **Rickrokyfy/MFU-Updated revision 5c08df3707b3434e9a519ba54942323e93b226eb**, previously published and verified:

* [Base revision](https://github.com/Rickrokyfy/MFU-Updated/tree/5c08df3707b3434e9a519ba54942323e93b226eb)
* [Download that base as a ZIP without Git](https://github.com/Rickrokyfy/MFU-Updated/archive/5c08df3707b3434e9a519ba54942323e93b226eb.zip)

Extract the contents of the downloaded base's top-level folder into `mod/MFU-Updated-base` in your own HOI4 user directory. `descriptor.mod`, `common`, `map` and the other base folders must be directly inside `MFU-Updated-base`, not nested one folder deeper. Copy the supplied `MFU-Updated-base.mod` alongside that folder. This loader retains the base name MFU-Updated and its replacement paths, adds a relative local path, and omits the Workshop association. It does not supply or download the base itself. Disable other installed copies of MFU-Updated in this playset to avoid an ambiguous parent dependency. A newer Workshop build or a moving branch is not an equivalent controlled baseline.

Extract the selected `MFU_CHI_<mode>` folder and its matching `.mod` file alongside the base folder, then add **MFU-Updated and exactly one comparison overlay** to a dedicated playset. Confirm the overlay loads after MFU-Updated. The reference/default deliverable is **full**, with the human-USA interface enabled; the current local workspace also has that mode enabled. The archive does not automatically select a mode. Choose another single overlay explicitly for a comparison. Do not combine overlays with each other, another overhaul/AI mod, World Ablaze or Sheep's Mod.

| Overlay | Expected behavior |
|---|---|
| unchanged | Original pre-China-prototype policies, aircraft reduction retained |
| minimal | Earlier cautious manual opportunities; automatic plans suppressed |
| full_no_usa | Readiness/recovery/limited-operation package, no USA interface |
| full | Same package plus human-USA preferences |

No Git operations are needed. The overlays contain only affected script/localization files; unchanged/minimal modes override full-package additions with empty documents. Run fresh campaigns for between-mode comparisons. Do not hot-switch modes on an existing save: old variables may persist even when their scripts are disabled. Save/reload tests should keep the same mode. The current workspace itself has full behavior enabled; when using it as base, still load the selected comparison overlay afterward. Check load order and startup errors rather than assuming a launcher dependency resolved them correctly.

All four modes require the **same** pinned base and preserve its non-AI content, including the completed 24-tier CAS/tactical-bomber reduction. The overlays contain no equipment, unit-template, production, aid, combat-bonus, global-define or map replacements. “Unchanged” means unchanged China policy, not reversal of the aircraft reduction. Do not use different base revisions, DLC sets or unrelated mod edits between comparison modes.

Installed references used in development identify Operation Postern **1.19.4.1.99a5 (f584)**; the original mod still declares **1.19.0.1**. No compatibility metadata was changed. Record your actual version, checksum, active DLC entitlements, map/mod revision and enabled playset. Installed DLC descriptors are not ownership proof. Existing Chinese focus selection checks Waking the Tiger; other mod systems reference newer DLCs. A complete required-DLC set is not established. Use the same actual DLC set in every comparison.

## Scenario and controllers

Use the ordinary map-based China war, normally the default multiplayer 1936 bookmark at 12:00, with historical focuses and identical difficulty/settings. Avoid the later-hour no-China/fast bookmarks and partial-war configurations. The package requires existing AI-controlled, non-capitulated Nationalist China fighting existing Japan. Communist China, human China, peacetime and abstract modes retain their prior policies.

Hold Japan's controller constant within each comparison. Test AI Japan separately from a repeatable human-Japan protocol. Keep the date/conditions of war, player interventions, game speed, pause policy, aid schedules, volunteer use and air deployments consistent. Use several paired starts; report distributions and anomalies, not one favorable campaign. The package never grants equipment or recreates aid deliveries.

## Implemented full-mode cycle

1. Recovery suppresses manual offensive pokes and battleplan execution against JAP/MAN/RCC. Normal defense and the existing defensive allocations remain.
2. At a weekly assessment, China compares deployed equipment with template demand for ten essential archetypes: rifles, horses, radios, support equipment, artillery, field guns, AA, pack artillery, heavy artillery and motorized equipment. Each positive-demand archetype must reach 90% fill to prepare. Zero-demand optional categories are skipped; zero infantry demand fails closed. Specific model/variant counts are not added to archetype totals a second time. Confirm this aggregation in your executable during the first smoke test.
3. After at least 14 days of recovery and two consecutive ready weekly assessments, a valid nearby objective can open a 14-day careful opportunity window. During it the package omits an execution override: the engine may select careful plan execution and manual opportunities. It is allowed to decline attacks. There is no forced rush or constant activation.
4. A weekly drop below 80% fill in any demanded essential category ends the window. Expiry or an invalid/captured objective ends it at the daily check. New recovery starts for at least 14 days. Readiness changes can take up to a week to be detected. Two sampled assessments are not proof of continuous readiness between them.

All thresholds/durations are provisional tuning assumptions. 90/80 provides hysteresis; two assessments reject a single transient delivery; 14-day windows limit commitment and provide a recovery interval. These values are not measured balance optima. Country averages can hide a poor frontline. The scripts do not read local organization, actual supply satisfaction or local superiority; the engine retains those tactical evaluations. Even full equipment fill with empty reserves may not sustain a long offensive.

## Objectives and defensive coverage

Only two mod-specific candidates are enabled: East Hebei (609), staged from Chinese-controlled Beijing (608), and hostile Shandong (597), staged from Chinese-controlled Hebei (614). Selection requires a Chinese core held by a JAP/MAN/RCC country actually at war with China, a dynamically adjacent Chinese-controlled state, and at least six Chinese divisions in the named staging state. Counts are presence proxies, not proof of spare forces, a passable supply route, local superiority or exact adjacent-division positioning. No static bitmap adjacency claim was made.

East Hebei is the default first eligible candidate; Shandong is the fallback or a requested coastal response. Objectives invalidate when recovered, disconnected or no longer supported by the staging presence. A 25% AIFC target-score preference is applied only during an eligible window. The careful offensive posture covers the Japan/Manchukuo/Reorganized China fronts generally: target weighting does not geographically confine plan or manual attacks. The package does not increase the global concentration share, delete defensive buffers, order particular divisions or promise an encirclement. Existing frontline minimums still depend on the engine. A 10% front-unit-request increase is added for an eligible USA-requested Shandong response; check that it does not strip defense elsewhere.

Legacy date/support-counter posture rules are excluded only in the normal AI-China scope. The former minimal blanket suppression is inactive in full mode. Burma's force-execution rule is excluded in full scope so it cannot silently force or contradict the new operation window. Recovery and offensive policies are mutually exclusive; later-war counter thresholds cannot introduce a rush override.

## Human-USA interface

The English category appears for a human USA, after China initializes in a qualifying war, when USA is not at war with China. USA does not need to enter the Japanese war to make an advisory request. AI USA cannot select requests.

Choose one preference: East Hebei, Shandong response or recovery. Offensive requests are unavailable during an active window or with an invalid target; pending requests remain visibly registered while China recovers/prepares. The request lasts 30 days, with a 60-day cooldown starting on selection. No PP, equipment, donor-cost or combat-stat effect is added. A request does not create another shipment and cannot bypass readiness.

Recovery requests interrupt the current window and pause new windows for their duration. Cancel removes the preference but retains cooldown and an already-started minimum recovery interval. Cancelling or expiring an offensive preference does not cancel an autonomous operation already selected by China. Capture/invalid staging, expiry, hostile or AI USA, disabled interface or loss of China eligibility removes the preference. Peace/capitulation/controller/scenario changes clear the package state; annexation has an explicit cleanup hook. Validate the engine event scopes and scheduling in these cases.

Read-only status decisions show recovery, preparation, offensive opportunity, pending/active preference and requested recovery, with remaining-day counters. These status entries are intentionally unclickable. In full_no_usa, use a permitted debug variable inspector or an uncompressed save to inspect the namespaced phase, readiness flags, fill/demand ratios, objective and timers; no release-only diagnostic is assumed. `aiview` is documented by the shipped game, but some other AI dump commands are explicitly unavailable in release builds.

## Template findings and deliberate exclusion

No OOB/template/production changes were made. China-specific AI templates are commented out, and three shared generic entries compete for the infantry role, including a mechanized-heavy target. Shipped documentation warns against multiple role entries for a country. China starts with affordable militia-based Sanjiao Jun and more expensive regular/reorganized formations; regular battalions require more equipment in this overhaul. Observe which target the AI actually selects, its industry burden and field shortages. A blanket country exclusion or shared OOB correction would affect human/excluded scenarios, so it was not bundled without evidence of a safe dynamic selection fix. Do not assume World Ablaze's heavy infantry or vanilla MP widths fit MFU.

## First smoke and lifecycle tests

Before long campaigns check startup errors for unknown triggers/effects/IDs, the active mod checksum, status localization and archetype counter aggregation. Confirm recovery starts, a single weekly ready sample does not open a window, a second can, and an invalid objective cannot activate. Verify that no lower policy continues to suppress execution in an eligible window and no rule forces continuous activation. A lack of attacks may still be a rational engine choice.

Exercise 90% and 80% fill boundaries, zero optional/infantry demand, new equipment models/variants, a shipment that remains in stockpile versus one that reinforces divisions, an interrupted preparation sample, expiry, target capture, staging loss, repeated USA selection, cancellation and cooldown. Switch CHI to human and back, end the Japanese war, capitulate/annex/release CHI and change scenario eligibility. Confirm cleanup and a fresh recovery on re-entry. Do not change other countries' AI controls accidentally.

Save/reload within recovery, preparation, an offensive window, a pending request, a recovery request and cooldown. Timers must not reset, duplicate or skip requests. Compare host and clients' phase/objective/timers. Record desynchronization errors, daily/weekly hitching and simulation speed on the same hardware/player count. No random draws or global division scans were added, but that does not prove multiplayer safety.

## Campaign measurements and aid comparisons

For each unchanged/minimal/full_no_usa/full comparison, run no optional aid, a fixed plausible delivery schedule and a higher donor-feasible schedule. Keep donor costs and existing route mechanics intact; record amounts actually delivered and when they reached deployed units, not merely decision clicks. Include blocked/delayed deliveries. Separate USA preference effects from USA aid quantities.

Record at fixed dates and operation boundaries: Japanese divisions/manpower and division-days committed to China; equipment losses, replacements and production burden; air commitment; territory/VP/industrial/supply-hub control and dates of milestones. For China record casualties, equipment losses/fill/reserves, territory, capitulation/survival time, offensive duration, gains per loss and recovery time. Also note Japanese forces diverted away from other theaters. Increased attack count alone is not success.

The intended result is higher sustained Japanese military/economic commitment with a contestable war, not an invulnerable China or rapid Japanese collapse. Report any faster Chinese collapse, wasteful repetitive attacks, defenses stripped for objectives, stalemate created by narrow targets, broken aid or disproportionate donor burden. Recommend numerical tuning only after these observations.

## Source provenance for this prototype

Reference inspection/access date: **2026-10-30**. World Ablaze's official public China strategy and template files were inspected on its master branch through the web reader. Existing evidence does not identify an immutable source revision; cache ages differed and revision/raw/API access was unavailable or denied. No World Ablaze source adaptation or reuse license is claimed. Sheep's legitimate Workshop page was inspected, but actual scripts were unavailable; **no Sheep script adaptation** is claimed. The installed 1.19.4.1 shipped references support the independently written hooks. Loading, archetype/variant aggregation, response speed, actual template selection, outcomes/balance and multiplayer synchronization all remain external-test responsibilities.
