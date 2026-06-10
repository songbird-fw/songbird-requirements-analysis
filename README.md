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
 
| ID | Scope | Type | Priority | Quality Characteristic | Requirement Description (Atomic & Verifiable) | Approved |
| :---: | :---: | :---: | :---: | :---: | :--- | :---: |
| **RGFM1** | G | F | M | - | The system must execute static routing of IPv4/IPv6 packets between distinct logical and physical interfaces. | - |
| **RGFM1.1** | G | F | M | - | The system must support address translation via Source NAT (Masquerading) and Destination NAT (Port Forwarding). | - |
| **RGFM1.2** | G | F | M | Interoperability | The system must support IPv6 stateless address autoconfiguration (SLAAC) and Neighbor Discovery Protocol (NDP) on all configured interfaces. | - |
| **RGFM1.3** | G | F | M | Interoperability | The system must implement NAT64 translation to allow IPv6-only internal clients to reach IPv4-only external destinations, mapping traffic through a configurable NAT64 prefix (default: 64:ff9b::/96). | - |
| **RUFM2** | U | F | M | Flexibility | The user interface must allow the creation of security policies (policy management) based on the combination of Source Interface and Destination Interface. | - |
| **RUFM2.1** | U | F | M | Usability / Security | The Web UI must provide an interface to visualize and create firewall rules based on "Source Interface Zone" and "Destination Interface Zone". | - |
| **RUFM2.2** | U | F | M | Usability | The security policy editor in the Web UI must enforce the entry of mandatory fields: Source Int., Destination Int., Source/Destination IP/Subnet, Protocol (TCP/UDP/ICMP), Destination Port, and Action (Accept/Drop). | - |
| **RUFM3** | U | F | M | - | The network management interface must display a hierarchical tree structure, listing 802.1Q VLAN sub-interfaces nested under their respective physical interfaces. | - |
| **RUFM3.1** | U | F | M | Usability | The hierarchical tree in the interface must update dynamically, reflecting any addition or removal of VLAN sub-interfaces within 5 seconds of detection. | - |
| **RGFM4** | G | F | M | Efficiency / Performance | The packet filtering and forwarding pipeline (Data Plane) must be implemented entirely via eBPF programs loaded into the Linux kernel, completely bypassing the iptables/nftables subsystem. | - |
| **RGFM5** | G | F | M | Interoperability | The system must integrate an internal DHCP server for the dynamic allocation of IP addresses and network parameters across configured LAN segments. | - |
| **RGFM5.1** | G | F | M | Interoperability | The internal DHCP server must allow lease duration configuration and static IP binding based on the client's MAC address. | - |
| **RGFM5.2** | G | F | M | Reliability | The DHCP server must support simultaneous independent pools isolated per configured VLAN interface. | - |
| **RGFM5.3** | G | F | M | Interoperability | The system must support DHCPv6 with prefix delegation (PD) to assign IPv6 prefixes to downstream LAN segments. | - |
| **RGFM6** | G | F | M | Interoperability | The system must integrate a local DNS server/forwarder for name resolution of internal clients. | - |
| **RGFM6.1** | G | F | M | Interoperability | The local DNS forwarder must intercept port 53 traffic on local segments, cache successful queries, and forward unresolved requests to upstream DNS servers defined in the configuration. | - |
| **RGFM6.2** | G | F | M | Security | The local DNS server must support local hostname resolution mapping names defined in the static DHCP bindings table. | - |
| **RGFS6.3** | G | F | S | Interoperability / Security | The system must allow switching the internal DNS engine from a standard Forwarder to a full Recursive DNS Server (e.g., via an integrated Unbound instance) via the YAML configuration file. | - |
| **RGFS6.4** | G | F | S | Security | When in Recursive mode, the local DNS engine must resolve queries by directly traversing the global DNS root hints down to authoritative nameservers, bypassing upstream ISP resolvers. | - |
| **RGFS6.5** | G | F | S | Integrity | The Recursive DNS engine must enforce validation of DNS Security Extensions (DNSSEC) for 100% of traversing queries, dropping unauthenticated or tampered responses. | - |
| **RGFM6.6** | G | F | M | Interoperability | The system must integrate a DNS64 function that synthesizes AAAA records from A records for IPv4-only destinations, operating in conjunction with the NAT64 translation layer defined in RGFM1.4. | - |
| **RGNM7** | G | N | M | Reliability / Integrity | Operating system and firewall application updates must be atomic (A/B system update), ensuring an automatic and transparent rollback to the previous state in case of a boot failure. | - |
| **RGFS8** | G | F | S | Maintainability | The entire state and configuration of the firewall must be fully defined, importable, and exportable via structured YAML files. | - |
| **RGFS8.1** | G | F | S | Maintainability | The YAML configuration file must validate against a strict schema before execution, rejecting any syntax or schema violation with an error log. | - |
| **RGFS8.2** | G | F | S | Maintainability | The YAML file must include a dedicated `interfaces` section defining physical ports, IP assignments (IPv4/IPv6), and 802.1Q VLAN IDs. | - |
| **RGFS8.3** | G | F | S | Security | The YAML file must encrypt sensitive data (e.g., repository SSH keys or API tokens) using a secure local secret provider or environment variables. | - |
| **RGFS8.4** | G | F | S | Maintainability | The system must apply changes from a newly imported YAML file atomically: if any network block fails to initialize, the previous runtime network state must be fully restored within 15 seconds. | - |
| **RUFS9** | U | F | S | Interoperability / Flexibility | Every configuration change saved by the user via the Web UI must automatically trigger a structured Git commit and push to a designated remote repository (DevOps/GitOps mode). | - |
| **RUFS9.1** | G | F | S | Integrity | When an admin saves changes in the Web UI, the system must write the updated state to the local YAML file, trigger an automated Git commit with a structured message (e.g., `[Songbird Config] Updated via WebUI by [User]`), and push to the remote repository. | - |
| **RUFS9.2** | G | F | S | Reliability | If the `git push` to the remote repository fails (e.g., network down), the system must queue the change locally and retry every 60 seconds, warning the admin via a Web UI notification banner. | - |
| **RUFS9.3** | G | F | S | Security | The GitOps subsystem must support authentication with remote Git repositories (GitHub, GitLab, self-hosted) via SSH Private Keys or personal access tokens. | - |
| **RGNM10** | G | N | C | Portability / Integrity | The underlying operating system must adopt an immutable architecture with the root file system (`/`) mounted as read-only, except for directories dedicated to data persistence and system logs. | - |
| **RGFC11** | G | F | C | Reliability | The system must support an Active-Passive High Availability (HA) configuration. | - |
| **RGFC11.1** | G | F | C | Reliability / Integrity | In an HA Active-Passive configuration, both nodes must reference the same remote Git repository; each node must independently pull and apply any configuration update within 60 seconds of a new commit being pushed to the designated branch. | - |
| **RGFC11.2** | G | F | C | Reliability | The system must support the Virtual Router Redundancy Protocol (VRRP) to manage a shared virtual IP address, enabling automatic and transparent failover from the Active node to the Passive node within 3 seconds of Active node failure detection. | - |
| **RGFC12** | G | F | C | Interoperability | The system must support the BGP dynamic routing protocol to allow route advertisement and native integration with external load balancers (e.g., MetalLB in Kubernetes environments). | - |
| **RGFC13** | G | F | C | Security | The system must integrate a third-party IDS/IPS engine (e.g., Suricata or Snort) capable of intercepting passing traffic via eBPF hooks and blocking known threats based on updatable signature sets. | - |
| **RUFC14** | U | F | C | Efficiency / Usability | The monitoring tool built into the Web UI must display real-time metric charts for analysis and troubleshooting. | - |
| **RUFC14.1** | U | F | C | Efficiency / Performance | The monitoring dashboard must display real-time charts for global CPU usage, memory utilization, and network throughput per active interface. | - |
| **RUFC14.2** | U | F | C | Usability / Performance | Metric charts in the Web UI must refresh via WebSockets or Server-Sent Events (SSE). | - |
| **RUFC14.3** | U | F | C | Usability | The monitoring tool must allow filtering traffic metric charts by individual VLAN ID or specific Physical Interface. | - |
| **RGFM14.4** | G | F | M | Integrity / Security | The eBPF data plane must emit structured ring-buffer events containing connection metadata (Timestamp, Source/Destination IP, Source/Destination Port, Protocol, Interface, and eBPF Verdict: ACCEPT/DROP) for every matched policy. | - |
| **RUFS14.5** | U | F | S | Usability | The Web UI must feature an interactive "Live Traffic Log" viewer displaying both allowed (ACCEPT) and blocked (DROP) packets in a tabular format. | - |
| **RUFC14.6** | U | F | C | Efficiency / Usability | The Live Traffic Log viewer must allow dynamic filtering by Verdict (Blocked/Allowed), Source IP, and Destination Port, updating the filtered items. | - |
| **RGNM14.7** | G | N | M | Reliability / Security | Traffic logs must be written to a dedicated persistent local directory (e.g., `/usr/local/var/log/songbird/`) with an automated log-rotation policy that caps total log storage to 500MB to protect disk space. | - |
| **RGFM15** | G | F | M | Security | The Web UI must be accessible exclusively via encrypted HTTPS connections, automatically rejecting or redirecting HTTP traffic on port 80. | - |
| **RGFS15.1** | G | F | S | Security / Integrity | The system must integrate an automated ACME client component to provision and renew TLS certificates via Let's Encrypt using HTTP-01 or DNS-01 validation challenges. | - |
| **RGFS15.2** | G | F | S | Reliability | The ACME client must run a daily check via a systemd timer/cron job and trigger automated certificate renewal exactly 30 days prior to the TLS certificate's expiration date. | - |
| **RUFM16** | U | F | M | Security | The Web UI must require mandatory authentication before exposing any functionality, blocking every unauthenticated request with an HTTP 401/403 response. | - |
| **RUFM16.1** | U | F | M | Security | The system must support local authentication via username and password hashed with bcrypt (cost factor ≥ 12), without any possibility of access using plaintext credentials. | - |
| **RUFM16.2** | U | F | M | Security | The system must temporarily block an account for 10 minutes after 5 consecutive failed login attempts from the same IP, logging the event to the system audit log. | - |
| **RUFM16.3** | U | F | M | Security / Integrity | Every Web UI session must be associated with a signed session token (e.g., JWT or HttpOnly+Secure cookie) with a configurable expiration (default: 8 hours). | - |
| **RUFS16.4** | U | F | S | Security | The system must support two-factor authentication (TOTP/RFC 6238) for administrator accounts, with the ability to enable or disable it per individual user. | - |
| **RUFS16.5** | U | F | S | Security | The Web UI must expose a user management section allowing creation, modification, and revocation of local accounts with distinct roles (e.g., *admin* and *read-only*). | - |
| **RGNM16.6** | G | N | M | Security / Integrity | All authentication events (successful login, failed login, logout, account lockout) must be written to the audit log with ISO 8601 timestamp, source IP address, and username. | - |
| **RUFS17** | U | F | S | Interoperability | The system must support notification delivery via at least one configurable channel among: email (SMTP), HTTP/HTTPS webhook, or Telegram. | - |
| **RGNM17.1** | G | N | S | Reliability | The alerting subsystem must remain operational independently of the rest of the Web UI: a frontend crash must not prevent delivery of configured notifications. | - |
| **RGFM18** | G | F | M | Usability | On first boot without a valid YAML configuration file, the system must enter bootstrap mode, exposing a minimal Web UI wizard accessible via HTTPS on the WAN interface for initial configuration. | - |
| **RGFM18.1** | G | F | M | Security | In bootstrap mode, the system must accept Web UI connections exclusively from the internal LAN, blocking all other access until the initial configuration is complete. | - |
| **RGFS19** | G | F | S | Reliability | The system must expose an internal HTTP endpoint `/health` that responds with HTTP 200 and a JSON payload containing the operational status of each primary subsystem (eBPF data plane, DHCP, DNS, GitOps). | - |
| **RUFS19.1** | U | F | S | Usability | The Web UI must include a diagnostics page showing the real-time status of each internal subsystem, clearly indicating whether each component is *running*, *degraded*, or *stopped*. | - |
| **RGFM20** | G | F | M | Security | In the absence of an explicit security rule matching a traffic flow, the system must apply a *default deny* policy, dropping the packet and recording the event in the traffic log. | - |
| **RGFM20.1** | G | F | M | Reliability | In the event of an unexpected process crash or reboot, the system must automatically reload the last valid configuration state within 30 seconds, without manual intervention. | - |
 
