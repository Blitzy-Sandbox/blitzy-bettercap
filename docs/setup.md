# Setup

`bettercap` is a Go project. The repository ships a `Makefile`, a `Dockerfile`, and an
`arm64` Docker build for installation in a variety of environments.

## Prerequisites

- A working Go toolchain (`go`) on `PATH`.
- Python 3 (used by `network/make_manuf.py` to generate the OUI manufacturer table during
  the `resources` build step).
- `libpcap` and the platform-specific dependencies required for raw packet capture and
  wireless frame injection.

## Build from Source

    make build

This runs the `resources` step (regenerating `network/manuf.go`) and then invokes
`go build -o bettercap .`.

For a build with the Go race detector enabled:

    make build_with_race_detector

## Install

After building, install the binary and bundled caplets:

    sudo make install

This copies the `bettercap` binary to `${PREFIX}/bin` (default `/usr/local/bin`) and
provisions the `caplets/` directory under `${PREFIX}/share/bettercap/`.

A `bettercap.service` unit is included in the repository root for running `bettercap` as
a systemd service.

## Docker

Build a local image:

    make docker

A separate `Dockerfile.arm64` and a `make build-arm64` target are provided for cross
building an `arm64` binary via Docker BuildKit.

## Tests

    make test

Runs the full Go test suite with atomic coverage instrumentation and writes a
`cover.out` profile. `make html_coverage` renders the profile as HTML, and
`make benchmark` runs the Go benchmarks.
