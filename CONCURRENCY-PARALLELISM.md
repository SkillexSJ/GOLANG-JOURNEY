# 🔀 Concurrency vs Parallelism — Golang Notes

## 🎩 Funny Example to Understand Concepts

### Dhoro ekta manush duniate **ek "HAT"** niye jonmo hoise

* Tar **Matha** ar **Pa** chulkani shuru hoise
* Jodi shey **ekbar Matha** abar **arekbar Pa** chulkani kore —
  ➜ Shey **Concurrent** 📌
  ➜ Meaning: **Context Switch** kortese

---

### Ar jodi manush **dui "HAT"** niye jonmo hoy

* Ek HAT diye **Matha**
* Arek HAT diye **Pa** chulkani
* Ek sathe kaj 🔥
  ➜ Shey **Parallel** 📌
  ➜ Meaning: **Same time e multiple kaj** cholse

---

## 🧠 CPU Example Breakdown

* CPU Core = **4 ta**
* Logical Core = **4 × 2 = 8 ta**

| Situation          | OS Action      | Result                                  |
| ------------------ | -------------- | --------------------------------------- |
| Process = **7 ta** | OS nibe 1 core | **6 ta** parallel cholbe                |
| Process = **8 ta** | OS nibe 1 core | 6 ta parallel + **1 ta context switch** |

📌 Jodi Logical Core er cheye **process beshi hoy** → Context switch lagbei

---

## ⚠️ Concurrent er Cons

* **Context switch** er jonno extra **time loss** hoy ⏳
* Performance degrade korte pare

---

## 🧮 When to Use What?

Use cases er upor depend kore:

**Concurrency vs Parallelism choose korar jonno — Scheduling Algorithm use hoy:**

* First Come First Serve (FCFS)
* Shortest Job First (SJF)
* Longest Job First (LJF)
* Priority Scheduling
* Round Robin
* Shortest Remaining Time First (SRTF)

---

## ⏱ Real-Life Example — Time Calculation

Dhoro:

* Core = **1 ta**
* **2 ta process**:

  * P1 → ⏱ 10 minute
  * P2 → ⏱ 2 minute

### ⚪ If Concurrent Execution

* Context switching time dhori = **2 min**

```
Total = 10 + 2 + 2 = 14 minute
```

### 🟢 If Parallel Execution

```
Total = 10 + 2 = 12 minute
```

✔ Eikhane **Parallel** is better

---

## 🏁 Quick Summary Table

| Term            | Meaning                       | Human Example                           |
| --------------- | ----------------------------- | --------------------------------------- |
| **Concurrency** | Alternately multiple task run | 1 HAT → Matha & Pa alternately chulkani |
| **Parallelism** | Same time e multiple task run | 2 HAT → Matha & Pa ek sathe chulkani    |

---

✨ Easy Formula:

> **Concurrency** = Multiple work progress, but context switch hoy
> **Parallelism** = Multiple work **exact same time** cholse

---

Done! 🚀
