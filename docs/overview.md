# Overview

The repository is organized as a single Go module (`main.go` + `go.mod`) backed by a set
of focused subpackages. The `PACKAGES` variable in the `Makefile` enumerates the
formatted source tree.

## Top-Level Layout

- `main.go` / `main_test.go` — program entry point and smoke tests.
- `Makefile` — build, install, docker, test, benchmark, and formatting targets.
- `Dockerfile`, `Dockerfile.arm64` — container builds, including ARM64 cross builds.
- `bettercap.service` — systemd unit for running as a service.
- `release.py` — release tooling.
- `LICENSE.md`, `SECURITY.md` — GPL 3 license and security policy.

## Module Layout

- `core/` — shared primitives and runtime helpers used across packages.
- `session/` — interactive session, command parsing, and module lifecycle plumbing.
- `modules/` — concrete feature modules (WiFi, BLE, CAN-bus, HID, spoofers, proxies,
  sniffer, port scanner, REST API, web UI, etc.) that plug into the session.
- `network/` — host and interface discovery, OUI manufacturer lookup
  (`network/make_manuf.py` generates `network/manuf.go`), and address handling.
- `packets/` — packet builders and decoders.
- `routing/` — routing-table helpers.
- `firewall/` — platform firewall manipulation used by MITM features.
- `tls/` — TLS plumbing for HTTPS-level proxies and capture.
- `log/` — structured logging utilities.
- `js/` — JavaScript runtime bindings used by scriptable proxies and plugins.
- `caplets/` — bundled `.cap` scripts ("caplets") shipped at install time and copied
  into `${PREFIX}/share/bettercap/caplets/`.

## Entry Point

`main.go` wires the session, loads the configured modules, and dispatches commands.
`main_test.go` provides startup-level coverage.
