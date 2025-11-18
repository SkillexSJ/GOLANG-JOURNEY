# ⚠️ Race Condition & Mutex in Go

## ❓ What is a Race Condition?

- Jokhon multiple processes ba threads **shared data**  
  (code segment, data segment) access kore and same time e change korte chay
- Example:
  - Dhoro **1000 worker** mile `count + 1` kore barabe
  - Race condition er jonno output **964** moto ashe
  - Mane baki **36 ta** update **haire gese** 😅

---

## 🔒 Solve Race Condition using Mutex Lock

- Use: `sync.Mutex` package
- Methods: `Lock()` & `Unlock()`
- Eita ensure kore:
  - **Ek somoy e sudhu ekta goroutine** value ta access korte parbe
  - Others wait korbe
  - Unlock hole **next goroutine** access pabe

---

### 🧑‍💻 Example Code — Mutex Lock in Go

```go
package main
import (
    "fmt"
    "sync"
)

func main() {
    var wg sync.WaitGroup
    var mu sync.Mutex
    count := 0
    worker := 1000

    for i := 0; i < worker; i++ {
        wg.Add(1)
        go func() {
            defer wg.Done()
            mu.Lock() // khela shuru
            count++
            mu.Unlock() // khela sesh
        }()
    }

    wg.Wait()
    fmt.Println("Final Count:", count)
}
