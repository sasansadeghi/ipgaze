# iPGaze

**Free network, DNS, email and security diagnostics — 70+ tools, no signup, no account.**

### → [ipgaze.com](https://ipgaze.com)

This repository is the public home of iPGaze: issue tracker, changelog, and a
place to request tools. The service itself runs at
[ipgaze.com](https://ipgaze.com).

---

## Why

Debugging a mail or DNS problem usually means bouncing between half a dozen
single-purpose sites — one for the SPF record, another for the MX lookup, a
third for the certificate chain, a fourth to check whether a port is actually
open. iPGaze puts them in one place, with consistent output and no sign-up wall.

## Tools

**DNS** — [lookup](https://ipgaze.com/tools/dns) ·
[propagation](https://ipgaze.com/tools/dns-propagation) ·
[reverse DNS](https://ipgaze.com/tools/reverse-dns) ·
[DNSSEC](https://ipgaze.com/tools/dnssec) ·
[CAA](https://ipgaze.com/tools/caa) · [SOA](https://ipgaze.com/tools/soa) ·
[SRV](https://ipgaze.com/tools/srv) ·
[nameservers](https://ipgaze.com/tools/nameservers) ·
[full DNS report](https://ipgaze.com/tools/dns-report)

**Email authentication** — [SPF](https://ipgaze.com/tools/spf) ·
[DKIM](https://ipgaze.com/tools/dkim) · [DMARC](https://ipgaze.com/tools/dmarc) ·
[MTA-STS](https://ipgaze.com/tools/mta-sts) ·
[TLS-RPT](https://ipgaze.com/tools/tls-rpt) ·
[BIMI](https://ipgaze.com/tools/bimi) · [MX](https://ipgaze.com/tools/mx) ·
[blacklist check](https://ipgaze.com/tools/blacklist)

**IP & network** — [what's my IP](https://ipgaze.com/tools/whats-my-ip) ·
[IP lookup](https://ipgaze.com/tools/ip) ·
[bulk geolocation](https://ipgaze.com/tools/bulk-geo) ·
[ASN lookup](https://ipgaze.com/tools/asn) ·
[subnet calculator](https://ipgaze.com/tools/subnet) ·
[IPv6 compress](https://ipgaze.com/tools/ipv6-compress) ·
[ping](https://ipgaze.com/tools/ping) ·
[traceroute](https://ipgaze.com/tools/traceroute) ·
[open port check](https://ipgaze.com/tools/open-port)

**Security & web** — [SSL certificate](https://ipgaze.com/tools/ssl) ·
[security headers](https://ipgaze.com/tools/security-headers) ·
[HTTP status](https://ipgaze.com/tools/http-status) ·
[redirect chain](https://ipgaze.com/tools/redirect-chain) ·
[DNS leak test](https://ipgaze.com/tools/dns-leak) ·
[WebRTC leak test](https://ipgaze.com/tools/webrtc-leak) ·
[WHOIS](https://ipgaze.com/tools/whois)

**Developer utilities** — Base64, JWT decode, hashing, JSON/YAML, regex tester,
cron parser, UUID, timestamps, text diff, and more.

[Browse all tools →](https://ipgaze.com)

## How the tools run

Every tool page states which of these two models it uses:

- **Client tools** run entirely in your browser. Base64, JWT decoding, hashing,
  text diff and the other format utilities never send your input anywhere — the
  work happens locally in JavaScript.
- **Server tools** need the server to reach the network on your behalf: DNS
  resolution, WHOIS, TLS handshakes, ping, traceroute, port checks.

## Notes on the server tools

Tools that connect to a user-supplied host are guarded against SSRF. Hostnames
are resolved and **every** returned A/AAAA address is checked before a
connection is opened; private, loopback, link-local and reserved ranges are
rejected, including the `169.254.169.254` cloud metadata endpoint. Process-based
tools (ping, traceroute) are spawned with an explicit argument array rather than
a shell string.

Per-IP rate limiting applies to all API endpoints, with a stricter cap on the
active network tools.

## Guides

Long-form write-ups on the problems these tools diagnose — SPF lookup limits,
DMARC policy modes, DNS TTL behaviour, certificate chains, reading a traceroute:

[ipgaze.com/guides](https://ipgaze.com/guides)

## Built with

Next.js 14 (App Router) · TypeScript · Tailwind CSS. Self-hosted on a single
Linux VPS behind nginx and systemd.

## Feedback

Found a bug, got a wrong result, or want a tool that isn't there?
[Open an issue](../../issues) — or use the
[contact form](https://ipgaze.com/contact).

## Funding

iPGaze is free to use and ad-supported; the ads pay for the server.

---

© iPGaze · [Privacy](https://ipgaze.com/privacy) ·
[Terms](https://ipgaze.com/terms)
