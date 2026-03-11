
## How to present content:
1. Problem appears
2. Engineer struggles
3. Insight happens
4. Solution found
5. Knowledge extracted

## Nodes:
1. Document fetch
2. Content Parser
	1. Commands
	2. Random thoughts
3. Problem and solution extractor
	1. Root problem
	2. What failed
	3. Why it mattered
4. Technical Context builder
	1. Add missing context
	2. Environment
5. Story Hook Generator
	1. Zeigarnik effect
	2. Narrative transportation
6. Debugging journey builder
	1. Pratfall effect
7. Root cause and insight generator
	1. Cognitive Ease
		1. Explain real cause using technical mental models
8. Actionable solution builder
	1. Self efficacy
	2. Heuristic
9. Final Narrative composer

### Example:

``` text
Hook
Problem
Environment
Debugging Attempts
Mistake
Insight
Solution
```

```
Title: Fixing a Proxmox VM Locked by a Phantom Snapshot

Hook
I was about to restart a customer's VPS when Proxmox refused to start the VM.

Debugging
I tried restarting the daemon services...

Insight
The lock entry remained in the VM configuration.

Solution
Run:

qm unlock <vmid>
```