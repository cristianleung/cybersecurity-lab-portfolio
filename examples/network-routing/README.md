# Corrected OSPF reference

These clean-lab configurations follow the IPv4 and IPv6 topology diagrams in the original OSPF report. They replace inconsistent typed examples; they are not a capture of a new router run.

Use IOS images supporting `ip ospf <process> area <area>` and classic `ipv6 ospf <process> area <area>` interface commands. Multilayer switches also need routed-port and IPv6-routing support. Confirm platform feature availability and interface names before applying. Existing device configuration is outside these clean-lab examples.

`topology.json` records both ends of all seven links. R1, R2, R3, S1, and S2 form the Area 0 ring; S1 connects R5 in Area 1, and S2 connects R4 in Area 2. Per-interface activation keeps each IPv4 and IPv6 interface in its intended area.

Expected neighbor counts after convergence: R1/R2/R3: 2 each; S1/S2: 3 each; R4/R5: 1 each. These counts are predictions from the graph and require verification on devices.

Verify with `show ip ospf neighbor`, `show ip route ospf`, `show ip ospf`, `show ipv6 ospf neighbor`, `show ipv6 route ospf`, and `show ipv6 ospf`. From R1, test both edge networks with IPv4 and IPv6 pings. The reports retain the original screenshots separately from these corrected configurations.
