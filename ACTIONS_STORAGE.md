# GitHub Actions storage

EOPLite uses GitHub Actions to build the client, plugin hub, and Windows installer. The free plan includes **0.5 GB of Actions artifact storage** per month.

## If workflows fail with storage quota errors

1. Open **GitHub → Settings → Billing and plans → Plans and usage → Actions**
2. Under **Storage**, delete old **Artifacts** (or use **Manage storage** on each repo’s Actions tab)
3. Re-run only what you need:
   - **asngdajwk-plugins** → `Build EOPLite Plugin Hub` (workflow_dispatch)
   - **eop-lite** → `Sync upstream RuneLite` (workflow_dispatch, leave *force build* off unless you need a new client JAR)

## What was filling storage

- Daily upstream sync building a **~30 MB client JAR** + **Windows installer** every day
- Artifacts kept with long default retention
- Hub rebuilds triggered by version-sync commits

Workflows are now tuned to:

- Sync upstream **weekly** (not daily)
- Keep artifacts for **1 day** only
- Skip client/installer builds when already on the latest RuneLite tag
- Run hub version sync **manually** only

## Emergency: client updated but hub manifest version lags

If the client is on `1.12.32` but the hub still serves `1.12.31` manifests, run **Publish manifest version aliases** on the hub repo:

- Source: `1.12.31`
- Targets: `1.12.32` (add `1.12.31.1` if needed)

This republishes existing plugin JARs under the new version name without rebuilding all plugins.
