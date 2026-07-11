
### **Systems Engineer — Infrastructure Automation & Storage Platforms** | Nov 2024 – Present
* Built a ZFS-based backup and replication platform for XenServer and Proxmox environments to protect both NVMe data and OS disks. Developed a custom REST API to manage backup jobs and prevent overlapping executions, and implemented ZFS send/receive replication with incremental sync, automated snapshot retention, and cleanup. The platform was later introduced as a customer-facing backup service.
* Planned and completed a 400TB production NFS storage migration between ZFS storage servers hosting live VMs by using ZFS send/receive over `mbuffer`. Used a full initial replication followed by incremental snapshot transfers to reduce the final synchronization to under an hour, then performed the cutover by pausing VMs, applying the last differential snapshot, moving the storage IP to the new server, and validating that all VMs resumed without data loss.
* Built and prepared 400–500TB production OmniOS storage servers from bare metal, including BIOS and firmware updates, OS installation on dedicated boot disks, LACP configuration for dual 10GbE NICs, RAIDZ2 pool creation with napp-it using planned disk placement to avoid caddie-level failures, and NFS export to XenServer and Proxmox hosts as production storage repositories.

### Systems Engineer: Nov 2022 – Oct 2024
* Prepared and deployed production XenServer (XCP-ng) and Proxmox (KVM/LXC) hosts from bare metal, including IPMI setup, OS and hypervisor installation, networking, and ZFS storage configuration on HP, Dell, Quanta, and Supermicro servers. 
* Built Bash automation for VPS provisioning, security hardening, OS reinstallation, and storage backup recovery. Maintained OS templates and supported automated VPS provisioning through the in-house Xenica platform integrated with WHMCS.
* Resolved L2 infrastructure incidents independently and coordinated with datacenter and network teams to drive L3 escalations through to resolution within SLA.
* Deployed and managed Storj storage nodes on underutilized servers to generate additional revenue, with Prometheus and Grafana used to monitor node health and storage capacity.
* Restored customer VMs from storage and NVMe backups, validating data integrity and VM boot after recovery.

### Technical Support Engineer: Nov 2020 – Oct 2022
* Provided technical support for KVM/Xen VPS, dedicated servers, and cPanel shared hosting, resolving 200–400 customer tickets per month within SLA across Linux and Windows environments.
* Diagnosed and resolved VPS issues including boot failures, OS reinstalls, disk resizing, SSH/RDP connectivity, and performance problems, escalating complex cases with complete diagnostic details when required.
* Monitored production servers, investigated system issues, and escalated findings to senior engineers for resolution.
* Wrote and maintained internal knowledge base articles to document troubleshooting procedures and provide consistent guidance for the support team.