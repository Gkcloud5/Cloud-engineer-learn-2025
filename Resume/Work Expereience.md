## Technical Support Engineer: Nov 2020 – Oct 2022
* Resolved customer issues via live chat and support tickets across Linux and Windows VPS environments, escalating complex cases to senior engineers with full diagnostic context.
* Order provisioning with checking the server free space manually.
* Monitored production servers, identified anomalies, and flagged issues to senior engineers for timely remediation.
* Authored internal knowledgebase articles standardizing troubleshooting procedures, reducing repeat escalations and onboarding time for new support staff.
* Delivered front-line technical support for KVM/Xen VPS, dedicated servers, and cPanel shared hosting customers, resolving [X] tickets/month within SLA targets
- Diagnosed and fixed customer VPS issues: failed boots, OS reinstalls, disk resize problems, RDP/SSH access failures, and performance complaints on both Windows and Linux guests
- Performed network troubleshooting for customer connectivity issues using `tcpdump`, `mtr`, and `ping` — isolating guest-side misconfiguration from host- and provider-side causes
- Handled abuse reports and IP reputation investigations (AbuseIPDB, RIPE, bgp.he.net), coordinating null-route and mitigation actions with the network team
- Assisted customers with firewall configuration (iptables/firewalld), DNS, and web-hosting environment issues across shared and VPS platforms
- Documented recurring issues and fixes, building internal knowledge-base articles that reduced repeat ticket volume

## Systems Engineer: Nov 2022 – Oct 2024
* Resolved L2 incidents independently and drove L3 escalations to closure by coordinating with datacenter and network teams, owning issues through to resolution within SLA.
* Provisioned production servers end-to-end (IPMI configuration, OS installation, hypervisor setup, networking, ZFS storage) for customer-facing VPS workloads. 
	* HP, DELL, QUANTA, SUPERMICRO
* Built Bash automation for core infrastructure workflows — VPS provisioning, security hardening, OS reinstallation, and storage server backup recovery — reducing manual effort on recurring operations.
* For company extra revenue i have used unusued hardware to ran storj crypto node. and monitored with promotheous and grafana
* Improved fleet reliability by diagnosing recurring server issues, performing root cause analysis, and implementing permanent fixes to maintain uptime commitments.
* Mentored junior engineers on virtualization, storage administration, and troubleshooting practices.
* -Operated a mixed-hypervisor production fleet of [X] Proxmox VE (KVM/LXC) and XCP-ng/Xen nodes serving [X]+ customer VPS instances, covering node health, capacity, and VM lifecycle management
- Administered ZFS storage pools on hypervisor nodes: pool creation, snapshots, quota management, scrubs, and failed-disk replacement with resilver monitoring
- Resolved guest-level boot failures across Linux distributions (AlmaLinux, Rocky, Ubuntu, Debian, CentOS): GRUB/initramfs recovery, missing virtio and Xen paravirtual drivers, dracut rebuilds after kernel updates on EL9 Xen HVM guests
- Troubleshot production networking on a multi-homed BGP network (own ASN): VLAN-aware vs. traditional Proxmox bridge models, tap/bridge/bond traffic-path tracing, MTU and firewall/nftables diagnostics
- Maintained Linux and Windows OS templates and supported WHMCS-integrated provisioning through the in-house automation platform (Xenica)
- Acted as escalation point for support-tier tickets involving storage, virtualization, and network layers under a 99.99% SLA with financial refund penalties

## Systems Engineer — Infrastructure Automation & Storage Platforms Nov 2024 – Present
* Designed and built a ZFS-based snapshot backup and replication platform for XenServer and Proxmox environments, covering NVMe data disks and OS disks across the production fleet — later launched as a customer-facing backup service.
* Developed a custom REST API to manage backup job states, prevent overlapping executions, and provide centralized visibility into backup operations.
* Implemented efficient replication using ZFS send/receive — initial full sync followed by incremental transfers — with automated retention and cleanup management on destination backup servers.
* Prepared new servers for production end-to-end, from IPMI access through hypervisor, networking, and storage configuration to customer VPS delivery.
* Resolved L2/L3 production incidents across compute, storage, and network layers under a 99.99% SLA with financial downtime penalties.
* Designed and operate an automated cross-node ZFS snapshot backup and replication system (Bash, cron, `zfs send/receive`) protecting customer VPS data across [X] Proxmox hypervisor nodes, with hypervisor auto-detection and Git-based script delivery from Bitbucket
- Hardened backup pipeline against silent failures by adding structured logging, atomic script updates (temp-file + `mv`), checksum verification, and network-failure resilience — eliminating unlogged cron failures across the fleet
- Established fleet-wide automation workflows using `dsh` distributed shell across node groups: parallel script deployment, `md5sum` integrity verification, and hostname-prefixed output auditing across [X] nodes
- Authored ZFS disaster-recovery runbooks (send/receive flag behavior, dataset rename vs. clone-promote, single-VM restore procedures) adopted as team standard operating procedure in the infrastructure repository
- Administer ZFS RAIDZ2 storage pools ([X] TB across NVMe, hybrid NVMe+HDD tiers) including replication, snapshot lifecycle management, disk replacement, and resilvering under production load
- Manage OmniOS-based NFS storage backend serving XCP-ng compute nodes; support NFS and Ceph storage repositories, VDI/VBD lifecycle via `xe` CLI
- Maintain backup job state in MySQL with sync-first reconciliation between API status and local state, preventing recurring job conflicts
- Drive root-cause analysis for complex production incidents: conntrack exhaustion causing asymmetric outbound failures, IPv6 NDP failures across Proxmox bridge models, and selective BGP null-route diagnosis
- Storage Server Complete migration
	-  Planned and executed a 400TB server-to-server storage migration for a production NFS storage repository hosting live VMs, using ZFS send/receive streamed over mbuffer for high-throughput transfer.
	- Designed an incremental snapshot approach — full initial replication (3–5 days) followed by progressively smaller differential sends — shrinking the final sync to under an hour and minimizing VM downtime.
	- Coordinated the cutover: paused all VMs on the storage repository, sent the final differential snapshot, reassigned the storage IP to the destination server, and validated VM resume with no data loss.
- - Storage Server Preparation:
	- Provisioned production OmniOS storage servers (400–500TB capacity) from bare metal, including BIOS/firmware updates, OS installation on dedicated boot disks, and LACP bonding of dual 10GbE NICs for the primary data path.
	- Designed RAIDZ2 storage pools via napp-it with deliberate disk placement — mapping drive bays from BIOS/caddie documentation to ensure no two disks in the same vdev shared a physical caddie, protecting against backplane-level failures.
	- Exported pools over NFS to hypervisor hosts as production storage repositories.