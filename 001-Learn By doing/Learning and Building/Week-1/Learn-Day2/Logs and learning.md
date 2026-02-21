* When i am learning logs in fastapi, i have created the log file store the requst logs of my http, after 2 days i saw my logs i was socked, wtf, who all are. 
* some one tried to get my VPS /etc/passwd
  
Here are the logs:

```
2026-02-18 21:13:10,353 | INFO | Log test endpoint triggered
2026-02-19 14:25:16,294 | INFO | GET /async | 2004.87ms
2026-02-19 14:25:18,219 | INFO | GET /favicon.ico | 0.38ms
2026-02-19 14:25:27,691 | INFO | GET /env-test | 1.53ms
2026-02-19 14:25:52,133 | INFO | Log test endpoint triggered
2026-02-19 14:25:52,134 | INFO | GET /log-test | 1.37ms
2026-02-19 17:00:46,314 | INFO | GET / | 1.58ms
2026-02-19 17:00:56,745 | INFO | GET / | 0.93ms
2026-02-19 17:00:57,458 | INFO | PRI  | 0.39ms
2026-02-19 17:00:57,901 | INFO | GET /favicon.ico | 0.37ms
2026-02-19 17:01:01,807 | INFO | GET /sitemap.xml | 0.69ms
2026-02-19 19:37:15,507 | INFO | GET / | 1.62ms
2026-02-19 19:39:12,520 | INFO | GET /favicon.ico | 0.37ms
2026-02-19 19:58:10,740 | INFO | GET / | 1.01ms
2026-02-19 19:58:19,573 | INFO | GET / | 0.73ms
2026-02-19 19:58:20,218 | INFO | PRI  | 0.37ms
2026-02-19 19:58:20,637 | INFO | GET /favicon.ico | 0.41ms
2026-02-19 19:58:24,461 | INFO | GET /login | 0.42ms
2026-02-19 20:04:23,501 | INFO | GET //httpbin.org/ip | 0.37ms
2026-02-20 02:58:14,125 | INFO | GET / | 0.54ms
2026-02-20 02:58:46,400 | INFO | GET /favicon.ico | 0.39ms
2026-02-20 02:58:58,050 | INFO | GET //api.ipify.org/ | 0.67ms
2026-02-20 02:59:05,433 | INFO | CONNECT  | 0.36ms
2026-02-20 05:20:44,887 | INFO | CONNECT  | 0.37ms
2026-02-20 05:20:45,390 | INFO | CONNECT  | 0.34ms
2026-02-20 05:59:04,501 | INFO | GET / | 0.82ms
2026-02-20 06:02:06,217 | INFO | GET / | 0.55ms
2026-02-20 06:31:07,094 | INFO | GET / | 0.81ms
2026-02-20 07:34:30,580 | INFO | GET / | 0.83ms
2026-02-20 07:36:33,659 | INFO | GET /favicon.ico | 0.38ms
2026-02-20 07:43:27,989 | INFO | GET /../../../../../../etc/passwd | 0.69ms
2026-02-20 08:13:03,652 | INFO | GET /.git/config | 0.62ms
2026-02-20 08:13:03,653 | INFO | GET /.env.development | 1.14ms
2026-02-20 08:13:03,667 | INFO | GET /.aws/credentials | 0.3ms
2026-02-20 08:13:03,675 | INFO | GET /.env.production | 0.32ms
2026-02-20 08:13:03,716 | INFO | GET /config.json | 0.41ms
2026-02-20 08:13:03,719 | INFO | GET /.env | 0.25ms
2026-02-20 08:17:52,008 | INFO | GET / | 0.85ms
2026-02-20 09:55:32,540 | INFO | POST /api/client/update | 0.42ms
2026-02-20 11:13:51,033 | INFO | GET / | 0.84ms
2026-02-20 11:15:22,711 | INFO | GET / | 0.77ms
2026-02-20 11:32:33,063 | INFO | GET / | 0.98ms
2026-02-20 11:32:44,109 | INFO | GET / | 0.99ms
2026-02-20 14:01:24,608 | INFO | GET / | 0.77ms
2026-02-20 14:01:25,037 | INFO | GET /favicon.ico | 0.4ms
2026-02-20 14:01:25,456 | INFO | GET /sitemap.xml | 0.35ms
2026-02-20 14:01:25,465 | INFO | GET /robots.txt | 0.3ms
2026-02-20 15:25:50,925 | INFO | GET / | 0.8ms
2026-02-20 15:25:59,336 | INFO | GET / | 0.87ms
2026-02-20 15:25:59,539 | INFO | PRI  | 0.43ms
2026-02-20 15:25:59,926 | INFO | GET /favicon.ico | 0.46ms
2026-02-20 15:26:05,549 | INFO | GET /.well-known/security.txt | 0.39ms
2026-02-20 18:45:09,218 | INFO | GET / | 1.02ms
2026-02-20 19:32:36,736 | INFO | GET / | 0.73ms
2026-02-20 19:33:18,912 | INFO | GET /favicon.ico | 0.36ms
2026-02-20 20:41:46,233 | INFO | GET / | 0.82ms
2026-02-20 20:41:55,072 | INFO | GET / | 0.76ms
2026-02-20 20:41:55,697 | INFO | PRI  | 0.37ms
2026-02-20 20:41:56,112 | INFO | GET /favicon.ico | 0.39ms
2026-02-20 20:42:00,527 | INFO | GET /.well-known/security.txt | 0.36ms
2026-02-20 21:00:13,206 | INFO | GET / | 0.77ms
2026-02-20 21:46:28,134 | INFO | GET / | 0.87ms
2026-02-20 21:57:53,736 | INFO | GET /bins/ | 0.38ms
2026-02-20 22:02:33,329 | INFO | GET /bin/ | 0.75ms
2026-02-20 22:15:04,729 | INFO | GET /backup/ | 0.39ms
2026-02-20 23:54:53,588 | INFO | GET / | 1.5ms
2026-02-20 23:55:02,011 | INFO | GET / | 0.65ms
2026-02-20 23:55:02,291 | INFO | PRI  | 0.38ms
2026-02-20 23:55:02,513 | INFO | GET /favicon.ico | 0.35ms
2026-02-20 23:55:05,941 | INFO | GET /login | 0.37ms
2026-02-21 01:40:21,438 | INFO | GET / | 1.46ms
2026-02-21 03:49:32,203 | INFO | GET /../../../../../../etc/passwd | 0.41ms
2026-02-21 04:56:59,292 | INFO | GET / | 0.75ms
2026-02-21 04:57:29,683 | INFO | GET /favicon.ico | 0.43ms
2026-02-21 04:57:42,665 | INFO | GET //api.ipify.org/ | 0.43ms
2026-02-21 04:57:51,341 | INFO | CONNECT  | 0.58ms
2026-02-21 05:34:43,083 | INFO | GET /status | 0.95ms
2026-02-21 05:34:43,361 | INFO | GET /stat | 0.38ms
2026-02-21 07:06:43,491 | INFO | GET / | 0.84ms
2026-02-21 07:58:55,741 | INFO | GET / | 0.58ms
2026-02-21 08:38:16,701 | INFO | GET / | 0.57ms
2026-02-21 08:38:17,444 | INFO | POST / | 0.36ms
2026-02-21 08:38:17,847 | INFO | POST /_next | 0.37ms
2026-02-21 08:38:18,549 | INFO | POST /api | 0.37ms
2026-02-21 08:38:18,859 | INFO | POST /_next/server | 0.4ms
2026-02-21 08:38:19,100 | INFO | POST /app | 0.42ms
2026-02-21 08:38:19,598 | INFO | POST /api/route | 0.74ms
2026-02-21 10:18:13,135 | INFO | GET / | 0.79ms
2026-02-21 10:58:48,412 | INFO | GET / | 0.97ms
2026-02-21 14:30:12,173 | INFO | GET| /async|2004.5ms
2026-02-21 14:30:13,610 | INFO | GET| /favicon.ico|0.53ms
```

So i just stopped the fastapi learning and planning to secure the server first. i checked and find some things regarding it
* first important attact: `GET /../../../../../../etc/passwd
* `## 2️⃣ Secret File Scanning`
* IP checking/Proxy scans
* API and directory guessing

## Production setup: 
-> Production grade
```
Internet → FastAPI (uvicorn)
```
to:
```
Internet → Nginx → FastAPI → Logs → Fail2Ban
```


## Using ngnix reverse proxy:
### why?
* without reverse request will direct 
