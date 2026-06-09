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

## Must have
1. Basic router/firewall function
2. Fortigate like policy management (Source and Destination Interface)
3. Fortigate like interface management (es. list of vlan under interface)
4. eBPF (instead of iptables) --> if Linux is used as OS
5. DHCP and DNS
6. Atomic upgrades

## Should have
1. YAML-based configuration
1.1 DevOps mode: changes in the UI prompt for a code commit to a repo
2. Sick webui

## Could have
1. Immutable OS
2. HA
3. BGP (so you can use it with MetalLB)
4. IDS/IPS (with third party tool like suricata or snort maybe?)
5. Very good monitoring and analysis tool built-in
