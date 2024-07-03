# Intro black

[Main site](https://black.readthedocs.io/en/stable/)

[Documentation](https://black.readthedocs.io/en/stable/)

## How to install black:

```bash
pip install black
```

## How to format code:

```bash
black file.py
```

## How to format code with custom settings:

```bash
black --line-length 120 file.py
```

## How to format code with custom settings and write to file:

```bash
black --line-length 120 file.py --write
```

## How to format code with custom settings and write to file with diff:

```bash
black --line-length 120 file.py --diff
```

## How to format code with custom settings and write to file with diff and verbose:

```bash
black --line-length 120 file.py --diff --verbose
```

## How to format code with custom settings and write to file with diff and verbose and check:

```bash
black --line-length 120 file.py --diff --verbose --check
```

## How to format code with custom settings and write to file with diff and verbose and check and exclude:

```bash
black --line-length 120 file.py --diff --verbose --check --exclude venv
```

## How to format code with custom settings and write to file with diff and verbose and check and exclude and include:

```bash
black --line-length 120 file.py --diff --verbose --check --exclude venv --include tests
```

## How to format code with custom settings and write to file with diff and verbose and check and exclude and include and quiet:

```bash
black --line-length 120 file.py --diff --verbose --check --exclude venv --include tests --quiet
```