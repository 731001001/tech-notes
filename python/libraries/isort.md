# Intro isort

## docs

- [Main site](https://pycqa.github.io/isort/)
- [Documentation](https://pycqa.github.io/isort/docs/)
- [Configuration](https://pycqa.github.io/isort/docs/configuration/options/)

## how to use

### Install

```bash
pip install isort
```

### Basic usage

```bash
isort file.py
```

### Configuration

Create a file named `pyproject.toml` in the root of your project with the following content:

```toml
[tool.isort]
profile = "black"
```

### Sort imports

```bash
isort file.py
```

### Check if imports are sorted

```bash
isort --check-only file.py
```

### Sort all files in a directory

```bash
isort .
```

### Sort all files in a directory recursively

```bash
isort . --recursive
```

### Sort all files in a directory recursively and check if imports are sorted

```bash
isort . --recursive --check-only
```

### Sort all files in a directory recursively and apply changes

```bash
isort . --recursive --apply
```