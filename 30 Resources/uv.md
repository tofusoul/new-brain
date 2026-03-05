---
id: uv
aliases:
  - uv
tags: []
---

# uv

uv is an extremely fast Python package installer and resolver, written in Rust. It's designed as a drop-in replacement for `pip` and `pip-tools` workflows.

## Installation

You can install uv using pip:
```bash
pip install uv
```
Or via curl:
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

## Basic Usage

- **Create a virtual environment:**
  ```bash
  uv venv
  ```
  (This is much faster than `python -m venv`)

- **Activate the virtual environment:**
  ```bash
  source .venv/bin/activate
  ```

- **Install packages:**
  ```bash
  uv pip install <package_name>
  uv pip install -r requirements.txt
  ```

- **Generate a requirements.txt (lock file):**
  ```bash
  uv pip compile pyproject.toml -o requirements.txt
  uv pip compile requirements.in -o requirements.txt
  ```

- **Sync a virtual environment with a lock file:**
  ```bash
  uv pip sync requirements.txt
  ```
