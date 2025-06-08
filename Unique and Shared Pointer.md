## Key Features – Why Use Smart Pointers?

Smart pointers like `unique_ptr` and `shared_ptr` are **wrappers around raw pointers** that handle memory cleanup **automatically**—so you don’t accidentally leave junk behind (aka memory leaks).

They give you **ownership semantics**—a way to control *who's responsible* for deleting the memory and *when* it should happen.

---

##  Unique Pointers (`unique_ptr`)

- Only **one owner** of the memory.
- When that owner goes out of scope, the memory gets freed automatically.
- Ownership can be **transferred** (via `std::move`), but never copied.

```cpp
std::unique_ptr<int> a = std::make_unique<int>(10);
std::unique_ptr<int> b = std::move(a); // a gives up ownership, b is now the boss

```

>  Think of it like a **single key to a locker**. Pass it on if you want, but only one person can hold it at a time.

---

##  Shared Pointers (`shared_ptr`)

- Multiple pointers can **share ownership** of the same memory.
- Keeps an internal **reference count** of how many owners exist.
- Memory is cleaned up **only when the last owner** is gone.

>  Imagine **multiple friends with copies of the house key**. The house stays until the last one leaves.

---

