# Technical corrections and validation scope

The professional editions include corrected reference examples. Original Word reports and screenshots remain unchanged as historical evidence. Corrections describe the intended configuration; they do not claim the lab was rerun or that screenshots show the corrected state.

## Layer 2 mitigations — corrected

- Replaced `switchport violation shutdown` with `switchport port-security violation shutdown`.
- Enabled DHCP snooping and dynamic ARP inspection explicitly for VLAN 1.
- Assigned trust to the verified router/DHCP uplink, with the client port untrusted. The report states the assumed interface mapping rather than treating it as a measured fact.
- Added a client DHCP packet-rate limit and kept port-security controls on the client port. Values are labeled lab examples.
- Corrected the DHCP-server lease check to `show ip dhcp binding`; distinguished that from the switch's `show ip dhcp snooping binding`.
- Corrected the prose from DHCP spoofing to DHCP snooping and separated ARP validation from DHCP exhaustion controls.
- Explained how static clients require an appropriate ARP ACL or another supported binding configuration for dynamic ARP inspection.
- Normalized shell command prompts and removed prose placeholders from executable command blocks. The attack tools were not executed during editing.
- Included a complete [switch reference](../examples/network-security/layer-2-switch.cfg) with [assumptions and checks](../examples/network-security/README.md).

## OSPF configurations — reconciled with the diagrams

- The original IPv4 diagram assigns R1 G0/0/1 `10.0.0.18/30` and R3 G0/0/0 `10.0.0.10/30`. Corrected those typed examples to remove duplicate endpoint addresses.
- Aligned all IPv6 interfaces with the seven /64 links in the original IPv6 diagram, replacing inconsistent prefixes in the typed commands.
- Replaced mismatched OSPF `network` statements with per-interface OSPFv2 and OSPFv3 activation. The five ring links use Area 0; S1–R5 uses Area 1; S2–R4 uses Area 2.
- Added explicit OSPFv2 and OSPFv3 router IDs, routed switch interfaces, IPv6 forwarding, mode exits, and privileged verification commands.
- Replaced malformed verification examples with `show ip ospf neighbor`, `show ip route ospf`, `show ip ospf`, and their classic IPv6 counterparts.
- Added an addressing table and [seven device configurations](../examples/network-routing/README.md). [Topology data](../examples/network-routing/topology.json) records both endpoints of each link.
- Checked unique addresses, usable host addresses, matching peer subnets and areas, unique router IDs, Area 0 connectivity, and correspondence between topology data and generated configuration text. These are static checks; device convergence and platform support remain runtime checks.
- Original console captures are explicitly labeled as original evidence. The original narrative's successful troubleshooting outcome remains attributed to the source report. The class sign-off image remains only in the archived original.

## Local AI — complete reference deployment

- Corrected the WSL flag to `wsl --update` and used HTTP for the default local UI URL.
- Replaced incomplete Docker excerpts with complete Ollama and Open WebUI commands using ASCII option flags, images, a shared Docker network, persistent volumes, and an explicit backend URL.
- Chose a container-only CPU reference architecture. Native host Ollama from the Windows screenshots is not required by this updated example.
- Added a [Compose configuration](../examples/local-ai/compose.yaml) and [setup and readiness commands](../examples/local-ai/README.md). The UI is bound to the local host; the model API has no published host port.
- Added model download/listing, backend connectivity, browser response, logs, and shutdown instructions. The example model is identified as a reference choice.
- Checked the examples against the upstream [Ollama](https://github.com/ollama/ollama) and [Open WebUI](https://github.com/open-webui/open-webui) documentation. Docker Compose validation checks structure and resolved configuration, not service readiness. Images and a model were not downloaded or run during editing.
- Image tags follow upstream quick-start examples and may change; the report explains recording digests for a reproducible run.

## Portfolio preservation and scope

- Objectives, background sections, troubleshooting, and conclusions were edited for clarity. Unsupported historical digressions were removed.
- Filled the empty AWS Labs 4–6 objective from the existing exercise content and described the IAM policy's specific management actions accurately.
- Retained all 126 technical image occurrences and all eight original BGP reference tables; added one corrected OSPF addressing table.
- Verified archived original files against recorded SHA-256 hashes. Checked Word archive integrity, retained image bytes, PDF figure counts, text bounds, and repository file links.
- No new performance metrics, certifications, completion dates, or claims of independent lab work were added. Physical networking, AWS, attack tools, and model inference were not rerun.
