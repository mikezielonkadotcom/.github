# New Plugin Checklist (mikezielonkadotcom)

This is the default checklist for *any new WordPress plugin repo* we create under the `mikezielonkadotcom` GitHub org.

## 1) Shared Update Machine updater (required)
- [ ] Add build-time sync script: `scripts/sync-um-updater.sh`
- [ ] Ensure release workflow runs sync step *before* packaging the zip
- [ ] Pin updater ref (deterministic): `UM_UPDATER_REF=v1.0.0` (or latest tag)
- [ ] Confirm `.distignore` excludes `scripts/` so tooling does not ship in the release zip
- [ ] Do **not** manually edit `includes/um-updater.php` — it is generated at build time

**Source of truth:** <https://github.com/mikezielonkadotcom/um-updater>

## 2) Release hygiene
- [ ] `.distignore` exists and is correct (no dev junk in zip)
- [ ] Tag/release flow is documented (GitHub Actions release workflow)

## 3) CI / QA basics
- [ ] Lint/tests (if applicable) run in CI
- [ ] Release workflow produces a clean installable zip

## Notes
- The shared updater file is guarded to prevent redeclare fatals when multiple MZV plugins are installed.
- Keep updater versions aligned across plugins to avoid “first-loaded wins” drift.
