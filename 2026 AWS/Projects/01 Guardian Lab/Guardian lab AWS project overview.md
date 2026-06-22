
## Problem statement:
	Enterprise infrastruture fails in unpredictable ways, like node crash, disk fill, applications hand, databases corrupt, and network path drop. this all are will affect real users on unexpected time. if it happens at mid night then there is no person to check and resolve it. so we need to prevent mostly before it comes. this project will help to prevent most of this issue. 
		The goal of this project is simulate these failure conditions in a controlled environment and prove that detection, automated response and recovery can happen faster than a human can even open a terminal.


## Architecture Diagram:


### Phases of the project:
**Phase 1** → VPC + EC2 + EFS + Security Groups (Infrastructure)

**Phase 2** → Flask app + PostgreSQL on EC2 (Workload)

**Phase 3** → CloudWatch + SNS + Lambda automation (Detection + Action)

**Phase 4** → EBS Snapshots + S3 backup + EventBridge (Backup Strategy)

**Phase 5** → Run the 5 drills + write post-mortems (Proof)


### Tech stack:

| Tool / Technology                 | Role in the Project                                                                                                                       | Why This, Not Something Else                                                                                                                                                   |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| EC2 (3 instances)                 | Compute — 1 bastion/controller + 2 worker nodes running the workload                                                                      | Industry standard cloud compute. Chose over ECS/EKS to keep focus on infrastructure resilience, not container orchestration                                                    |
| VPC (Public + Private Subnet)     | Network isolation — Public subnet for app traffic, Private subnet for management                                                          | Mirrors VLAN-10/VLAN-20 design. Chose over flat networking because subnet separation is a real enterprise security requirement                                                 |
| Security Groups + NACLs           | Firewall rules — control inbound/outbound traffic per instance and subnet                                                                 | Security Groups are stateful (instance level), NACLs are stateless (subnet level) — both needed for realistic drill scenarios                                                  |
| EFS (Elastic File System)         | Shared storage — mounted across all 3 EC2 instances simultaneously                                                                        | Direct replacement for shared NFS/Ceph. Chose over EBS because EBS is single-instance only; EFS gives true shared state across nodes                                           |
| EBS (Elastic Block Store)         | Per-instance block storage — OS disk and PostgreSQL data volume                                                                           | Fast, low-latency disk per EC2. Snapshot capability is the backbone of the backup strategy                                                                                     |
| S3                                | Backup destination — stores EBS snapshots, database dumps, logs                                                                           | Durable, cheap, infinitely scalable. Chose over EFS for backups because S3 is the standard cold/warm backup target in AWS                                                      |
| Flask + PostgreSQL                | Application workload — the thing being protected and recovered                                                                            | Realistic two-tier app that generates real failure scenarios across compute, storage, and network                                                                              |
| CloudWatch Metrics + Alarms       | Monitoring and alerting — tracks CPU, disk, memory, app health, triggers alarms on threshold breach                                       | Native AWS observability. Chose over self-hosted Prometheus to demonstrate production-grade AWS tooling                                                                        |
| SNS (Simple Notification Service) | Alert routing — receives CloudWatch Alarm and fans out to Lambda and email                                                                | Decouples alarm from action. One SNS topic can trigger multiple subscribers simultaneously — critical for Boss Round drill                                                     |
| Lambda                            | Automated remediation — receives SNS trigger, executes healing actions (restart app, clean disk, revert security group, restore snapshot) | Serverless, event-driven, no server to manage. Direct replacement for Python webhook handler                                                                                   |
| EventBridge (Scheduled Rules)     | Cron replacement — triggers Lambda on schedule for periodic EBS snapshots                                                                 | Native AWS scheduler. Chose over EC2-hosted cron because EventBridge is managed, survives instance failures, and is fully auditable                                            |
| Auto Scaling Group (ASG)          | Node recovery — automatically replaces terminated EC2 instance                                                                            | Direct replacement for virsh migrate. When a node is killed, ASG detects it and launches a replacement without manual intervention                                             |
| CloudWatch Logs                   | Centralized log aggregation — ships logs from all 3 EC2 instances to one place                                                            | Native AWS log storage. Chose over self-hosted Loki to keep the stack fully managed and demonstrate AWS-native observability                                                   |
| CloudWatch Dashboard              | Unified visibility — single pane showing metrics, alarms, log insights across all nodes                                                   | Native, zero setup. Optionally replaced with Grafana on EC2 if richer visualization is needed                                                                                  |
| IAM Roles + Policies              | Security layer — grants Lambda, EC2, and EventBridge least-privilege access to AWS resources                                              | No hardcoded credentials anywhere. IAM roles are the AWS-native RBAC system — non-negotiable in any real AWS project                                                           |
| CloudFormation                    | Infrastructure as Code — provisions entire AWS environment in repeatable, version-controlled YAML templates                               | AWS-native IaC, no additional tooling required, state managed automatically by AWS. Terraform port planned as a follow-on project to demonstrate cross-platform IaC capability |
| GitHub                            | Version control + documentation — all CloudFormation templates, Lambda functions, scripts, post-mortems                                   | Every change is traceable and reviewable. Serves as the live portfolio artifact shown in interviews                                                                            |

## The Drills:

Each drill follows the same structure: **What was simulated → What was expected → What actually happened → How it was recovered → RTO/RPO measured.**

---

**Drill 1 — Kill the Node (EC2 Instance Termination)**

**What was simulated:**  
Worker node-2 EC2 instance was hard-stopped via AWS Console to simulate an unexpected host failure.

**What was expected:**  
Auto Scaling Group detects the unhealthy instance, terminates it, and launches a replacement within the configured warm-up period. CloudWatch Alarm fires and SNS notifies via email.

**What actually happened:**  
_(To be filled after you run the drill — write exactly what happened, including any delays or surprises)_

**Recovery path:**  
ASG automatically launched a replacement EC2 instance. EFS shared storage ensured the new node had immediate access to application data without manual intervention.

**RTO measured:** _(fill after drill)_  
**RPO measured:** _(fill after drill)_

---

**Drill 2 — Disk Fill (EBS Volume at 100%)**

**What was simulated:**  
EBS volume on worker node-1 was filled to 100% capacity using a Bash script writing junk data in a loop.

**What was expected:**  
CloudWatch disk utilization alarm triggers at 85% threshold. SNS routes alert to Lambda. Lambda automatically deletes old EBS snapshots and temporary files to recover space.

**What actually happened:**  
_(To be filled after you run the drill)_

**Recovery path — Primary:**  
Lambda function triggered by SNS cleans old snapshots and temp files, disk utilization drops below threshold, alarm resolves automatically.

**Recovery path — Alternate (if Lambda fails):**  
SSH into instance via bastion, manually identify large files using `df -h` and `du -sh /*`, delete or archive to S3, verify disk recovers.

**RTO measured:** _(fill after drill)_  
**RPO:** Not applicable — no data loss event.

---

**Drill 3 — Application Crash (Flask Process Kill)**

**What was simulated:**  
Flask web application process was force-killed on the primary worker node using `kill -9` to simulate an application crash.

**What was expected:**  
CloudWatch custom metric detects application health check failure. Alarm triggers SNS. Lambda executes SSM Run Command to restart the Flask service on the target instance.

**What actually happened:**  
_(To be filled after you run the drill)_

**Recovery path — Primary:**  
Lambda uses SSM Run Command to restart Flask service remotely. No manual SSH required.

**Recovery path — Alternate (if SSM restart fails):**  
Lambda triggers AMI restore from last known good snapshot. Instance is replaced with a clean state. PostgreSQL data remains intact on EBS data volume.

**RTO measured:** _(fill after drill)_  
**RPO measured:** _(fill after drill)_

---

**Drill 4 — Database Corruption (PostgreSQL Recovery)**

**What was simulated:**  
PostgreSQL data directory was manually corrupted by deleting critical system catalog files, simulating a database corruption event.

**What was expected:**  
Application health check fails. CloudWatch alarm fires. SNS routes to Lambda. Lambda initiates EBS snapshot restore to last known good state.

**What actually happened:**  
_(To be filled after you run the drill)_

**Recovery path — Primary:**  
Lambda detaches the corrupted EBS data volume, restores from the most recent EBS snapshot, reattaches the restored volume, restarts PostgreSQL service via SSM Run Command.

**Recovery path — Alternate (if snapshot restore fails):**  
Restore PostgreSQL from S3 database dump taken by the most recent EventBridge-scheduled backup Lambda.

**RTO measured:** _(fill after drill)_  
**RPO measured:** _(distance between last snapshot and corruption event)_

---

**Drill 5 — Network Block (Security Group / NACL Modification)**

**What was simulated:**  
Inbound traffic on port 80 and 443 was blocked on the Public Subnet NACL, simulating a network partition or misconfigured firewall rule cutting off application traffic.

**What was expected:**  
CloudWatch Synthetics canary or external health check detects application unreachable. Alarm fires. SNS triggers Lambda. Lambda reverts the NACL rule to restore traffic.

**What actually happened:**  
_(To be filled after you run the drill)_

**Recovery path — Primary:**  
Lambda uses Boto3 to identify the modified NACL rule and revert it to the baseline configuration stored in CloudFormation template.

**Recovery path — Alternate (if Lambda cannot reach AWS API due to network block):**  
CloudFormation stack update via AWS Console to redeploy baseline network configuration, restoring correct NACL rules.

**RTO measured:** _(fill after drill)_  
**RPO:** Not applicable — no data loss event.

