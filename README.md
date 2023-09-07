開発用イメージを管理しています。mainブランチにpushしたときにgithub actionが実行されます。

# 追加方法
イメージごとのディレクトリを作成します。最低限DockerfileとCHANGELOG.mdが必要になります。
次にworkflowsにactions用のymlファイルを使用します。

## Dockerfile
省略

## CHANGELOG.md
https://keepachangelog.com/en/1.0.0/にしたがって記述します。

以下に例を示します。
```
# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.1.0] - 2023-01-02
### Added
- ionic 開発用イメージ。
```

## docker-{actions}.yml
{actions}の部分は追加したデイレクトリと合わせてください。
```
name: docker.{actions}

on:
  push:
    branches: 
      - main
    paths:
      - .github/workflows/docker-{actions}.yml
      - {actions}/**

env:
  # Format
  REGISTRY: ghcr.io
  REPOSITORY: ${{ github.repository }}
  IMAGE: {actions}


jobs:
  build:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      packages: write
      id-token: write
    defaults:
      run:
        working-directory: {actions}

    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      # https://github.com/docker/setup-buildx-action
      - name: Setup Docker buildx
        uses: docker/setup-buildx-action@v2
      # https://github.com/docker/setup-qemu-action
      - name: Set up QEMU
        uses: docker/setup-qemu-action@v2

      # Login against a Docker registry except on PR
      # https://github.com/docker/login-action
      - name: Log into registry ${{ env.REGISTRY }}
        uses: docker/login-action@v2
        with:
          registry: ${{ env.REGISTRY }}
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}

      - name: Download release tool
        run: |
          wget -q https://github.com/naughty-ghost/release-tool/releases/download/1.0.0/release-tool.zip -O release-tool.zip
          unzip release-tool.zip

      - name: Extract Docker metadata
        id: meta
        run: echo "tag=ghcr.io/$REPOSITORY-$IMAGE:$(./release-tool | tr -d '\n')" >> $GITHUB_OUTPUT

      - name: Build and push Docker image
        run: |
          docker buildx create --use
          docker buildx build \
            --platform linux/amd64,linux/arm64 \
            --tag ${{ steps.meta.outputs.tag }} \
            --push .

```