
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

