# Bravo Crew OT

Independent GitHub Pages deployment of the existing Bravo Crew application.

Website: https://morrissey529-ship-it.github.io/Bravoot/

## Preserved application

The production files were recovered from https://fused-network-m83ez7f.shipstatic.com on November 6, 2026. That deployment originated from Alphaot commit `6d7f29a739ff2d4f0af1a9218b55940b2cd8b88a`, with Bravo branding, opposite workdays, and Bravo RPC remapping already applied.

All four tabs, the existing login, calendar, rotations, and Bravo RPC behavior are retained. Styles and icons previously loaded from Alphaot are now included here. Asset filenames use the Bravo prefix; internal DOM identifiers retain their original names for compatibility. The Seniority button is labeled **Shared Seniority**, as requested, and intentionally opens the existing shared page.

## Data and permissions

Bravo uses the existing Supabase project and its `bravo` and `bravo_private` schemas. No data or database definitions were migrated or changed. Crew operations call `bravo_*` RPCs. The publishable browser key is intentionally public; no privileged service key is included.

**Admin and Editor roles are still shared with Alpha.** Both applications use `public.profiles.role` and `public.current_user_role()`. Promoting someone here also grants the corresponding Alpha access. Moving hosting does not isolate permissions. Shared seniority and account profiles are intentional exceptions to crew data isolation.

Separating permissions requires a separately scoped Bravo role store, corresponding checks in every Bravo RPC/policy, and replacement of the profile-management UI. Existing shared privileges must be reviewed individually; do not demote shared accounts without confirming their Alpha access requirements.

Users sign in again at the new origin with their existing credentials. Password login is unchanged. Email confirmation delivery and a successful authenticated session require user acceptance testing; no passwords or sessions are copied between sites.

## Deployment

GitHub Pages publishes the `main` branch root. `.nojekyll` keeps the buildless HTML, CSS, and JavaScript intact. All app assets are relative to this repository's path. The old ShipStatic deployment is retained as a rollback option.
