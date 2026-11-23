# Changelog

All notable changes to this tap are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and commit messages follow [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/).

The tap itself is not versioned: there are no tags or releases. Each cask carries the version of
the tool it installs, and GoReleaser rewrites the cask on every tool release.

## [Unreleased]

### Added

- Backstage `catalog-info.yaml` and technology tags.

### Changed

- `kube-node-viewer` cask follows the tool's releases, from v0.8.1 (2026-11-02) to v0.17.0
  (2026-11-18), each update committed by GoReleaser from the
  [kube-node-viewer release](https://github.com/StaffOps/kube-node-viewer/releases).

[Unreleased]: https://github.com/StaffOps/homebrew-tap/commits/main
