# asngdajwk-plugins

EOPLite plugin hub index. The GitHub Action builds plugins listed under `plugins/`.

Each plugin is a **file with no extension** in `plugins/`, for example `plugins/my-bank-plugin`:

```text
repository=https://github.com/Samadfero/my-bank-plugin.git
commit=full_40_character_git_commit_hash
```

Do not put `.gitkeep` or other random files in `plugins/` — the builder reads every file there.
