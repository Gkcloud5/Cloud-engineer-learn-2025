
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
* Squash merge: Combines all PR commits into one, use to keep `main` history clean.
* Rebase & merge: replays commits on top of target branch, use when you want clean linear history and keep each commit


### 5.5 Common mistakes:
* Pushing huge WIP PRs: split them
* Merging without checking CI: always wait for green
* Force-pushing to shared branches: never use `--force-with-lease` on feature branch
* No PR description or screenshots: reviewers hate this. Provide steps to test


### 5.6 PR templates and Branch protection setup:
#### 5.6.1 PR templates:
* It's markdown file that, when placed in root directory of repo, automatically populates the description field whenever someone opens a new pull request

#### 5.6.2. CodeOwners:
* A file that specifies which teams or individual are responsible for reviewing code changes in specific parts of repo

#### 5.6.3 Branch Protection:
* A set of rules configured by the repo administration to control what can be merged into