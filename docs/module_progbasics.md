
# **Programming Basics questions**
## **Computer science**
### **Data structures**
#### **What is the purpose of the array (list in some programming languages) data structure? Name some methods of it!**
The Array object, as with arrays in other programming languages, enables storing a collection of multiple items under a single variable name.

In JavaScript, arrays aren't primitives but are instead Array objects, and have members for performing common array operations. JavaScript arrays are resizable and can contain a mix of different data types.

JavaScript arrays must be accessed using nonnegative integers (or their respective string form) as indexes (the first index is [0]).

Some Array methods:

- push() - adds an element at the end of the list (and returns the new length of the array)
- forEach() - Calls a function for each element in the calling array
- splice() - removes or replaces one or more element of the list from the specified index
- filter() - removes an element with a certain value
- reduce() - executes a user-supplied "reducer" callback function on each element of the array (from left to right), to reduce it to a single value
- sort() - sorts the elements of an array in place

#### **What are the differences between a list/array and a set?**
A set is a collection which is unordered, unchangeable\*, and unindexed, doesn't allow duplicate values, and can only contain immutable data types. While list/array items are ordered, changeable/mutable, allow duplicate values, and can contain any data types.

*\*can't change the items' value in a set, however can add or remove from a set*
#### **What are the purpose and some methods of a dictionary/map data structure (simple data objects in JavaScript)?**

In JavaScript, an object is a standalone entity, with properties and type. A property of an object can be explained as a variable that is attached to the object. You access the properties of an object with a simple dot-notation. Like all JavaScript variables, both the object name (which could be a normal variable) and property name are case sensitive. You can define a property by assigning it a value.

Some Object methods:

- Object.create() - creates a new object, using an existing object as the prototype of the newly created object.
- Object.entries() - returns an array of a given object's own enumerable string-keyed property [key, value] pairs
- Object.assign() - copies all enumerable own properties from one or more source objects to a target object. It returns the modified target object
- Object.values() - returns an array of a given object's own enumerable property values, in the same order as that provided by a for...in loop
#### **Algorithms**

#### **Write a method (or pseudocode) that generates the Fibonacci sequence.**
```JS
 function F(n)
 if (n *equal to* 0) then
 return 0
 if (n *equal to* 1) then
 return 1
 else  return F(n-1) + F(n-2)
```

#### **How do you find a max value in a list/array if you can’t use any built-in functions or methods?**
```JS
function biggestNumberInArray (arr) {
// First a variable needed for the largest number with value: null

let largest = null;

// The loop iterate through the array

for (let i = 0; i < arr.length; i++) {
// Compares stored number with current number of array, stores the largest one
    if (arr[i] > largest){ 
    largest = number}
}
return largest;
}
```


#### **How do you find the average of values in a list/array if you can’t use any built-in functions or methods?**
```JS
let total = 0;

for(let i = 0; i < grades.length; i++) {
    total += grades[i];
}

let avg = total / grades.length;
```

#### **What do we call an in-place sort?**
An in-place algorithm is an algorithm that does not need an extra space and produces an output in the same memory that contains the data by transforming the input ‘in-place’. However, a small constant extra space used for variables is allowed.
#### **Explain an algorithm which sorts a list!**
A bubble-sort algorithm iterates through the given list, and compares each element's value to the next element's value. Given the list is to be sorted in ascending order, the algorithm switches the elements' places every time an element's value is greater than the value of the next element. The process is repeated until the entire array is sorted.

### **Programming paradigms - procedural**
#### **Explain the characteristics of the procedural programming paradigm.**
Procedural programming is a programming paradigm built around the idea that programs are sequences of instructions to be executed. They focus heavily on splitting up programs into named sets of instructions called procedures, analogous to functions. A procedure can store local data that is not accessible from outside the procedure's scope and can also access and modify global data variables.
#### **What is the call stack?**
A call stack is a mechanism for an interpreter (like the JavaScript interpreter in a web browser) to keep track of its place in a script that calls multiple functions — what function is currently being run and what functions are called from within that function, etc.

When a script calls a function, the interpreter adds it to the call stack and then starts carrying out the function.

Any functions that are called by that function are added to the call stack further up, and run where their calls are reached.

When the current function is finished, the interpreter takes it off the stack and resumes execution where it left off in the last code listing.

If the stack takes up more space than it was assigned, a "stack overflow" error is thrown.

#### **What is "stack overflow"?**
A stack overflow is a programming error when too much memory is used on the call stack. A stack overflow occurs for example when there is a recursive function (a function that calls itself) without an exit point. The browser/hosting environment has a maximum stack call that it can accomodate before throwing a stack error.
#### **What are the main parts of a function?**

- the function keyword
- an optional name ( this is also because it can be anonymous )
- a list of parameters names enclosed in parentheses
- the statement enclosed in braces
#### **What is the difference between parameters and arguments?**
Function parameters are the variables that are defined when the function is declared (the names listed in the function's definition). Function arguments are the real values passed to the function (declared within a function when the function is called). Parameters are initialized to the values of the arguments supplied. 

*argument -  a value provided as input to a function*

*parameter - a variable identifier provided as input to a function*

### **Programming languages - JavaScript**
#### **What does it mean that a type is immutable? Tell examples.**
Immutable data cannot be changed once created. In JavaScript String and Numbers are immutable data types.
#### **What does it mean that an object is mutable? Tell examples.**
Mutability describes whether the state of a value can be modified after its declaration or not. Take an example that we have a variable, and we assign a value to it. Later if we need to modify the value of this variable, and we change it, then changing its state, the object is considered to be mutable. 

In JavaScript, objects and arrays are mutable by default: they are addressed by reference, not by value. 

Example: 

```JS
// If person is an object, the following statement will not create a copy of person:

const x = person;  // Will not create a copy of person.

// The object x is not a copy of person. It **is** person. Both x and person are the same object.

// Any changes to x will also change person, because x and person are the same object.

const person = {

firstName:"John",

lastName:"Doe",

age:50, eyeColor:"blue"

}

const x = person;

x.age = 10;      // Will change both x.age and person.age

```

#### **What is a conditional expression?**
Conditional statements control behavior in JavaScript and determine whether or not pieces of code can run.

Conditional expressions return different values based on the result of the boolean expression specified by the programmer (based on the condition being true or false). The result of boolean expression is either True or False. e.g if..else, while, ternary operator

#### **What are different types of arguments?**
An argument is a variable or value passed to a function as input. There are two types of arguments such as **positional arguments** and **key arguments**.

*argument -  a value provided as input to a function*

JavaScript functions do not perform type checking on the passed arguments

*parameter - a variable identifier provided as input to a function*

JavaScript function definitions do not specify data types for parameters


#### **What is variable shadowing?**
Variable shadowing refers to the practice of naming two variables — for example, a global and a local variable or a local variable and a callback function parameter — with the same name and within scopes that overlap. The variable scoping rule states that inner scope can access variables defined in the outer scope.

#### **What can happen if you try to delete/add an item from/to a list, while you are iterating over it?**
With push/unshift: The iteration continues without an issue, calculating with the original list length. With pop/shift: The loop stops before it’s done(because of index failure), with a  result of a mangled array.
#### **If you need to access the iterator variable after a for loop, how would you do it?**
Just assign it to another variable inside the for loop and the new variable can be used afterwards outside the for loop.
#### **What type of elements can a list contain?**
JavaScript arrays can indeed contain any and all types of data. An array may contain other objects (including other arrays) as well as any number of primitive values like strings, null , and undefined . When you place an object inside of another object, it's called a nested object.
#### **What can the + operator be used for?**
\+	perform mathematical operations between numeric operands (addition)

++	Increment operator increase operand value by one

+= 	Sums up left and right operand values and assigns the result to the left operand

\+ 	also perform concatenation operation when one of the operands is of string type
#### **What is string formatting?**
String formatting is the process of inserting variables into a string. In modern languages generally, it is done by using the {} brackets. It is also called string interpolation.

In javascript, there is no built-in string formatting function. But there are other ways to format a string:

- Using {} brackets within backticks ``

Formatting string in javascript is best done by the use of backticks (``) and the placeholder variables are inserted within the backticks wrapped in curly braces ({}) preceded by a dollar sign ($).

Example: `Hello ${name}`

- Using + operator to concatenating the string with the variables

This replaces the variable with the value and concatenates it with the string.

`	`Example: 'Hello' + name + '!'

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

Also JavaScript has many string methods you can use to format strings:

toLowerCase() - convert strings to their lowercase version

toUpperCase()- convert strings to their uppercase version.

replace() - replace a section of a string with a substring

trim() - modifies strings by removing whitespaces from the beginning and end of a string

split() - takes a pattern and divides a String into an ordered list of substrings

replace() - returns a new string with one, some, or all matches of a pattern replaced by a replacement

etc.

#### **Name 4 iterable types.**
String, Array, TypedArray, Map, Set, and Intl.Segments are all built-in iterables, because each of their prototype objects implements an @@iterator method. 
#### **Does the order of the function definitions matter? Why?**
Hoisting is JavaScript's default behavior of moving declarations to the top of the current scope.

Hoisting applies to variable declarations and to function declarations.

Because of this, JavaScript functions can be called before they are declared.



#### **What is spread/rest syntax for?**
The rest parameter syntax allows a function to accept an indefinite number of arguments as an array, providing a way to represent variadic functions in JavaScript.

Spread syntax can be used when all elements from an object or array need to be included in a new array or object, or should be applied one-by-one in a function call's arguments list.

Spread syntax looks exactly like rest syntax. In a way, spread syntax is the opposite of rest syntax. Spread syntax "expands" an array into its elements, while rest syntax collects multiple elements and "condenses" them into a single element.

rest syntax example: foo(arg1, arg2, **...manyMoreArg**)

spread syntax example: [1, **...iterableObj**, '4', 'five', 6]
#### **What does a destructuring assignment mean?**
Destructuring Assignment is a JavaScript expression that allows to unpack values from arrays, or properties from objects, into distinct variables. 
#### **What happens when you try to assign the result of a function which has no return statement to a variable?**
The variable will give back undefined as well.
## **Software engineering**
### **Debugging**
#### **What techniques can you use while debugging a program?**
Using console.log()/console.table() etc.

Adding test cases

Using the IDE's debugging tools

Asking other developers/team members for help
#### **What does step over, step into and step out mean when using the debugger?**
Step in: means that if there is a function call, it goes inside the function and you can see how the function is executing line by line till it returns and you go back to the next line right after the function call.

Step over: means that if there is a function call, it just executes it like a black box and returns the result, but you cannot see how the function was executed.

Step out: means that if you have Stepped in a function and now you want to skip seeing how the rest of the function is going to execute, you Step out and the function returns. Then, you go back to the next line, that is the line right after the function call.

#### **How can you start to debug a program from a certain line using the debugger?**
Add a breakpoint, then start debugging (press Fn + F5 -> Continue)
### **Version control**
#### **What are the advantages of using a version control system?**
Strong support for non-linear development (which allows you to work on different parts of a system concurrently).

Distributed development allows for multiple people to be working on the same project at the same time.

Everything saved in git is accessible later.
#### **What is the difference between the working directory, the staging area and the repository in git?**
The Working Tree is the area where you are currently working, it is untracked. 

The Staging Area is when git starts tracking and saving changes that occur in files. These saved changes reflect in the .git directory.

The Local Repository is everything in the .git directory: all of the checkpoints or commits. It is the area that saves everything.
#### **What are remote repositories in git?**
Remote repositories are versions of a project that are hosted on the Internet for example on GitHub. Collaborating with others involves managing these remote repositories, pushing and pulling data to and from them when you need to share work.
#### **Why does a merge conflict occur?**
If you’ve changed the same part of the same file differently in the two branches you’re merging, Git won’t be able to merge them cleanly. Git doesn’t automatically create a new merge commit. It pauses the process while you resolve the conflict. If you want to see which files are unmerged at any point after a merge conflict, you can run git status.

#### **Through what series of commands could you put a new file into a remote repository connected to your existing local repository?**
$ git pull // it is recommended to pull to synchronize any meantime changes before pushing

$ git add <file>

$ git commit -m "<descriptive message>"

$ git push -u origin <branch>
#### **What does atomic commits and descriptive commit messages mean?**
Atomic commits are what they sound like: atomic (very small).  Every commit pertains to one fix or feature.

Descriptive commit messages: When the commit messages are meaningful, concise and easy to read.

You/ or others should understand what you were working on, just by reading the commit message

Usually use present tense, like: remove unused imports, add hamburger menu for mobile ui

#### **What’s the difference between Git and GitHub?**
Git is the version control software, and Github is a git repository hosting service which offers all the source code management provided in git. Github is where you upload your git repository (it is simply a convenient website to backup and share your repositories, via the git protocol).
## **Software design**
### **Clean code**
#### **What does clean code mean?**
Code is clean if it can be understood easily – by everyone on the team. Clean code can be read and enhanced by a developer other than its original author. With understandability comes readability, changeability, extensibility and maintainability.
#### **What steps do we usually do during a clean code refactoring?**
First we need to try and understand the code.

Write down ideas on how to improve the code - check for repeated code,dead code, bad variable names, global variables, magic numbers etc.

Act on the notes, check that the code works the same way at every little change/step

In the end, the code should be free of clutter, complexity and cleverness.
### **Error handling**
#### **What is error/exception handling?**
An exception is an error that happens during execution of a program. When that error occurs, Python generates an exception that can be handled, which avoids your program to crash.
#### **What are the basics of exception handling in JavaScript?**
Try-catch allows you to gracefully handle errors or exceptions in your code.

If the try block runs to failure, it jumps to the except block rather than crashing. The except block contains the logic that deals with the exception gracefully. If there is a finally block, the code in it always runs, doesn't matter if there was an error or not.


#### **In which case should we catch an exception? Why?**
We should catch only well defined, foreseeable exceptions to maintain flow control. Defining broader exceptions may cause the program to not work as expected.
#### **What can/should we do with an exception in the catch block?**
We should tell the program how to continue executing our code. E.g. to print a meaningful error message, or quit the programme if needed.
#### **What does the finally statement do in a try-catch block in JavaScript?**
catch block: Will be executed only if the code inside the try block doesn’t generate an exception.

finally block: Code is always executed, whether the program executed properly or it raised an exception.

####
####
####


