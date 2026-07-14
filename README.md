# WinDroid data repo

Project-authored data fetched at runtime by the WinDroid app.

- `compat/compat_db.json` — the online compatibility database mapping an app → its known-good
  container profile (dxwrapper / box64 preset / wincomponents / env / driver). The app fetches this
  on a ~24h TTL (and via Settings → Update database), overlaying the bundled seed so new entries
  reach users without an APK rebuild.

Schema: `{"version": <int>, "apps": [ { "match": {...}, "profile": {...} }, ... ]}`.
Remote entries win over the bundled seed; keep `version` ≥ the shipped seed.
