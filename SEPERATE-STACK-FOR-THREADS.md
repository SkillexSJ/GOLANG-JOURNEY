# 🐹 Golang Notes – Process, Thread & Stack (Detailed)

## 🧩 Process & Thread Concept

- 🖥️ **OS ekta process er vitor thread ke define kore**  
  Mane: ekta program cholte gele OS tar jonno ekta **process** create kore  
  ar oi process er vitor ek ba onek **thread** thakte pare.

- ⚙️ **Single ekta processor same time ekta thread ke execute kore**  
  Multi-tasking holeo processor extremely fast switch kore bole  
  mone hoy jeno ek sathe anek thread cholse.

---

## 🎵 Real-Life Example

- Jemon ekta **Music Player**:
  - Song play
  - Playlist update
  - Visualization animate
  - Download cholse
  - Volume control etc.

- Ei jabotiyo kaj gulo **"STACK"** e store thake  
  ar **ek-ekta thread er maddhome** ei kaj gulo execute hoy.  
  ➝ Each task = ekta **thread** er kaj

---

## 🧵 THREAD STACK (Detailed)

- 📌 Initially jokhon process create hoy:
  - OS ekta stack allocate kore **main thread** er jonno

- ➕ Porobortite proyojon onushare:
  - Notun **thread banay**
  - Prottek thread er jonno **notun alada stack** allocate hoy

- 🧠 **Stack Allocation** e kichu extra data o store hoy  
  (function call, local variable, return address etc.)

- 💾 Ei data-ta **process** ei joma thake  
  Dhore nao ekta **Stack == 8MB** (sathe **heap** thekeo memory nite pare)  
  ➝ Thread number barle stack memory barte pare

- 🔄 Stack gulo **physically alada** memory te thake  
  but **data adan prodan** possible (via shared memory)

- 📍 Stack **serially allocate hoy na**  
  mane shob ekshathe continuous memory te thake na  
  **Chinno vinno** jagay thakte pare

---

## 🧠 Role of Kernel (OS Boss)

- Kernel holo OS er **core part**  
  je **process**, **thread** banay & manage kore

- 👨‍💻 Programmer kernel ke instruct kore:
  - “Amar program er jonno **koto gulo thread** lagbe”

- ❌ Process nijer:
  - **koyta thread ase**
  - **stack kothay allocate**
  - ei sob **track rakhe na**
  - Process only tar **main thread** ke shudhu **directly bujhe**

- ✔️ Ei sob **tracking & management**:
  - Thread control
  - Resource distribution
  - Context switching  
  ➝ Sob **Kernel** kore

---

## 🔥 Quick Summary

| Topic | Simple Meaning |
|------|----------------|
| Process | Running program managed by OS |
| Thread | Process er vitor independent execution unit |
| Stack | Thread specific memory (local data store) |
| Kernel | Thread/process management authority |

---

✨ Final Line:  
👉 Thread er sob secret plan & location **Kernel er hat-e** 😄
