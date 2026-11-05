# Source inventory and generation notes

Generated: 2026-11-05

## Included and inspected agency-related sources

| Project/source | Upstream file | Result after normalization |
|---|---|---:|
| NSABlocklist | https://github.com/Gabe284/Blocklists/blob/main/NSABlocklist.txt | 8,193 unique domains |
| BadBlock NSA Blocklist – Next Generation | https://github.com/celenityy/BadBlock/blob/pages/wildcards-no-star/nsa-blocklist-ng.txt | 2,872 unique domains |
| Adblock the NSA | https://github.com/gasull/adblock-nsa/blob/master/filters.txt | 105 unique domains |
| Jeff's Counter-Intelligence Service Hardening Policies | https://github.com/jeffreyulatan/Jeff-s-Counter-Intelligence-Service-Hardening-Security-Policies/blob/master/HOSTS/HOSTS | Same normalized domain set as the current combined file, plus localhost.localdomain |
| Tigthor NSA-CIA-Blocklist | https://github.com/tigthor/NSA-CIA-Blocklist/blob/main/HOSTS/HOSTS | Byte-identical upstream HOSTS blob to Jeff's HOSTS file; same normalized set |

**Published combined unique domains: 8,194.**

### Overlap findings

- NSA NG shares 2,871 domains with NSABlocklist and contributes one additional domain.
- Adblock the NSA contributes no additional domains beyond NSABlocklist.
- Jeff's HOSTS and Tigthor's HOSTS have the same upstream blob SHA and normalize to the same set; compared with the current combined file, their only additional normalized hostname is `localhost.localdomain`, which is a local system name and is deliberately excluded.
- Consequently, the agency-related additions from the newly inspected Jeff/Tigthor projects are **zero**. The list's domain count remains 8,194. The sources are documented for provenance without duplicating their contents.

## Projects inspected but excluded

- **InfoSecREDD/Uni-Adblock** (https://github.com/InfoSecREDD/Uni-Adblock): its README describes a broad multi-source adblocker and claims a Government/Surveillance category spanning many entities. It is not a narrowly separable, independently attributable agency-only feed; merging its full aggregation would import unrelated advertising, tracking, and telemetry domains. Excluded.
- **BadBlock Anti-Monitoring** (https://badblock.celenity.dev/wildcards-no-star/monitoring.txt): targets monitoring/MDM and remote-management infrastructure, not government regulatory agencies specifically. Excluded.
- **Cybo's Hosts** (https://github.com/donuthack/Hosts): company/app-focused Anti collections, not a regulatory-agency feed. Excluded.
- **Block List Project** (https://github.com/blocklistproject/Lists): general-purpose ad, tracker, and malware categories, not an agency-specific source. Excluded.
- **CISA .gov data** (https://github.com/cisagov/dotgov-data): official registry data, not a threat or surveillance blocklist. Its full .gov inventory includes federal, state, local, tribal, and other government domains; blocking it would disable ordinary government services. Excluded.

## Normalization

- Lowercase DNS names; remove trailing dots.
- Convert accepted names to `0.0.0.0 domain`.
- Deduplicate exact hostnames and sort alphabetically.
- Ignore comments and source metadata.
- Exclude IP literals, malformed hostnames, wildcard rules, URL paths, and non-host rules because this output is a DNS hosts file, not an IP firewall.
- Do not collapse domains to parent zones; explicit hostnames remain explicit.
- Exclude local system names such as `localhost.localdomain`.

## Important limitations

This is an experimental research-derived list, not a verified inventory of current government or intelligence-agency endpoints. Inclusion does not establish ownership, maliciousness, or current operational use. The original material is old in places: Jeff/Tigthor identify a 2019 check date, while Adblock the NSA is a historical Adblock Plus ruleset associated with Shadow Brokers-era malware infrastructure. Do not treat it as a current authoritative threat feed.

False positives may disrupt DNS, hosting, education, CDN, and ordinary network services. Test in a separate DNS policy before deploying globally. DNS blocking cannot prevent ISP/backbone interception, routing-layer surveillance, compromised endpoints, or traffic to unlisted infrastructure.
