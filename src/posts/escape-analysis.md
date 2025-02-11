---
title: 'Escape Analysis'
seoTitle: 'Escape Analysis'
datePublished: 2025-02-11T01:05:07.341Z
slug: escape-analysis
tags: escape analysis, compiler optimization, memory management, Go
---

We know that the computer stores variables depending on where they are within the scope of the program into either the stack or heap memory.

As a quick refresher:

> Stack memory is a region in the RAM that is used to store local variables, function calls and control flow data in a LIFO manner.

> Heap Memory is a dynamically allocated region in memory that stores content that is shared by all threads of a current process.

From the above definitions and our CS classes, we know that when we define variables in functions, those variables are placed on the stack memory that is created.

```go
func main() {
    count := 10;
    fmt.Printf("Count is %d", count)
}
```

In the above code, the variable count is created in the stack memory since it's a "local variable"

Let's look at another example

```go
func main() {
    count := 5;
    go countdown(&count)
}


func countdown(time *int) {
    // do something with the time
}
```

From our definition of the Stack Memory and it's association with "local variables", at first glance, one might think that the variable "count" is created and placed in the stack. But nope, it's created and stored in the Heap.

**When we create a variable that belongs to the functions stack but instead it's created in the heap, we say the variable has escaped to the heap**

Let's understand why this happens.

### Escape Analysis

Consists of compiler algorithms that decide whether a variable should be created in the stack memory or the heap instead of the stack. Escape analysis is an optimization technique in compilers.

### Why was it created on the heap instead of the stack?

You might be asking yourself that, the answer is that, objects in the stack memory only exist for the lifetime of the function within which they are called. Once the function runs and terminates, it's stack frame is popped off to free the memory. The reason why the GO (or other language) compiler placed this function inside the heap is because of this reason.

Since functions have different execution lifetimes, we don't want one function's lifetime to affect the other function because the other function is dependent on whatever object that was passed to it. If it wasn't created in the heap, The function `countdown` would never see the value of that particular object.

Immediately the compiler identifies that we are sharing memory of a particular object, it places that object inside the heap and not the function stack.

Remember this: _Anytime a variable is shared outside the scope of a function’s stack frame, the variable is allocated on the heap_

Know that the heap memory is accessible by all functions inside the executing process.
