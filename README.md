# Hash Identifier

Identify the algorithm behind a hash string by its prefix, length, and character set — the first move in any password-cracking workflow.

## Overview

The Hash Identifier is an educational cryptography tool designed to demonstrate hash algorithm identification techniques. This tool helps security professionals and developers understand hash format recognition, which is the first step in any password-cracking or security analysis workflow. The identification is performed entirely offline with no network access required.

**Important:** This tool is intended solely for educational and educational purposes. Hash algorithm identification is a reconnaissance step only and should never be used as the sole basis for security decisions. This tool is for learning about hash formats and understanding the identification process in cryptography.

## Features

### Hash Format Identification

- **~30 hash formats** identified by distinctive prefixes:
  - `$2b$`, `$2a$`, `$2y$` - bcrypt variants
  - `$argon2id$` - Argon2id (modern standard)
  - `$apr1$` - Apache MD5-crypt (htpasswd -m)
  - `$1$` - MD5-crypt
  - `{SSHA}` - Salted SHA hash
  - And many more

### Hex Hash Identification

- **Common hash lengths** identified by character count:
  - **MD5**: 32 hex characters
  - **SHA-1**: 40 hex characters
  - **SHA-256**: 64 hex characters
  - **SHA-512**: 128 hex characters
  - **NTLM**: 32 hex characters (specific format)
  - **MD4**: 32 hex characters
  - **RIPEMD**: 32 hex characters
  - **BLAKE2**: Various lengths
  - **SHA-3**: Various lengths

### Input Type Detection

- **MySQL5 format**: Recognized by `*` prefix followed by 40 uppercase hex chars
- **NetNTLMv1/v2**: Traditional 13-char DES crypt recognition
- **Non-hash input detection**: Identifies JWTs, base64 blobs, and other non-hash inputs
- **JWT detection**: Leading `eyJ` indicates base64-encoded JSON Web Token

### Confidence Scoring

- **high / medium / low confidence** rankings for each guess
- **One-line reason** for every guess explaining the identification logic
- **Ranked candidates** sorted by likelihood

### Rich Output

- **Colored output table**: Visual display of identification results
- **Clean exit codes**: For shell scripting and automation
- **Pure-function core**: No network, no filesystem, no global state, instant runtime

### Educational Design

- **Foundations tier**: Built for someone who has never written Python before
- **Heavily commented source code**: Teaching aid with explanations
- **learn/ folder**: Explains every concept from zero
- **Single readable file**: Entire tool is one file for easy understanding

## Installation

### Requirements

- **Python 3.14+**: The install script will check version compatibility
- **uv**: Modern Python package manager (auto-installed by `./install.sh`)
- **just**: Command runner (auto-installed by `./install.sh`)

### No Compilers or System Libraries Required

- Pure Python implementation
- No system libraries needed
- No network access required
- Project is one Python file plus tests

### Install Script

```bash
# Run the install script (auto-installs dependencies)
./install.sh

# Or using uv and just directly
uv tool install hash-identifier
```

### Verify Installation

```bash
hash-identifier --help
just
# Lists available recipes:
# just test       # run pytest (30+ tests, runs in under a second)
# just lint       # ruff + mypy --strict + pylint
# just format     # yapf
# just run -- <h> # identify a hash
```

## Quick Start

```bash
# Identify a hash
just run -- 5f4dcc3b5aa765d61d8327deb882cf99
# ✔ MD5 (medium) — 32 hex chars, most likely candidate at this length

# Or using uv
uv run hash_identifier 5f4dcc3b5aa765d61d8327deb882cf99
```

### Using just as Command Runner

Type `just` to see all available recipes:

| Recipe | Description |
|--------|-------------|
| `just` | List available recipes |
| `just test` | Run pytest (30+ tests, runs in under a second) |
| `just lint` | Run ruff + mypy --strict + pylint |
| `just format` | Format with yapf |
| `just run -- <h>` | Identify a hash by passing the hash value |

## Commands Reference

### `just run -- 5f4dcc3b5aa765d61d8327deb882cf99`

Identify the algorithm behind the hash string.

Output: `✔ MD5 (medium) — 32 hex chars, most likely candidate at this length`

### `just test`

Run the pytest test suite (30+ tests, runs in under a second).

### `just lint`

Run code quality checks (ruff + mypy --strict + pylint).

### `just format`

Format the code with yapf.

### `just run -- <h>`

Identify a hash by passing the hash value as an argument.

## Learn

This project includes step-by-step learning materials covering security theory, architecture, and implementation — written for someone who has never touched Python before.

| Module | Topic |
|--------|-------|
| **00 - Overview** | Quick start, prerequisites, common problems |
| **01 - Concepts** | What hashes are, real-world breaches, the three identification signals |
| **02 - Architecture** | Three-layer architecture, six-step decision pipeline, data-driven design |
| **03 - Implementation** | Line-by-line walkthrough — every Python feature explained when first encountered |
| **04 - Challenges** | Five tiers of extension ideas, from adding a prefix rule to building an ML classifier |

## Legal and Ethical Notes

### Educational Use Only

This tool is designed for educational purposes. Key principles:

- **Hash identification is reconnaissance only**: Should not be used as sole basis for security decisions
- **Only identify hashes** from materials you own or have permission to analyze
- **Never use identification results** for actual security enforcement without additional verification
- **Understand the identification process** as part of learning cryptography

### Learning Value

Understanding hash identification helps students:

- Recognize different hash algorithm formats
- Learn about password storage schemes
- Understand the first step in password-cracking workflows
- Appreciate why multiple verification steps are needed in security analysis

### Legal Compliance

- Use only on hash values you own or have permission to analyze
- Educational purpose only - do not use for actual security enforcement
- Follow institutional policies regarding cryptography tools

### Responsible Use

- Always combine identification with other security analysis
- Never make security decisions based solely on hash identification
- Report any misuse of the tool to appropriate authorities

## License

AGPL 3.0 - See the LICENSE file for full terms and conditions. This project is provided "as is" without warranty of any kind, either express or implied. AGPL requires that source code be made available to users over a network.