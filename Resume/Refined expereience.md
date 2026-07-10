### Role 1 — Technical Support Engineer (Nov 2020 – Oct 2022)
* Delivered front-line technical support for KVM/Xen VPS, dedicated servers, and cPanel shared hosting, resolving [X] tickets/month within SLA across Linux and Windows environments
* Diagnosed and resolved guest-level VPS issues — failed boots, OS reinstalls, disk resizing, SSH/RDP access failures, and performance complaints — escalating complex cases with full diagnostic context
* Performed network troubleshooting using tcpdump, mtr, and ping to isolate guest-side misconfiguration from host- and provider-side causes
* Investigated abuse reports and IP reputation issues (AbuseIPDB, RIPE, bgp.he.net), coordinating null-route and mitigation actions with the network team
* Authored internal knowledge-base articles standardizing troubleshooting procedures, reducing repeat escalations and new-hire onboarding time

### Role 2 — Systems Engineer (Nov 2022 – Oct 2024)
* Operated a mixed-hypervisor production fleet of [X] Proxmox VE (KVM/LXC) and XCP-ng/Xen nodes serving [X]+ customer VPS instances, covering node health, capacity planning, and VM lifecycle management
* Provisioned production servers end-to-end — IPMI configuration, OS installation, hypervisor setup, networking, and ZFS storage — on HP, Dell, Quanta, and Supermicro hardware
* Resolved guest-level boot failures across Linux distributions (AlmaLinux, Rocky, Ubuntu, Debian, CentOS): GRUB/initramfs recovery, virtio and Xen paravirtual driver issues, and dracut rebuilds after kernel updates on EL9 Xen HVM guests
* Administered ZFS storage pools across hypervisor nodes: pool creation, snapshots, quota management, scrubs, and failed-disk replacement with resilver monitoring
* Troubleshot production networking on a multi-homed BGP network (company-owned ASN): Proxmox bridge models, tap/bridge/bond traffic-path tracing, MTU and nftables firewall diagnostics
* Acted as escalation point for storage, virtualization, and network-layer incidents under a 99.99% SLA with financial refund penalties, driving root cause analysis and permanent fixes
* Deployed distributed storage nodes (Storj) on underutilized hardware to generate supplemental revenue, with Prometheus and Grafana monitoring for capacity and node health
* Built Bash automation for VPS provisioning, security hardening, OS reinstallation, and backup recovery workflows; maintained OS templates and WHMCS-integrated provisioning via the in-house platform (Xenica)

### Role 3 — Systems Engineer, Infrastructure Automation & Storage Platforms (Nov 2024 – Present)

* Designed and built a ZFS snapshot backup and replication platform (Bash, cron, zfs send/receive) protecting customer VPS data — NVMe data disks and OS disks — across [X] XenServer and Proxmox hypervisor nodes, with hypervisor auto-detection and Git-based script delivery from Bitbucket; later launched as a customer-facing backup service
* Developed a custom REST API to manage backup job states, prevent overlapping executions, and provide centralized visibility, with job state persisted in MySQL using sync-first reconciliation to prevent recurring conflicts
* Hardened the backup pipeline against silent failures with structured logging, atomic script updates, checksum verification, and network-failure resilience — eliminating unlogged cron failures across the fleet
* Implemented efficient replication via ZFS send/receive — initial full sync plus incremental transfers — with automated retention and cleanup on destination backup servers
* Established fleet-wide automation using dsh distributed shell: parallel script deployment, md5sum integrity verification, and audited execution across [X] nodes
- Administer ZFS RAIDZ2 storage pools ([X] TB across NVMe and hybrid NVMe+HDD tiers) and an OmniOS-based NFS backend serving XCP-ng compute nodes, including NFS/Ceph storage repositories and VDI/VBD lifecycle via xe CLI
- Authored ZFS disaster-recovery runbooks (send/receive semantics, clone-promote vs. rename, single-VM restores) adopted as team standard operating procedure
- Drove root-cause analysis for complex production incidents — conntrack exhaustion causing asymmetric outbound failures, IPv6 NDP failures across Proxmox bridge models, selective BGP null-route diagnosis — under a 99.99% SLA with financial downtime penalties
