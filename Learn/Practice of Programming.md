# Practice of Programming

Basic principle : Simplicity, Clarity, Generality, Automation

How to achieve these basic principles ?
**Simplicity** : Keep your Programs short and manageable. 
**Clarity**: Make sure your program are easy to understood. 
**Generality**: Your program work well in a broad range of situations and adapt well as new situation arises
**Automation**: Letting machine do the work for us. 

## Naming 
**Use descriptive names for globals, short names for locals.**
- The broader the scope of a variable, the more information should be conveyed by its name.
- Global functions and classes and structures should also have descriptive names.
- short names for local variable is sufficient.

> Using a long variable names regardless of context is mistake.

**Clarity is often achieved through bravity**

**Function names should be based on Active verbs**

```javascript
now = date.getTime();
putChar();

// Function returning boolean should be named so that return value is unambigous


```

## Rob Pikes 5 Rule of Programming

* **Rule 1.** You can't tell where a program is going to spend its time. Bottlenecks occur in surprising places, so don't try to second guess and put in a speed hack until you've proven that's where the bottleneck is.
    
* **Rule 2.** Measure. Don't tune for speed until you've measured, and even then don't unless one part of the code overwhelms the rest.
    
* **Rule 3.** Fancy algorithms are slow when n is small, and n is usually small. Fancy algorithms have big constants. Until you know that n is frequently going to be big, don't get fancy. (Even if n does get big, use Rule 2 first.)
    
* **Rule 4.** Fancy algorithms are buggier than simple ones, and they're much harder to implement. Use simple algorithms as well as simple data structures.
    
* **Rule 5.** Data dominates. If you've chosen the right data structures and organized things well, the algorithms will almost always be self-evident. Data structures, not algorithms, are central to programming.
