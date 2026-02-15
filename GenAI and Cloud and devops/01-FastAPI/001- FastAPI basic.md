
### What is fastAPI:
* it is a python framework that help us to create servers that handle the HTTP request and return response

```
User (browser) → Request → FastAPI → Function runs → Response → User
```

### What is Uvicorn:
* Uvicorn is the server that runs FastAPI and handles incoming HTTP requests


### About pydantic:
* Pydantic validate the data automatically.


### Final mental map of data process in fastapi world:

```
User sends request → Uvicorn receives → FastAPI matches route → Pydantic validates → function runs → JSON returned.
```

