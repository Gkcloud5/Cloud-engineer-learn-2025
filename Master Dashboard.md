---
type: "Dashboard"
created: {{date}}
tags: [dashboard, learning, master]
---

# 🧠 Master Dashboard

> “Clarity + Consistency = Mastery”

---

## 🌞 Today’s Focus
- 🎯 **Main Topic:** [[<Your Topic of the Day>]]
- ⏱️ **Time Goal:** 1 hr
- 🧩 **Focus Mode:** Deep Work / Pomodoro / Flow
- 📅 **Date:** <% tp.date.now("dddd, MMMM Do YYYY") %>

✅ **Mini Wins Today**
- [ ] Read / Watch 1 key concept  
- [ ] Summarize in your own words  
- [ ] Create 1 atomic note  
- [ ] Review yesterday’s notes  

---

## 📚 Learning Tracker
| Date                            | Topic | Time Spent | Progress % | Key Takeaway | Dopamine Hit 🔥 |
| ------------------------------- | ----- | ---------- | ---------- | ------------ | --------------- |
| <% tp.date.now("YYYY-MM-DD") %> |       |            |            |              | [ ]             |

Use [[Daily Learn Log]] for detailed progress.  
👉 *Tip:* Use a dataview query below to auto-pull your daily logs.

```dataview
table date, topic, progress, dopamine
from "Learning/Daily Logs"
sort date desc
