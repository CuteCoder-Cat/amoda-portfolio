---
title: "Deep Dive into Stacks: A Practical Guide for Software Engineers"
datePublished: 2023-11-09T19:40:19.000Z
cuid: clorlftng00080al9bet2h31w
slug: deep-dive-into-stacks-a-practical-guide-for-software-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/wstYTyWtGac/upload/d1ae6fdfc834744111ba65a912501eb4.jpeg
tags: programming, data-structures, data-structures-and-algorithm-course

---

## What is a Stack?

A stack is a very important data structure that is used to work on data *temporarily*. Unlike other data structures that are built into a language, a stack is rather a layer added to an existing data structure, such as an array or linked list. In this tutorial, however, we will focus on the array-based implementation of a stack.

So just like arrays, the data added to a stack is stored in contiguous memory. The main difference between a stack and an array is how operations on data are performed. A stack behaves differently from an array due to a ***set of rules*** that are added to the behavior of the array.

Data structures that are built on top of rules from other data structures are called <mark>abstract data types</mark>. Another type of abstract data type is the **queue**, which we will discuss in another post.

The stack data structure is a very important data structure used in various areas of computer science, like recursion. A stack helps to implement various things. The undo and redo functionalities of your IDE are based on a stack; your browser navigation, forward and back, is also based on a stack.

## How does it differ from an array?

The following rules differentiate how a stack operates from how an array operates.

1. You can only **add** to the end of the stack.
    
2. You can only **read** from the end of the stack.
    
3. You can only **delete** from the end of the stack.
    

In a typical array, one can insert data into any index they want, but in a stack, that is prohibited. If this rule is broken, then it is no longer a stack but something else. (#1)

Reading from a typical array does not restrict where in the array you read from. You can read from the beginning of the array, the middle, or the end, wherever you want to read from. But then, in a stack, it is mandatory to only read from the end of the stack.

The third rule states that you can only delete from the end of the stack. This is a very different behavior from a normal array because, in an array, one can delete at any index they want.

It should be noted that these rules are not pre-written in most languages but are implemented when the stack data structure is built. It is typically not a built-in structure but rather something that the programmer explicitly creates.

> The end of the stack is referred to as the top. This is because we look at the stack not like a horizontal array but as a vertical array.

## Scenario

You can think of a stack data structure as stones placed on top of each other, like in the preview picture above. To add another stone, you place it on top of the already existing stones, not below or in the middle (Rule #1)

If the stones were colored and you want to see (read) the color of the most recent one, you will obviously look down at the stones. The latest one simply refers to the one you just added to the stack. (Rule #2)

Also, to remove a stone, you would have to remove the one from the top first, as this is the only logical way to go about it if you don't want your stone empire to come crumbling down (Rule #3)

This behaviour of the stack is referred to as the **<mark>LIFO</mark>** This is an acronym for Last In, First Out. This basically means that the first thing you add to the array is the last thing that comes out.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699291262795/6659f108-28bf-4f32-9b53-12cf105a35f2.png)

## Operations Performed on a Stack

The operations performed on a stack are:

* Reading, a.k.a. "Peeking,"
    
* Adding: AKA "Pushing to the Stack".
    
* Removing: AKA "Popping from the Stack".
    

## Implementation of a Stack in Python

```python
class Stack:
    def __init__(self):
        self.data = []

    def push(self, value):
        self.data.append(value)
        return len(self.data) - 1 # return the index of the item

    def peek(self):
        # Return the last value if the data array is not empty else
        # return None
        return self.data[-1] if len(self.data) > 0 else None

    def remove(self):
        # Here too when the user tries removing the last item, return
        # it if there are elements in the array else return None
        return self.data.pop() if len(self.data) > 0 else None
```

### Code Explanation

We define the Stack class; as previously stated, the stack is a data structure that you create and does not come pre-built in most programming languages.

In the`__init__` method, we create an empty array and attach it to the object. As you can see here, the stack we are implementing is based on the array data structure.

Next, we define the `push` method, the push method is responsible for inserting a new value onto a stack. This is accomplished by invoking the append method and passing in the user-supplied value. The append method adds to the end of the list, which is referred to as the ***TOP*** in a stack. The index of the last item is then returned.

Next, we define the `peek` method, the peek method simply returns the last item in the array if there are items in it; otherwise, it returns None.

The `remove` method is next. Here, we return the last item in the array. This is done by calling the pop() method on a list. This will remove the last item in the list and return it.

Let's quickly go through an example of this implementation.

```python
s1 = Stack()
s1.push(1) # This adds 1 to the stack
print(s1.peek()) # This prints out 1, since it's the item at the top
s1.push(2)
s1.push(3)
print(s1.peek()) # This prints out 3, since it's the latest item at the top

s1.remove()
print(s1.peek()) # this prints 2 since 3 has been removed from the stack
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699292885137/046bfb6d-0dd8-4f50-a38c-ba3c7a1912f5.png)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699293075698/604b1ac7-5d21-4d7e-b783-99569e389795.png)

As you can see from above, the LIFO behavior is working in full effect. The first item added will be the last item to leave.

## Real-world use cases

* **Browser Forward and Back Navigation**  
    Web browsers implement forward and back navigation using two stacks: the undo stack and the redo stack. As the user navigates between pages, the current URL is pushed onto the undo stack. Pressing the back button pops the URL from the undo stack and pushes it onto the redo stack, allowing the user to move backward and forward through their browsing history. This dual-stack system ensures efficient navigation between visited pages. This is a very simple breakdown; a lot gets built on this, though :D
    
* **Function Call Management**  
    In programming, a call stack is a stack data structure that controls a function call. When a function is called, its parameters, local variables, and return address are pushed onto the call stack. As functions complete execution, they are deleted from the stack, returning the program to the previous execution context. This is mostly used in recursive programming.
    
* **Solving Algorithmic Problems**  
    Several problems you will encounter will require some comprehension of stacks in order to solve them efficiently. Some include:
    
    * First-depth search problem
        
    * Reversing items in a list or string