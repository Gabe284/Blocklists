# Source inventory and generation notes

Generated: 2026-11-05

## Included upstreams

| Source | Upstream | Normalized unique domains |
|---|---|---:|
| NSABlocklist | https://github.com/Gabe284/Blocklists/blob/main/NSABlocklist.txt | 8193 |
| NSA Blocklist – Next Generation | https://github.com/celenityy/BadBlock/blob/pages/wildcards-no-star/nsa-blocklist-ng.txt | 2872 |
| Adblock the NSA | https://github.com/gasull/adblock-nsa/blob/master/filters.txt | 105 |

Combined unique valid hostnames: **8194**.

The NSA NG list substantially overlaps the existing NSABlocklist; it is not an independent corroboration. The Adblock the NSA source is an older Adblock Plus ruleset associated with historical Shadow Brokers malware infrastructure. Its rules were converted from `||domain^` to hosts entries.

## Normalization

- Lowercase DNS names; remove trailing dots.
- Convert all accepted names to `0.0.0.0 domain`.
- Deduplicate exact hostnames and sort alphabetically.
- Ignore comments and source metadata.
- Exclude IP literals, malformed hostnames, wildcard rules, URL paths, and non-host rules because this output is a DNS hosts file, not an IP firewall.
- No root-domain collapsing: explicit subdomains remain explicit.

## Important limitations

This is a research-derived, experimental blocklist, not a verified list of current government or intelligence-agency endpoints. Inclusion does not establish ownership, maliciousness, or current operational use. DNS blocking cannot stop ISP-level interception, routing-layer surveillance, compromised endpoints, or traffic to unlisted infrastructure. False positives may disrupt DNS, hosting, education, CDN, and ordinary network services. Test in a separate DNS policy before deploying globally.

## Not included in the merged output

BadBlock's Anti-Monitoring list is a separate 928-entry category targeting monitoring/MDM and remote-management infrastructure. It is broader than NSA-related endpoints and can disrupt legitimate enterprise/device management. It should remain a separate opt-in list:
- Plain domains: https://badblock.celenity.dev/wildcards-no-star/monitoring.txt
- ABP: https://badblock.celenity.dev/abp/monitoring.txt

## Candidate related projects

- Jeff's Counter-Intelligence Service Hardening Security Policies: https://github.com/jeffreyulatan/Jeff-s-Counter-Intelligence-Service-Hardening-Security-Policies — historical hosts/IP-range material derived from CHEF-KOCH/NSABlocklist; high false-positive risk, especially super-ranges.
- Cybo's Hosts: https://github.com/donuthack/Hosts — has separate Anti collections for company/app-specific infrastructure; not NSA-specific.
- Block List Project: https://github.com/blocklistproject/Lists — maintained category lists in hosts format; general ads, tracking, malware, and telemetry rather than intelligence-specific.
- notracking/hosts-blocklists: https://github.com/notracking/hosts-blocklists — maintained multi-format aggregation for ads, trackers, malware; not intelligence-specific.

Only the three sources in the Included upstreams table are merged into `NSA-Combined.txt`. Other candidates require separate review and explicit opt-in before inclusion.
