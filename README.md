# movebin-vint

Moves a binary to `/usr/local/bin/`, making it accessible system-wide. Rewrite of [movebin-zig](https://github.com/tacheraSasi/movebin-zig) in VintLang.

## Usage

```bash
sudo vint main.vint <binary_path> [OPTIONS]
```

## Options

| Flag | Description |
|------|-------------|
| `-o`, `--output <name>` | Set a custom binary name (default: basename of source) |
| `-f`, `--force` | Force overwrite without prompting |
| `--no-backup` | Skip backup creation before overwriting |
| `-h`, `--help` | Show help message |
| `-v`, `--version` | Show version information |

## Examples

```bash
# Install a binary
sudo vint main.vint my-tool

# Install with a custom name
sudo vint main.vint my-tool -o custom

# Force overwrite with custom name
sudo vint main.vint my-tool -o tool -f

# Skip backup on overwrite
sudo vint main.vint my-tool --no-backup
```

## Features

- Copies binary to `/usr/local/bin/`
- Sets executable permissions (`chmod 755`)
- Optional custom output name via `-o`
- **Interactive overwrite confirmation** (skip with `-f`)
- **Timestamped backups** in `/usr/local/bin/.movebin_backups/` (skip with `--no-backup`)
- Full CLI flag support (`-h`, `-v`, `-f`, `-o`, `--no-backup`)
- Type-annotated VintLang code using `let x: type = value`
- Multi-file project with `modules/file_ops.vint` package

## Project Structure

```
movebin-vint/
  main.vint              # Entry point with main() and CLI flag parsing
  modules/
    file_ops.vint         # File operations package (copy, backup, chmod)
  vintconfig.json
  README.md
```

## Requirements

- VintLang interpreter (v0.1.0+ with type system)
- macOS/Linux (uses `/usr/local/bin/`)
- Write access to `/usr/local/bin/` (run with `sudo`)
