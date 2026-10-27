# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.2.0] - 2026-10-27
### Changed
- Goのダウンロード先をビルド環境のアーキテクチャ（amd64 / arm64）に応じて切り替えるよう変更。
- Goを1.26.2から1.27.3に更新。
- airのバージョンをv1.67.4に固定（従来は`latest`）。

## [0.1.0] - 2026-04-25
### Added
- golang開発用イメージ（debian:trixie ベース、Go 1.26.2）。
