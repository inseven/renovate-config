# Renovate Configuration

Shared Renovate configuration for my personal projects.

## Overview

This departs fairly significantly from the off-the-shelf Renovate configuration in order to produce PRs that follow the standard naming conventions I've settled on for my projects. Specifically, PR titles:

- follow [Conventional Commits](https://www.conventionalcommits.org) with sentence case
- lean heavily towards `fix` to ensure code changes are picked up by [Semantic Versioning](https://semver.org)
- add per-package manager emoji (🦀, ⚙️, 🔨, etc)
- itemize changed components

For example, using this configuration, PR titles look something like this:

```
fix: 🦀 Update Rust dependencies (ctrlc, rand, serde, serde_json)
```

In addition, the configuration disables the Dependency Dashboard.

## Usage

Create `renovate.json` in the root of your project:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": [
    "local>jbmorley/renovate-config"
  ]
}
```

