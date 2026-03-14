
### Reason:
This error is very common when **n8n tries to call another service inside Docker but the service is not reachable**. 

AI model link: http://172.17.0.1:11500/api/generate

My n8n workflow is connected with AI model running VPS by using tunneling.
### Checking:
1. First checking is port is active or not in n8n VPS
	1. `ss -tulnp | grep 11500`
		1. No output seems port is not running
		2. 