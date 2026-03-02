
* `Requests` library will help us to send and get response from local llm in python
	* If client sends requests
	* FastAPI calls local LLM using `requests`
	* LLM takes 5 seconds
	* During those 5 seconds
		* Worker is just waiting and doing nothing else
* fastAPI is built on async, that means it can handle many requests at the same time without blocking
* `httpx` async --> it will help to handle multip