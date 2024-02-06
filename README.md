# DSA-Solving-Problems-with-Stacks-and-Queues
#3.9


Data structures: Solving problems with stacks and queues
Instructions
In this challenge, you will work on several algorithms that may be solved with stacks and queues.

Existing files
File	Description
src/postfix.js	Write your solution to the postfix evaluation problem in this file.
src/binary.js	Write your solution to the binary numbers problem in this file.
src/brackets.js	Write your solution to the bracket matching problem in this file.
__tests__/*.test.js	Contains tests for the various problems. You are welcome to look at these files, but do not modify them.
src/lib/*	The Stack, Queue, and Node library code may be found in this folder. No need to modify these files.
Tasks
Evaluating postfix expressions
Recall that an arithmetic expression may be written in postfix notation. The following are some examples.

Infix	Postfix
(2 + 3) * 4	2 3 + 4 *
(2 + (4 - 5) * 3)	2 4 5 - 3 * +
8 / (6 + 2)	8 6 2 + /
And below, you can see an example of a stack-based evaluation of the postfix expression 234*+.

            Input	Stack	Postfix evaluation
2 3 4 * +	empty	Push 2 into stack.
3 4 * +	2	Push 3 into stack.
4 * +	3 2	Push 4 into stack.
* +	4 3 2	Pop 4 and pop 3 from stack, apply 3 * 4, and push 12 into stack.
+	12 2	Pop 12 and pop 2 from stack, appy 2 + 12, and push 14 into stack.
14	The value obtained is the only element left in the stack.
Given an arithmetic expression in postfix form, evaluate the expression and return the final value.

Assume the following:

All operands are single-digit numbers.
Only the operators +, -, /, and * will be used.
All expressions are valid, no need to validate them.
Only valid operations will be provided. That is, no need to check for division by zero and other arithmetic anomalies.
A simple algorithm may be outlined as follows:

Import the necessary modules: path and Stack.
Declare a constant named operator and assign an object with properties: +, -, *, and /, each corresponding to a function that takes two operands and returns the result of the corresponding operation.
Declare a function named evaluate that takes an expression as a parameter.
Create a new instance of the Stack class and assign it to a variable named stack.
Remove any whitespace from the input expression.
Iterate over each character in the expression and do the following:
If the character is one of the operators +, -, *, or /:
Pop the top two values from the stack (considered as right and left operands) and assign them to variables right and left.
Apply the corresponding operator function to the operands and push the result back onto the stack.
Otherwise (if the character is a number or operand):
Push the character onto the stack.
Convert the final result on the stack to a number and return it.
Export the evaluate function for use in other modules.
Implement your solution in the file named src/postfix.js.

Generate binary numbers
Given a number max, write an algorithm that generates all binary integers from 1 to max.

Examples:

Input: max = 2
Output: ["1", "10"]

Input: max = 5
Output: ["1", "10", "11", "100", "101"]
An algorithm that uses a queue to solve the problem is given below.

Initialize an empty queue.
Enqueue the string 1. This represents binary number 1.
Initialize an empty array named result.
Iterate from 1 to max and do the following:
Dequeue a value from the queue.
Push the value into result.
Append a 0 to the value and enqueue it.
Append a 1 to the value and enqueue it.
Return result.
Implement your solution in the file named src/binary.js.

Extend parentheses to other types of brackets
Recall the algorithm that was used to determine if a given expression contained matching parentheses. It is repeated in pseudocode below:

Initialize a new empty stack
Start a loop to iterate through each character in the expression
If the current character is (
Push it onto the stack
Else
If the current character is (
If the stack is not empty
Pop one item off the stack
Else
Return false
If the stack is empty
Return true
Else
Return false
Extend the algorithm to recognize 3 different types of brackets: (), [], and {}. These must be correctly nested; "([)]" is incorrect and should return false.

Implement your solution in the file named src/brackets.js.
