# songbird-requirements-analysis

Each requirement should:
* be unambiguous (interpretable in only one way);
* be testable (quantified), meaning that compliance or noncompliance can be clearly demonstrated;
* be binding, meaning that clients are willing to pay for it and unwilling not to have it;
* atomic, represent a single decision
* represent true, actual stakeholder needs;
* use stakeholder vocabulary;
* be acceptable to all stakeholders.

The overall collection of requirements should be:
* complete - The requirements adequately address boundary conditions, exception conditions and security needs;
* concise - No extraneous content in the requirements
* internally consistent - No requirement conflicts with any other;
* externally consistent - No requirement conflicts with any source material;
* feasible - A viable, cost-effective solution can be created within cost, schedule, staffing, and other constraints

Requirements scopes can be:
* User (U): what users interacts directly with
* General (G): what is invisible to the users

Requirements types can be:
* Functional (F) - what the software should do:
  * System behaviors - how the system responds to inputs, events, or triggers.
  * Data handling rules - how data is captured, validated, processed, stored, and transmitted.
  * Workflow logic - the sequence of operations or business rules that govern system behavior.
  * Interactions - how the system interfaces with users, external systems, hardware, or APIs.
  * Error handling - how the system behaves when something goes wrong.
* Non-functional (N) - how the software performs a task rather than what it should do:
  * Performance - response time, throughput, latency, and resource usage.
  * Security - encryption, authentication, authorization, and auditability.
  * Reliability and availability - uptime targets, fault tolerance, redundancy.
  * Usability - accessibility standards, user experience expectations, interface consistency.
  * Scalability - ability to handle increased load or data volume.
  * Maintainability - modularity, code quality, ease of updates, and documentation standards.
  * Compliance - adherence to regulatory or industry standards.
* Quality (Q) - how are the software characteristics:
  * Maintainability - Amount of effort needed for developers to update, refactor, or otherwise modify the software’s code.
  * Portability - Amount of effort needed to run the software on different platforms.
  * Reliability - How often the software’s functions succeed or fail.
  * Efficiency - Number of resources the software requires.
  * Integrity - How frequently the software loses data.
  * Memorability - Amount of time users must spend relearning functionality.
  * Flexibility - Number of different ways the software can be used.
  * Interoperability - Ease with which the software can integrate with other software.
  * Reusability - Extent to which the code can easily be used to solve other problems.

Requirements priorities can be mandatory (Must have - M), desirable (Should have - S), optional (Could have - C) or excluded (Won't have - W)

Requirements will be identified by R followed by the scope (U, G), then by the type (F, N), then by the priority (M, S, C, W), then by a numeric index (1, 1.1)

## Requirements Table (Sorted by Progressive Index)

| Requirement ID | Scope | Type | Priority | Quality Characteristic (Q) | Requirement Description (Atomic & Verifiable) |
| :--- | :---: | :---: | :---: | :--- | :--- |
| **RGFM1** | G | F | M | - | The system must execute static routing of IPv4/IPv6 packets between distinct logical and physical interfaces. |
| **RGFM1.1** | G | F | M | - | The system must support address translation via Source NAT (Masquerading) and Destination NAT (Port Forwarding). |
| **RUFM2** | U | F | M | Flexibility | The user interface must allow the creation of security policies (policy management) based on the combination of Source Interface and Destination Interface. |
| **RUFM3** | U | F | M | - | The network management interface must display a hierarchical tree structure, listing 802.1Q VLAN sub-interfaces nested under their respective physical interfaces. |
| **RGFM4** | G | F | M | Efficiency / Performance | The packet filtering and forwarding pipeline (Data Plane) must be implemented entirely via eBPF programs loaded into the Linux kernel, completely bypassing the iptables/nftables subsystem. |
| **RGFM5** | G | F | M | Interoperability | The system must integrate an internal DHCP server for the dynamic allocation of IP addresses and network parameters across configured LAN segments. |
| **RGFM6** | G | F | M | Interoperability | The system must integrate a local DNS server/forwarder for name resolution of internal clients. |
| **RGNM7** | G | N | M | Reliability / Integrity | Operating system and firewall application updates must be atomic (A/B system update), ensuring an automatic and transparent rollback to the previous state in case of a boot failure. |
| **RGFS8** | G | F | S | Maintainability | The entire state and configuration of the firewall must be fully defined, importable, and exportable via structured YAML files. |
| **RUFS9** | U | F | S | Interoperability / Flexibility | Every configuration change saved by the user via the Web UI must automatically trigger a structured Git commit and push to a designated remote repository (DevOps/GitOps mode). |
| **RGNM10** | G | N | C | Portability / Integrity | The underlying operating system must adopt an immutable architecture with the root file system (`/`) mounted as read-only, except for directories dedicated to data persistence and system logs. |
| **RGFC11** | G | F | C | Reliability | The system must support an Active-Passive High Availability (HA) configuration. |
| **RGFC12** | G | F | C | Interoperability | The system must support the BGP dynamic routing protocol to allow route advertisement and native integration with external load balancers (e.g., MetalLB in Kubernetes environments). |
| **RGFC13** | G | F | C | Security | The system must integrate a third-party IDS/IPS engine (e.g., Suricata or Snort) capable of intercepting passing traffic via eBPF hooks and blocking known threats based on updatable signature sets. |
| **RUFC14** | U | F | C | Efficiency / Usability | The monitoring tool built into the Web UI must display real-time metric charts for analys and troubleshooting. |
