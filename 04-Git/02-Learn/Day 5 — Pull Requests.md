
### 5.1 Real purpose of a PR:
* A *Pull request* -= a formal request to merge changes into a shared branch so others can inspect, test and approve before code lands.
* Companies use PR's to:
	* Run automated tests
	* Enforce code style and security checks
	* Force peer review
	* Keep history understandable

### 5.2 The PR lifecycle:
1. Create a feature branch locally
2. Make focused commits with clear messages
3. Push branches to remote
4. Open PR to github: include description, testing steps, ticket number
5. Assign reviewers, set labels, add reviewers
6. CI runs automatically on PR.
7. Reviewers requests changes or approves.
8. You update the branch, push changes
9. When green and approves, merge using the team approved method
10. Delete the feature branch

### 5.3 Branch and commit rules:
* Branch names: `feature/ticket-short desc`, `bug fixes/ticket-short`, `hotfix/version`.
* Commit names: Short summary --> login: add remember me option
* Keep PR's small - 200 lines max ideally. Big PRs
* Squash related WIP commits before merging if history should be clean.

### 5.4 Merge methods: when to use each:
* Merge commit: Preserves branch history: use for big, multi commit features when want trace
* Squash merge: Combines all PR commits into one, use to keep main history clean.
* 