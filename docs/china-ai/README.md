# China AI external testing package

This branch contains the aircraft-adjusted MFU base plus the full China operations package and optional human-USA preferences. It is an untested local prototype prepared for external gameplay testing.

- [Tester guide](TESTER_BRIEF.md): base revision, installation, all four comparison modes, provisional settings, limitations and measurement plan.
- [Comparison overlays ZIP](china-ai-tester-overlays.zip): unchanged, minimal, full without USA preferences and full; requires the exact base identified in the guide. It is not a standalone mod.
- [Static results](static-results.json): existing script-level checks; no engine execution.
- [Archive integrity](package-integrity.json): existing comparison-package checksum and parser checks.

Full mode with USA preferences is active in the branch's mod files. For controlled comparisons, use the common aircraft-adjusted base identified in the guide and exactly one overlay. Sector preferences do not confine attacks geographically. Requests cannot bypass readiness; cancellation does not cancel an autonomous operation already selected. Numerical defaults are provisional. Runtime loading, variant aggregation, responsiveness, templates, balance and multiplayer synchronization require external testing.

No World Ablaze or Sheep scripts were imported. Reference inspection date is 2026-10-30; World Ablaze's immutable revision could not be pinned.
