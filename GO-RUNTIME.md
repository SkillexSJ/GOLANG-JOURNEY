# 🧠 Golang Class Notes – Runtime, Scheduler & Socket

## 🥇 Memory Architecture

Memory 2ta space e bivajon:

1️⃣ **Kernel Space**  
2️⃣ **User Space**

- Ekta process jokhon kernel ke dak dey, tokhon sheita **System Call** bole
- Process er **Main Thread** → **Go Runtime** ke execute kore

---

## ⚙️ Go Runtime — ja ja kore 🔽

1️⃣ Initialize **Go Scheduler**

2️⃣ System Call → kernel ke dak dey  
   - Kernel **epoll_wait** create kore (separate thread e)  
   - Ei thread ta **always sleep mode** e thake

3️⃣ Main thread theke **epoll_ctl** kore → epoll_wait ke jagay dey value diye  
   - epoll value ta Go Runtime er kase dey  
   - Go Runtime sheita **User Space** e ek jaygay rakhe

4️⃣ **Garbage Collector** start kore (notun thread hobe)

---

### 📌 Important Notes

> epoll (Linux), kqueue (Mac), IOCP (Windows)  
> — eigula kernel er feature file read/write & I/O er jonno use hoy

👉 epoll 3 ta vag:
- `epoll_create`
- `epoll_ctl`
- `epoll_wait`

---

## 🌀 GO Scheduler

Go uses **M : P : G model**

| Symbol | Means |
|--------|------|
| M | Machine (OS Thread) |
| P | Processor (Logical Processor) |
| G | Goroutine |

Example:

- Dhori amar **4 ta core** → mane **4 ta logical processor**
- Tokhon **P = 4**
- Dhori **G = 16** goroutine

➡️ **Logical processor** 16 ta goroutine manage korbe  
➡️ **OS thread** 4 ta logical processor manage korbe

---

### 📍 Run Queues

Prottekta Logical Processor er ekta **Ring queue** thake →  
Jar nam: **Local Run Queue**

| Queue | Kakhon use hoy |
|-------|----------------|
| **Local Run Queue** | Slot faka thakle notun goroutine ekhane jay |
| **Global Run Queue** | Jodi Local queue full hoye jay → ekhane asbe |

⚙️ Stealing Mechanism:

> Jodi kono Local Queue completely khali hoye jay →  
> pasher Local Queue theke steal korbe  
> na paile → Global Queue theke nibe

---

## 🌐 Socket Banano — netpoll

Go Runtime communicates with kernel via:

### 🔌 `netpoll`

#### I/O Request Flow

1️⃣ Go Runtime kernel ke dak dey  
2️⃣ Kernel **epoll_wait** separate thread e create kore  
   - Ei thread **always sleeping**
3️⃣ User jokhon kono URL request dey → epoll_wait ke jagay dey value diye  
4️⃣ epoll shei value ta Go Runtime ke dey  
5️⃣ Go Runtime:
   - data → notun **goroutine** ke dey
   - nijeke **free** kore ney

---

## 🏁 Summary Diagram (Quick Memory Map)

| Layer | Works With |
|------|------------|
| Kernel Space | epoll, kqueue, IOCP, syscalls |
| User Space | Go Runtime, Scheduler, Goroutines |

---
