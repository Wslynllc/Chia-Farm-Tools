# Agents in Chia-Farm-Tools

Read `README.md` and the README in the directory you are changing before editing anything.

- Shared standards win: `Wslynllc/project-standards` (`README.md`, `Owner approval.md`, `Delivery gates.md`).
  `CI and runners.md` applies only if a workflow is added; no Proxmox or VM page applies. This file only adds this
  repository's values.
- This is a fork of `Valeri4n/Chia-Farm-Tools`. Upstream has no `AGENTS.md` or `CLAUDE.md`, so this file stands alone.
  Keep edits to existing scripts and READMEs small and targeted (no reformatting, renaming or moving) so upstream
  syncs stay easy. Upstream also has `archive/`, `data/` and `monitoring/`, which this fork lacks; why is unknown.
- Merging deploys nothing. There is no workflow, Makefile, deploy flag or stop switch. The scripts are copied to and
  run by hand on Linux farm hosts; the Windows files under `Support/Windows` and `plotting/windows` likewise.
- Owner tap (`rkroelin-yes`) is required only for `/.github/`, as `.github/CODEOWNERS` says. Every other path merges
  after an independent agent review. Do not add or widen CODEOWNERS in an ordinary change.
- Offline check: none exists (no tests, no CI). Before a push run `git diff --check` and
  `for f in $(git ls-files '*.sh'); do bash -n "$f" || echo "FAIL $f"; done`. That is syntax only, not an adopted check.
- Never run these scripts as part of agent work: they act on real disks, wallets and the network. Read them and
  `bash -n` them. The destructive ones are `storage-management/format_drive.sh` (`wipefs`, `mkfs`), `fix_drives.sh`
  (`umount`, `fsck -y`, then `dmesg -T -c` into `/home/harvest/logs`), `eject_drive.sh` (`umount`) and
  `plot_purge.sh` (`rm` of plot files).
- `chia-tools/` scripts call the public `coingecko.com` and `alltheblocks.net` pages, and parse their HTML, which
  breaks when those sites change. `wallet_transaction_capture.sh` writes `*-txn-wallet_id_*.csv` files into the current
  directory. There is no `.gitignore`: never commit that output, wallet data or addresses beyond the one already in
  `README.md` (the upstream owner's donation address; leave it).
- No build step and no generated files.
- Before a push: `git remote -v`, then `trufflehog git file://$PWD --no-update --no-verification` must find nothing.

## Where context lives

- `chia-tools/` status and transaction scripts; `storage-management/` drive, plot mover and plot purge scripts
  (`storage-management/archive/` holds old versions); `ubuntu-build/` Ubuntu install steps; `chia-commands/` one-line `chia rpc`
  queries; `Support/` how-tos; `plotting/windows/` Windows plotting commands.
- Each directory's `README.md` documents its scripts. Keep a script's entry there in step with the script.
- Settings for this repository (an `owner-gate` ruleset) are recorded in `Wslynllc/project-standards`, `Gates/README.md`.
- Kanban: no board for this repo (`hermes kanban boards list`). Related repos: none are referenced in the tree.
