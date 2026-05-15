# blitzy-bettercap

`bettercap` is a powerful, extensible, and portable framework written in Go that provides
security researchers, red teamers, and reverse engineers with an all-in-one solution for
performing reconnaissance and security testing against a wide range of network surfaces.

## Legitimate Purpose

This tool is intended for authorized network analysis, defensive research, and security
testing. Typical use cases include:

- Auditing the security posture of WiFi, Bluetooth Low Energy, CAN-bus, HID, and Ethernet
  networks that you own or have explicit permission to test.
- Investigating protocol behavior during incident response or vulnerability research.
- Teaching and learning network protocol internals in controlled lab environments.

Operators are responsible for ensuring all usage complies with applicable laws, internal
policies, and the rules of engagement of any authorized assessment.

## Capability Areas

- **WiFi**: network scanning, deauthentication, clientless PMKID association testing, and
  automatic WPA/WPA2/WPA3 handshake capture.
- **Bluetooth Low Energy**: device scanning, characteristic enumeration, reading and
  writing.
- **2.4GHz HID / MouseJacking**: scanning and over-the-air HID frame injection with
  DuckyScript support.
- **CAN-bus / DBC**: decoding, injection, and fuzzing of automotive bus frames.
- **IP recon**: passive and active probing of IPv4 and IPv6 hosts.
- **MITM spoofers**: ARP, DNS, NDP, and DHCPv6 spoofers for IPv4 and IPv6 networks.
- **Proxies**: packet-, TCP-, and HTTP/HTTPS-level proxies, scriptable with JavaScript
  plugins.
- **Sniffer**: credential harvesting and protocol fuzzing pipeline.
- **Port scanner**: high-speed scanning.
- **REST API & Web UI**: orchestration via a REST API with WebSocket events and a web
  interface.

## License

Released under the GPL 3 license.
