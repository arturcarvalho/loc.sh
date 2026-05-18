# loc.sh

One-shot installer that drops a `loc.sh` script into the current directory.
Running `./loc.sh` prints lines of code for the project, via
[`cloc`](https://github.com/AlDanial/cloc).

## Install

```sh
curl -fsSL https://github.com/arturcarvalho/loc.sh/raw/main/install.sh | sh
```

The installer asks which categories to exclude (markdown, JSON, config files,
media/binary, lock files, shell scripts) and lets you pick top-level folders
to skip, then writes an executable `loc.sh` with those choices baked in.

## Use

```sh
./loc.sh
```

Requires `cloc` (`brew install cloc` on macOS). `loc.sh` prints an install hint
and exits if `cloc` is missing.

See [MANUAL.md](MANUAL.md) for full details.
