# songbird-requirements-analysis

## Must have
1. Basic router/firewall function
2. Fortigate like policy management
3. Fortigate like interface management (es. list of vlan under interface)
4. eBPF (instead of iptables) --> if Linux is used as OS

## Nice to have
1. YAML-based configuration (changes made via webgui are lost during reboot?) --> need to think about it because it may be easy to lose track of the configuration you made if the syntax is too complicate
2. Immutable OS

