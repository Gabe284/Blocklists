# Gabe284 Blocklists

This repository publishes domain blocklists in standard hosts-file syntax.

## NSA-focused agency-related combined list

**[NSA-Combined.txt](NSA-Combined.txt)**

Raw subscription URL:

`https://raw.githubusercontent.com/Gabe284/Blocklists/main/NSA-Combined.txt`

- Format: `0.0.0.0 domain.example`
- 8,194 unique domains; deduplicated and alphabetically sorted.
- Includes the original NSABlocklist, BadBlock NSA NG, and Adblock the NSA.
- Jeff's Counter-Intelligence and Tigthor's NSA-CIA HOSTS projects were inspected and documented. Their normalized domain set is already represented; they add no new agency-related entries.
- Source details, exclusions, and limitations: [SOURCES.md](SOURCES.md).

## Scope and warning

This is an experimental research list, not a verified or authoritative inventory of current intelligence-agency infrastructure. The upstream lists overlap heavily and contain domains that may be ordinary public services, DNS infrastructure, hosting, or government websites. Inclusion is not proof of ownership or wrongdoing. Test with a separate DNS policy and maintain an allowlist for services you need before deploying system-wide.

The combined file blocks DNS names only. It does not block IP-level traffic or prevent ISP/backbone interception, device compromise, or surveillance that uses unlisted infrastructure.

## Upstream maintenance

The combined file is a snapshot of upstream data as of 2026-11-05. Review upstream changes before refreshing it; do not automatically trust newly added entries.
