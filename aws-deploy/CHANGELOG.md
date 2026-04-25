# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.5.0] - 2026-04-25
### Updated
- ベースイメージを `ubuntu:22.04` から `debian:trixie` に変更。
- terraformのバージョンを1.14.9に更新。
- ansibleのバージョンを13.6.0に更新。
- AWS CLIのバージョンを1.44.86に更新。

## [0.4.0] - 2026-03-30
### Updated
- terraformのバージョンを1.14.8に更新。
- ansibleのバージョンを13.5.0に更新。
- AWS CLIのバージョンを1.44.68に更新。
- PyYAMLのバージョンを6.0.3に更新。

### Fixed
- ENVの記法を推奨フォーマット(key=value)に統一。
- ansibleの重複インストール行を削除。

## [0.3.0] - 2023-11-24
### Updated
- terraformのバージョンを1.6.4に更新。
- ansibleのバージョンを9.0.1に更新。

## [0.2.0] - 2023-06-17
### Updated
- terraformのバージョンを1.4.6に更新。
- ansibleのバージョンを8.0.0に更新。

## [0.1.1] - 2023-02-12
### Updated
- バージョンアップデート。AWS CLIのバージョン固定。

## [0.1.0] - 2023-01-02
### Added
- AWS用デプロイイメージ。