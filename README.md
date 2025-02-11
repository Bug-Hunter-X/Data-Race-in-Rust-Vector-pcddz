# Data Race in Rust

This repository demonstrates a common data race issue that can occur in Rust when working with vectors and references.  The `bug.rs` file contains code that exhibits this behavior. The `bugSolution.rs` file offers a solution, avoiding the race condition.

**The Problem:**
The code creates a vector and obtains a reference to its first element.  After modifying the vector (by pushing another value), this reference is still used, leading to a potential data race because the vector's underlying data may be reallocated in memory. The compiler isn't able to detect this case easily as it may seem fine until runtime which might make it hard to debug.

**Solution:**
The `bugSolution.rs` addresses the problem by using techniques such as cloning or borrowing immutably. Note that copying large vectors can impact performance, so the best solution depends on the specifics of your application.