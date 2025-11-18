# ⚙️ CPU Registers & Architecture Notes (Bangla-English)

---

## 🧩 Type of Registers in CPU

Registers holo CPU er **ultra-fast small memory** jeikhane calculation er data rakha hoy.

---

### 🔹 AL, BL, CL, DL Registers (Lower 8-bit)

- Ei gulo **AX, BX, CX, DX** register er **lower 8 bits** ke represent kore  
  Example:  
  AX = **AH (upper 8bit)** + **AL (lower 8bit)**

---

### 🔹 AX, BX, CX, DX Registers (16-bit)

- Ei gulo **General Purpose Registers**
- 16-bit register assembly language e onek common operation e use hoy

| Register | Use |
|---------|-----|
| AX | Accumulator Register (main calculation) |
| BX | Base Register |
| CX | Counter Register |
| DX | Data Register |

---

### 🔹 EAX, EBX, ECX, EDX Registers (32-bit)

- Ei gulo 32-bit **extended** version of AX, BX, CX, DX
- Modern OS & software e **32-bit architecture** e move korar jonno

---

### 🔹 RAX, RBX, RCX, RDX Registers (64-bit)

- Ei gulo **64-bit version**  
- Aajkal er modern CPU (x86-64 architecture) e use hoy
- 64-bit = more performance + larger memory access

---

## 🖥️ CPU (Central Processing Unit)

> CPU = Computer er **brain**  
> ja instruction execute kore & decision ney

---

### 🔧 CPU er 2 ta Main Parts

#### 1️⃣ Processing Unit

- Ei part abar **2 vage**:
  - **Control Unit (CU)** → instruction decode & manage kore
  - **Arithmetic Logic Unit (ALU)** → math & logical operations kore

#### 2️⃣ Registers  
_(General Purpose Register o bola hoy)_

Vitor thake onek important registers:

| Register | Full Name | Kaj |
|---------|-----------|-----|
| PC | Program Counter | Next Instruction er address |
| IR | Instruction Register | Currently executing instruction |
| SP | Stack Pointer | Stack er top address track kore |
| BP | Base Pointer | Stack e specific frame (local variable location) track kore |

---

## 🔁 SP vs BP — Difference

| SP (Stack Pointer) | BP (Base Pointer) |
|------------------|------------------|
| Stack er top indicate kore | Stack er specific frame/local variable indicate kore |
| Push/Pop e SP change hoy | Function call e BP stable thake |
| Recent push kora data pointer | Function er local variable access korte help kore |

📌 Local variable access hoy:  
➡️ BP + offset / BP - offset diye

---

## 🧠 Process Meaning

- **Process** holo ekta **virtual machine**  
  je computer er **resource (CPU, Memory)** use kore
- Ekta process ke OS limited power dey  
  (mane shey shob korte pare na — CPU + Memory constraints ase)

👉 Process er moddhe thread thake (execution unit)

---

## 🛡️ Operating System er Kaj

- 🔌 Computer on hole **OS load hoy**
- ⏱️ CPU er **control ney** & process er priority manage kore
- 🧵 Thread schedule kore
- 🧩 Memory manage kore
- 🛡️ Security & resource protection dey
- 📡 Hardware & software er majhe connector hishebe kaj kore

---

## ✨ BONUS: Why Registers Matter?

| Level | Speed | Size |
|------|-------|------|
| Register | ⚡ Fastest | Very Small |
| Cache | Fast | Small |
| RAM | Normal | Large |
| Disk | Slow | Very Large |

➡️ CPU sobar age **Register** theke data ney  
tai register e data rakha mane **ultra-fast performance** 🚀

---

### 🧠 Mini Summary

- AL/BL/CL/DL → Lower 8-bit
- AX/BX/CX/DX → 16-bit
- EAX/EBX/ECX/EDX → 32-bit
- RAX/RBX/RCX/RDX → 64-bit
- CPU = CU + ALU + Registers
- SP → Top of stack
- BP → Local variable access

---

# 🧵 SP & BP Example (Stack Frame Visualization)

📌 C Code:
```c
int add(int a, int b) {
    int c = a + b;
    return c;
}
 ```

📌 Assembly Code:
 ```
    add:
        push    ebp
        mov     ebp, esp

        sub     esp, 4

        mov     eax, [ebp+8]
        add     eax, [ebp+12]
        mov     [ebp-4], eax

        mov     eax, [ebp-4]

        mov     esp, ebp
        pop     ebp
        ret
   ``` 

# 🎯 Stack Layout (During Execution)


        High Address
    +-----------------------+
    | b (2nd parameter)     |  <- EBP + 12
    +-----------------------+
    | a (1st parameter)     |  <- EBP + 8
    +-----------------------+
    | Return Address        |  <- EBP + 4
    +-----------------------+
    | Saved Old EBP         |  <- EBP (0)
    +-----------------------+
    | c (local variable)    |  <- EBP - 4  <-- ESP
    +-----------------------+
        Low Address
