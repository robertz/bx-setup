
## bx-setup

Lightweight helper to ensure required BoxLang modules are installed for your project. Define dependencies in `requirements.txt`, then run a single command to install anything missing.

### Prerequisites

- BoxLang runtime/CLI available on your PATH.
- The BoxLang module installer command `install-bx-module` available (used internally).

### Quick Start

1) Create a `requirements.txt` in your project root:

```text
# One module per line
bx-jsoup
bx-markdown@1.0.0   ## require >= 1.0.0
bx-yaml             ## latest available

# Blank lines and inline comments after `##` are ignored
```

2) From the project root, run:

```bash
boxlang setup.bx
```

The script lists installed modules, compares them to your requirements, and installs any that are missing or below the required minimum version.

### How It Works

- Reads `requirements.txt`, ignoring blank lines and inline comments after `#`.
- Accepts either:
  - `module-name` (installs latest available)
  - `module-name@x.y.z` (requires at least `x.y.z`)
- Detects installed modules via `install-bx-module --list` and compares versions numerically (build metadata like `+1` is ignored).
- Installs only what’s missing or below the minimum; otherwise does nothing.

### Requirements.txt Format

- One dependency per line.
- Optional minimum version using `@` (e.g., `bx-markdown@1.0.0` means
  the installed version must be `>= 1.0.0`).
- Inline comments use `##` and may follow an entry on the same line.
- Blank lines are allowed.

### Dry Run

- Preview actions without installing: `boxlang setup.bx --dry-run`

### Troubleshooting

- Command not found: If `install-bx-module` is unavailable, ensure the BoxLang CLI and necessary commands are installed and on your PATH.
- Network/permissions: Installing modules requires network access and sufficient permissions.
- File errors: If you see “Error reading requirements”, confirm `requirements.txt` exists at the project root and is readable.

### Notes

- Version comparison ignores build metadata after `+` when deciding if a module is up to date.
- Version ranges are not supported; use either no version (latest) or a minimum `x.y.z` via `@`.
