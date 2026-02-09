# rust-hello-world

[![Release](https://github.com/qzm/rust-hello-world/actions/workflows/release.yml/badge.svg)](https://github.com/qzm/rust-hello-world/actions/workflows/release.yml)
[![GitHub Release](https://img.shields.io/github/v/release/qzm/rust-hello-world)](https://github.com/qzm/rust-hello-world/releases/latest)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

A minimal Rust project with cross-platform CI/CD pipeline, building and releasing binaries for **9 platforms x 33 targets**.

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

**WebAssembly:**

```bash
tar xzf rust-hello-world-v*-wasm32-wasip1.tar.gz
wasmtime rust-hello-world.wasm
```

## Supported Platforms

### Linux (glibc)

| Architecture | Target Triple |
|-------------|---------------|
| x86_64 | `x86_64-unknown-linux-gnu` |
| i686 (32-bit) | `i686-unknown-linux-gnu` |
| ARM64 | `aarch64-unknown-linux-gnu` |
| ARMv7 | `armv7-unknown-linux-gnueabihf` |
| ARMv6 | `arm-unknown-linux-gnueabihf` |
| ARMv7 NEON | `thumbv7neon-unknown-linux-gnueabihf` |
| PowerPC64 LE | `powerpc64le-unknown-linux-gnu` |
| s390x | `s390x-unknown-linux-gnu` |
| RISC-V 64 | `riscv64gc-unknown-linux-gnu` |
| SPARC64 | `sparc64-unknown-linux-gnu` |
| MIPS (big-endian) | `mips-unknown-linux-gnu` |
| MIPS (little-endian) | `mipsel-unknown-linux-gnu` |
| MIPS64 (big-endian) | `mips64-unknown-linux-gnuabi64` |
| MIPS64 (little-endian) | `mips64el-unknown-linux-gnuabi64` |
| LoongArch64 | `loongarch64-unknown-linux-gnu` |

### Linux (musl, static)

| Architecture | Target Triple |
|-------------|---------------|
| x86_64 | `x86_64-unknown-linux-musl` |
| ARM64 | `aarch64-unknown-linux-musl` |
| ARMv7 | `armv7-unknown-linux-musleabihf` |

### macOS

| Architecture | Target Triple |
|-------------|---------------|
| x86_64 (Intel) | `x86_64-apple-darwin` |
| ARM64 (Apple Silicon) | `aarch64-apple-darwin` |

### iOS

| Architecture | Target Triple |
|-------------|---------------|
| ARM64 | `aarch64-apple-ios` |

### Windows

| Architecture | Target Triple | Toolchain |
|-------------|---------------|-----------|
| x86_64 | `x86_64-pc-windows-msvc` | MSVC |
| i686 (32-bit) | `i686-pc-windows-msvc` | MSVC |
| ARM64 | `aarch64-pc-windows-msvc` | MSVC |
| x86_64 | `x86_64-pc-windows-gnu` | GNU |

### BSD

| OS | Architecture | Target Triple |
|----|-------------|---------------|
| FreeBSD | x86_64 | `x86_64-unknown-freebsd` |
| NetBSD | x86_64 | `x86_64-unknown-netbsd` |

### illumos (Solaris derivative)

| Architecture | Target Triple |
|-------------|---------------|
| x86_64 | `x86_64-unknown-illumos` |

### Android

| Architecture | Target Triple |
|-------------|---------------|
| ARM64 | `aarch64-linux-android` |
| x86_64 | `x86_64-linux-android` |

### WebAssembly

| Runtime | Target Triple |
|---------|---------------|
| WASI | `wasm32-wasip1` |

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
git tag v0.2.0
git push origin v0.2.0
```

The release will include:

- Pre-built binaries for all 33 targets (`.tar.gz` / `.zip`)
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
