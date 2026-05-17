# loc.sh — Manual

## Install

```sh
curl -fsSL https://raw.githubusercontent.com/arturcarvalho/loc.sh/main/install.sh | sh
```

The installer asks which file categories to exclude, then writes an executable
`loc.sh` in the current directory with the chosen exclusions baked in.

Re-run the installer at any time to regenerate `loc.sh` with different
exclusions. The installer refuses to overwrite an existing `loc.sh` unless you
pass `--force`:

```sh
curl -fsSL https://raw.githubusercontent.com/arturcarvalho/loc.sh/main/install.sh | sh -s -- --force
```

## Exclusion categories (asked at install)

| # | Category | Files |
|---|---|---|
| 1 | Markdown | `.md` |
| 2 | JSON | `.json`, `.json5` |
| 3 | Config | YAML, TOML, INI |
| 4 | Media / binary | images, audio, video, fonts, archives, pdf |
| 5 | Lock files | `package-lock.json`, `yarn.lock`, `pnpm-lock.yaml`, `Cargo.lock`, `Gemfile.lock`, `poetry.lock`, `composer.lock`, `go.sum` |

Each prompt defaults to **Yes** — press Enter to exclude, type `n` to keep.

## Always excluded

- `loc.sh` itself.
- Inside a git repo: only tracked files and untracked files not matched by
  `.gitignore` are counted (via `git ls-files -co --exclude-standard`).
  Uncommitted work is included; ignored noise (e.g. `node_modules`) is not.
- Outside a git repo, these directories are skipped:
  `node_modules`, `vendor`, `dist`, `build`, `target`, `.venv`, `venv`,
  `.next`, `.nuxt`, `.cache`, `coverage`, `.git`.

## Usage

```sh
./loc.sh
```

Counts lines of code in the current directory. No arguments.

## Requirements

- [`cloc`](https://github.com/AlDanial/cloc) — install with `brew install cloc`.
  `loc.sh` prints an install hint and exits 127 if `cloc` is missing.
