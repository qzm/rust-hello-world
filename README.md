# rust-hello-world

[![Release](https://github.com/qzm/rust-hello-world/actions/workflows/release.yml/badge.svg)](https://github.com/qzm/rust-hello-world/actions/workflows/release.yml)
[![GitHub Release](https://img.shields.io/github/v/release/qzm/rust-hello-world)](https://github.com/qzm/rust-hello-world/releases/latest)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

A minimal Rust project with cross-platform CI/CD pipeline, building and releasing binaries for **3 platforms x 7 targets**.

## Quick Start

### From Source

```bash
git clone https://github.com/qzm/rust-hello-world.git
cd rust-hello-world
cargo run
```

### From Release

Download the pre-built binary for your platform from the [Releases](https://github.com/qzm/rust-hello-world/releases/latest) page.

**Linux / macOS:**

```bash
tar xzf rust-hello-world-v*-<target>.tar.gz
./rust-hello-world
```

**Windows:**

Extract the `.zip` file and run `rust-hello-world.exe`.

## Supported Platforms

| Platform | Architecture | Target Triple |
|----------|-------------|---------------|
| Linux    | x86_64      | `x86_64-unknown-linux-gnu` |
| Linux    | ARM64       | `aarch64-unknown-linux-gnu` |
| Linux    | ARMv7       | `armv7-unknown-linux-gnueabihf` |
| macOS    | x86_64 (Intel) | `x86_64-apple-darwin` |
| macOS    | ARM64 (Apple Silicon) | `aarch64-apple-darwin` |
| Windows  | x86_64      | `x86_64-pc-windows-msvc` |
| Windows  | ARM64       | `aarch64-pc-windows-msvc` |

## Build

### Development

```bash
cargo build
```

### Release

```bash
cargo build --release
```

The optimized binary will be at `target/release/rust-hello-world`.

## Release Process

Pushing a version tag triggers the GitHub Actions pipeline to build all platform binaries and publish a GitHub Release:

```bash
git tag v0.1.0
git push origin v0.1.0
```

The release will include:

- Pre-built binaries for all 7 targets (`.tar.gz` / `.zip`)
- Source code archives with version prefix (`-source.tar.gz` / `-source.zip`)

## Project Structure

```
rust-hello-world/
├── .github/
│   └── workflows/
│       └── release.yml    # Cross-platform CI/CD pipeline
├── src/
│   └── main.rs            # Entry point
├── Cargo.toml             # Package manifest
├── Cargo.lock             # Dependency lock file
└── README.md
```

## Requirements

- [Rust](https://www.rust-lang.org/tools/install) 1.85+ (Edition 2024)

## License

MIT
