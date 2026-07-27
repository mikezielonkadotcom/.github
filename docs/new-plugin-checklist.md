# New Plugin Checklist (mikezielonkadotcom)

This is the default checklist for *any new WordPress plugin repo* we create under the `mikezielonkadotcom` GitHub org.

## 1) Shared Update Machine updater (required)
- [ ] Add `includes/um-updater.php` from a reviewed `dontpressthis/um-updater` release tag through an explicit plugin-repo PR
- [ ] Record the approved SDK SHA-256 in package validation and verify both the source file and final ZIP copy
- [ ] Ensure release workflows package the committed file and contain no private SDK fetch, sync-script call, or `UM_UPDATER_REF`
- [ ] Confirm `.distignore` excludes `scripts/` so tooling does not ship in the release zip
- [ ] If the repo keeps `scripts/sync-um-updater.sh`, mark it as a manual maintainer helper for dedicated SDK-update PRs only

**Source of truth:** <https://github.com/dontpressthis/um-updater>

## 2) Release hygiene
- [ ] `.distignore` exists and is correct (no dev junk in zip)
- [ ] Tag/release flow is documented (GitHub Actions release workflow)

## 3) CI / QA basics
- [ ] Lint/tests (if applicable) run in CI
- [ ] Release workflow produces a clean installable zip

## Notes
- The shared updater file is guarded to prevent redeclare fatals when multiple MZV plugins are installed.
- Keep updater versions aligned across plugins to avoid “first-loaded wins” drift.
