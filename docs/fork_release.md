# Mojackhak Fork Release Contract

This document defines the packaging and release policy for the Mojackhak fork of Anipose.

## Scope

This fork keeps the upstream distribution and import names:

- distribution name: `anipose`
- import name: `anipose`

This repository must remain installation-compatible with downstream code that expects the upstream package name.

## Fork Identity

Required package metadata:

- `url` points to `https://github.com/Mojackhak/anipose`
- project URLs include both the fork repository and the upstream repository
- package description explicitly identifies this build as the Mojackhak fork

## Versioning

Use PEP 440 compatible post releases for fork packaging:

- upstream base: `1.1.25`
- first fork release: `1.1.25.post1`
- later fork releases: `1.1.25.postN`

## Tags

Use annotated tags for release points.

Tag format:

- `mojackhak-anipose-v<version>`

Example:

- `mojackhak-anipose-v1.1.25.post1`

## Dependency Policy

The managed environment must install the maintained Mojackhak `aniposelib` wheel alongside `anipose`.

Keep `install_requires` broad enough for packaging compatibility:

- `aniposelib>=0.7.12`

## Release Artifacts

Each release tag must produce:

- source distribution
- wheel
- GitHub Release entry with uploaded artifacts

Downstream repositories should install released wheels rather than Git commits once release artifacts exist.

## Validation

Each release build must validate:

- `python -m build`
- `python -m twine check dist/*`
- `import anipose`
