# Private plugin repos (EOPLite hub)

Each plugin stays **private** on GitHub. The hub repo `asngdajwk-plugins` is public, but only **signed JARs** are published to Pages — not your source.

## Required secret: `REPO_CREDS`

GitHub Actions must clone:

- `Samadfero/eoplite-clan-indicators` (private)
- `Samadfero/eoplite-plus-one-highlighter` (private)
- `Samadfero/clan-hall-exporter` (private)
- `Samadfero/eoplite-profiles` (private)

`GITHUB_TOKEN` alone **cannot** read other private repos.

### Set or refresh `REPO_CREDS`

1. GitHub → **Settings** → **Developer settings** → **Personal access tokens**
2. Create a **classic** token with scope **`repo`** (simplest — covers all your private repos, including new ones)
3. `asngdajwk-plugins` → **Settings** → **Secrets and variables** → **Actions** → **REPO_CREDS**
4. Value: `Samadfero:ghp_PASTE_TOKEN_HERE` (username, colon, token — no spaces)

If you use a **fine-grained** token instead, you must add **each** plugin repo manually. When you create a new plugin repo (e.g. `clan-hall-exporter`, `eoplite-profiles`), add it to the token or the hub build will fail.

### After updating the secret

**Actions** → **Build EOPLite Plugin Hub** → **Run workflow**

When green, restart EOPLite → **EOPLite Plugins** → install **Clan Hall Exporter**.
