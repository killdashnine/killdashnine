# Matthias van der Vlies

Telecom infrastructure engineer. Carrier-grade signalling and media in Rust:
SS7/SIGTRAN, IMS/VoLTE, SIP, SMPP.

The public work is one protocol per crate, each written against its own spec, plus
the runtime that ties them together.

## SS7 and SIGTRAN

| Crate | What it does | Spec | |
|---|---|---|---|
| [mtp2](https://github.com/Real-Time-Telecom-B-V/mtp2) | signal-unit framing, link state machine | ITU-T Q.703 | [![v](https://img.shields.io/crates/v/mtp2.svg?logo=rust)](https://crates.io/crates/mtp2) ![d](https://img.shields.io/crates/d/mtp2.svg) |
| [m2pa](https://github.com/Real-Time-Telecom-B-V/m2pa) | MTP2 peer-to-peer adaptation over SCTP | RFC 4165 | [![v](https://img.shields.io/crates/v/m2pa.svg?logo=rust)](https://crates.io/crates/m2pa) ![d](https://img.shields.io/crates/d/m2pa.svg) |
| [m3ua](https://github.com/Real-Time-Telecom-B-V/m3ua) | MTP3 user adaptation, ASP and SG state machines | RFC 4666 | [![v](https://img.shields.io/crates/v/m3ua.svg?logo=rust)](https://crates.io/crates/m3ua) ![d](https://img.shields.io/crates/d/m3ua.svg) |
| [mtp3](https://github.com/Real-Time-Telecom-B-V/mtp3) | MTP3-user SAP and point codes, the seam every MTP3 user binds to | ITU-T Q.704 | [![v](https://img.shields.io/crates/v/mtp3.svg?logo=rust)](https://crates.io/crates/mtp3) ![d](https://img.shields.io/crates/d/mtp3.svg) |
| [sccp](https://github.com/Real-Time-Telecom-B-V/sccp) | connectionless and connection-oriented SCCP | ITU-T Q.711 to Q.716 | [![v](https://img.shields.io/crates/v/sccp.svg?logo=rust)](https://crates.io/crates/sccp) ![d](https://img.shields.io/crates/d/sccp.svg) |
| [sua](https://github.com/Real-Time-Telecom-B-V/sua) | SCCP user adaptation over SCTP | RFC 3868 | [![v](https://img.shields.io/crates/v/sua.svg?logo=rust)](https://crates.io/crates/sua) ![d](https://img.shields.io/crates/d/sua.svg) |
| [tcap](https://github.com/Real-Time-Telecom-B-V/tcap) | transaction and component sublayers | ITU-T Q.771 to Q.775 | [![v](https://img.shields.io/crates/v/tcap.svg?logo=rust)](https://crates.io/crates/tcap) ![d](https://img.shields.io/crates/d/tcap.svg) |
| [itu-isup](https://github.com/Real-Time-Telecom-B-V/itu-isup) | ISUP messages and parameters, a direct MTP3 user (SI=5) | ITU-T Q.763 | [![v](https://img.shields.io/crates/v/itu-isup.svg?logo=rust)](https://crates.io/crates/itu-isup) ![d](https://img.shields.io/crates/d/itu-isup.svg) |
| [inap](https://github.com/Real-Time-Telecom-B-V/inap) | INAP CS-1 operations, a TCAP user | Q.1218, ETSI EN 300 374-1 | [![v](https://img.shields.io/crates/v/inap.svg?logo=rust)](https://crates.io/crates/inap) ![d](https://img.shields.io/crates/d/inap.svg) |
| [gsm_map](https://github.com/Real-Time-Telecom-B-V/gsm_map) | MAP operations, BER encode and decode | 3GPP TS 29.002 | [![v](https://img.shields.io/crates/v/gsm_map.svg?logo=rust)](https://crates.io/crates/gsm_map) ![d](https://img.shields.io/crates/d/gsm_map.svg) |
| [gsm_cap](https://github.com/Real-Time-Telecom-B-V/gsm_cap) | CAMEL Application Part | 3GPP TS 29.078 | [![v](https://img.shields.io/crates/v/gsm_cap.svg?logo=rust)](https://crates.io/crates/gsm_cap) ![d](https://img.shields.io/crates/d/gsm_cap.svg) |
| [tpdu](https://github.com/Real-Time-Telecom-B-V/tpdu) | SMS transfer-layer PDUs | 3GPP TS 23.040, 23.038, 24.011 | [![v](https://img.shields.io/crates/v/tpdu.svg?logo=rust)](https://crates.io/crates/tpdu) ![d](https://img.shields.io/crates/d/tpdu.svg) |
| [smpp34](https://github.com/Real-Time-Telecom-B-V/smpp34) | SMPP codec with an async client and server | SMPP 3.4 | [![v](https://img.shields.io/crates/v/smpp34.svg?logo=rust)](https://crates.io/crates/smpp34) ![d](https://img.shields.io/crates/d/smpp34.svg) |
| [async-sctp](https://github.com/Real-Time-Telecom-B-V/async-sctp) | tokio SCTP over the Linux kernel stack, Rust and Python | RFC 4960 | [![v](https://img.shields.io/crates/v/async-sctp.svg?logo=rust)](https://crates.io/crates/async-sctp) ![d](https://img.shields.io/crates/d/async-sctp.svg) |

All MIT. The stack composes: MTP2 or M2PA under MTP3, M3UA or SUA for SIGTRAN transport,
SCCP above that, TCAP above SCCP, then MAP, CAP or INAP as the application part.

## Runtime

[SIPhon](https://siphon-sip.org) is the SIP and media side, scriptable in Python.

- [siphon-sip](https://github.com/siphon-project/siphon-sip): proxy, B2BUA and IMS platform.
  [![v](https://img.shields.io/crates/v/siphon-sip.svg?logo=rust)](https://crates.io/crates/siphon-sip)
  [![pypi](https://img.shields.io/pypi/v/siphon-sip.svg?logo=pypi&logoColor=white)](https://pypi.org/project/siphon-sip/)
- [siphon-rtp](https://github.com/siphon-project/siphon-rtp): RTP and SRTP media engine,
  transcoding, DTLS.
- [siphon-sigtran](https://github.com/siphon-project/siphon-sigtran): SIGTRAN runtime over
  the crates above, M3UA and M2PA transport, MTP3 routing, SCCP.
- [siphon-smpp](https://github.com/siphon-project/siphon-smpp): SMPP addon, inbound and
  outbound, scriptable.
- [siphon-http](https://github.com/siphon-project/siphon-http): scriptable HTTP namespace.
- [caddy-siphon](https://github.com/siphon-project/caddy-siphon): Caddy with layer4, for
  fronting SIP over TLS and WSS.
- [pipecat-siphon](https://github.com/siphon-project/pipecat-siphon): pipecat
  FrameSerializer for the media WebSocket.

## Upstream

- [webrtc-rs/rtc#243](https://github.com/webrtc-rs/rtc/pull/243): retransmit the last DTLS
  flight when the peer repeats its own. Merged.
- [RestComm/jdiameter#170](https://github.com/RestComm/jdiameter/pull/170): SCTP
  multi-homing, client and server. Merged.
- [opentelecoms-org/jsmpp#123](https://github.com/opentelecoms-org/jsmpp/pull/123):
  alert_notification on a transceiver bind. Merged.
- [OpenSIPS/opensips#4277](https://github.com/OpenSIPS/opensips/pull/4277): hold a ctx
  reference for the rtp_relay in-dialog callback.
- [nickvsnetworking/pyhss#244](https://github.com/nickvsnetworking/pyhss/pull/244): fall
  back to Framed-IP-Address when Subscription-Id is absent.

## How I test this stuff

Codecs get validated against known-answer vectors from the spec, never round-trips. A
shared encode/decode bug passes a round-trip happily, and then you find it on someone
else's network.

Wireshark is the second opinion. Emit what our encoder produces, `text2pcap` it, and
assert the dissector reads back the IEs we intended. It does not share our bugs, so it
catches what a round-trip cannot. A field that comes back `[Malformed]` is our problem
until proven otherwise.

No `unwrap` or `expect` outside tests. Clippy with `-D warnings`, green, before anything
lands.

## Elsewhere

[realtime-telecom.nl](https://realtime-telecom.nl) &middot;
[siphon-sip.org](https://siphon-sip.org) &middot;
[LinkedIn](https://www.linkedin.com/in/mvdvlies/)
