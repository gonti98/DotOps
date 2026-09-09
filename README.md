# Dotops

Bootstrap, manage, and update your Linux system using [chezmoi].

> **Goal:** One command to go from a clean Linux installation to a fully
> configured, personalized system — reproducibly and securely.

## Quick start

Prerequisites:

- A clean Linux installation (currently only Arch)
- `curl`

```bash
sh -c "$(curl -fsSL https://get.chezmoi.io)" -- -b "$HOME/.local/bin" && \
  chezmoi init --apply https://github.com/gonti98/DotOps.git
```

> Never run unknown scripts without reading them.
> If you're not sure how something works, inspect the script or ask an LLM.

## ⚠️ Important warning

**Do not run this on a production or mature system.** This configuration will:

- Install/upgrade packages system‑wide via `sudo`
- Replace files in `~/.config/` and other locations
- Execute arbitrary commands from templates
- Potentially break existing configurations

**Always test on a VM or clean system first.** This tool is designed for reproducible setups, not incremental changes to existing environments.

## What problem does this solve?

Without Dotops, every new system requires:

- Manual package installation
- Recreating directory structures
- Copying and tweaking configs
- Restoring passwords, keys, and other private files

This is slow, error‑prone, and hard to reproduce.

Dotops turns this into:

```bash
clean Linux → curl this repo → automatic bootstrap → done
```

New package or config?

1. Test it manually
2. Add it to the managed list
3. Run `chezmoi apply`
4. Push changes for the future

### Core idea

Use [chezmoi] as a dotfile manager to:

- Manage `.config` files
- Manage tools from a single file list
- Run one‑time and on‑change scripts
- Encrypt sensitive data (passwords, keys, tokens)
- Keep everything version‑controlled and reproducible

## License

This project is licensed under the [MIT License].

[chezmoi]: https://www.chezmoi.io/
[MIT License]: LICENSE
