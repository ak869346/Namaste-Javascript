# 1. EveryThing in JavaScript happens inside an Execution Context.

There are two components of this Execution Context 
   1. Memory Component (Variable Envirnment) - Variable and Functions are stored as key value pairs.
   2. Code Component (Thread of Execution) - Where all code is executed one line at a time.

# Execution context is created in two phases:-
    1. Memory creation phase.
        For Vaiable it allocate a value undefined and for function it allocated full function code.
    2. Code Creation phase.
        WhenEver a function is invoked a brand new execution context is created.

# 2. JavaScript is a synchronous single threaded language.
    1. single threaded - Execute one command at a time.
    2. synchronous - executed in specific order means it will go to the next line once the current line execution is finished.

# Example

Var n = 2;
function square(n) {
    return n*n;
}
console.log(square(n));

# Explanation 

1. **Code Creation Phase**:
   - JavaScript engine reads and prepares the code, performs variable and function declarations hoisting.
   - No execution yet.

   [ Global Execution Context (during code creation) ]
   - n (undefined) // Variable declaration hoisted, but not assigned yet
   - function square(n) { ... } // Function declaration hoisted

---

2. **Memory Creation Phase**:
   - Memory is allocated for variables and functions, and initial values are set (undefined for variables).

   [ Global Execution Context (memory creation) ]
   - n = undefined // Variable `n` is hoisted with undefined value
   - function square(n) { ... } // Function `square` is stored in memory

---

3. **Global Execution Context (GEC) starts executing**:
   - The code starts executing line by line, starting with variable assignment.

   [ Global Execution Context (after `var n = 2;` executes) ]
   - n = 2
   - function square(n) { ... }

---

4. **Function Execution Context (FEC) when `square(n)` is called**:
   - A new function execution context is created, and the parameter `n` is passed the value `2`.

   [ Function Execution Context (square) ]
   - n = 2 // Parameter passed to the function
   - return n * n  // Computation: 2 * 2 = 4

---

5. **After function execution completes**:
   - The result `4` is returned, and the function execution context is popped off the stack.

   [ Global Execution Context (after function returns) ]
   - n = 2
   - function square(n) { ... }
   - Result of square(n): 4 (passed to console.log)

---

6. **Final Execution**:
   - `console.log(4)` is executed and outputs `4`.

   [ Global Execution Context (Final) ]
   - n = 2
   - function square(n) { ... }
   - Result of square(n): 4

# 3. Call Stack Manage the order of execution of execution contexts.

 Management of all these Execution Context by JS Engine.
 JS Engine use call stack to manage all these execution context.
    -> Everytime at the bottom of call stack Global Execution Context is present.

