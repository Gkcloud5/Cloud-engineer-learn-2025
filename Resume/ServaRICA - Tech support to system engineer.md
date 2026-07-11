## Systems Engineer — Infrastructure Automation & Storage Platforms Nov 2024 – Present

* KVM and XEN NVMe server backup automation system
	* Designed and built a ZFS-based snapshot backup and replication platform for XenServer and Proxmox environments, covering NVMe data disks and OS disks across the production fleet — later launched as a customer-facing backup service.
	* Developed a custom REST API to manage backup job states, prevent overlapping executions, and provide centralized visibility into backup operations.
	* Implemented efficient replication using ZFS send/receive — initial full sync followed by incremental transfers — with automated retention and cleanup management on destination backup servers.
- Storage Server Complete migration to another storage server
	-  Planned and executed a 400TB server-to-server storage migration for a production NFS storage repository hosting live VMs, using ZFS send/receive streamed over mbuffer for high-throughput transfer.
	- Designed an incremental snapshot approach — full initial replication (3–5 days) followed by progressively smaller differential sends — shrinking the final sync to under an hour and minimizing VM downtime.
	- Coordinated the cutover: paused all VMs on the storage repository, sent the final differential snapshot, reassigned the storage IP to the destination server, and validated VM resume with no data loss.
- Storage Server Preparation:
	- Provisioned production OmniOS storage servers (400–500TB capacity) from bare metal, including BIOS/firmware updates, OS installation on dedicated boot disks, and LACP bonding of dual 10GbE NICs for the primary data path.
	- Designed RAIDZ2 storage pools via napp-it with deliberate disk placement — mapping drive bays from BIOS/caddie documentation to ensure no two disks in the same vdev shared a physical caddie, protecting against backplane-level failures.
	- Exported pools over NFS to hypervisor hosts as production storage repositories.

### Systems Engineer: Nov 2022 – Oct 2024
- XEN and KVM Server Preparation:
	- Provisioned production servers end-to-end (IPMI configuration, OS installation, hypervisor setup, networking, ZFS storage) for customer-facing VPS workloads. 
	* HP, DELL, QUANTA, SUPERMICRO
* Resolved L2 incidents independently and drove L3 escalations to closure by coordinating with datacenter and network teams, owning issues through to resolution within SLA.
* Built Bash automation for VPS provisioning, security hardening, OS reinstallation, and backup recovery workflows; maintained OS templates and WHMCS-integrated provisioning via the in-house platform (Xenica)
* Deployed distributed storage nodes (Storj) on underutilized hardware to generate supplemental revenue, with Prometheus and Grafana monitoring for capacity and node health
* Manually recover VM from our backup
	* Storage VM backup.
	* NVMe VM backup
* Administered ZFS storage pools across hypervisor nodes: pool creation, snapshots, quota management, scrubs, and failed-disk replacement with resilver monitoring

### Technical Support Engineer: Nov 2020 – Oct 2022
* Delivered front-line technical support for KVM/Xen VPS, dedicated servers, and cPanel shared hosting, resolving 200 to 400 tickets/month within SLA across Linux and Windows environments
* Diagnosed and resolved guest-level VPS issues — failed boots, OS reinstalls, disk resizing, SSH/RDP access failures, and performance complaints — escalating complex cases with full diagnostic context
* Monitored production servers, identified anomalies, and flagged issues to senior engineers for timely remediation.
* Authored internal knowledgebase articles standardizing troubleshooting procedures, reducing repeat escalations and onboarding time for new support staff.