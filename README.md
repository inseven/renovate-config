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
    "local>inseven/renovate-config"
  ]
}
```

If package management depends on local submodules, it may be necessary to instruct Renovate to check these out to ensure lock files can be updated. For example,

```yaml
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": [
    "local>inseven/renovate-config"
  ],
  "cloneSubmodules": true,
  "cloneSubmodulesFilter": ["docs/_theme"]
}
```

This ensures the Jekyll theme used by [Thoughts](https://github.com/inseven/thoughts) and other projects is cloned before attempting to update lock files.

### Swift Ranges

Renovate doesn't currently seem to handle exclusive ranges correctly, so inclusive ranges should be used:

```swift
.package(url: "https://github.com/apple/swift-crypto.git", "1.0.0" ... "5.0.1"),
```

## Development

Install dependencies:

```sh
mise trust
mise install
```

Validate the configuration:

```sh
renovate-config-validator default.json
```

## License

Licensed under the MIT License (see [LICENSE](LICENSE)).
