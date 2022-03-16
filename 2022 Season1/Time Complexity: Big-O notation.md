# Time Complexity: Big-O Notation

## Table of Contents

- [Introduction](#introduction)
- [Virtual Machine, Pseudo-Language, Pseudo-Code](#virtual-machine-pseudo-language-pseudo-code)
- [Time Complexity](#time-complexity)
- [Worst-case Time Complexity and Big-O Notation](#worst-case-time-complexity-and-big-o-notation)

## Introduction

Today, I will talk about the time complexity, Big-O notation. First, there are some backgrounds on how the Big-O notation appears. Thus, I'll describe components of it, such as a virtual machine. Second, we measure the time complexity to compare with Big-O notation and understand why it appears.

## Virtual Machine, Pseudo-Language, Pseudo-Code

Developers measure the performance of algorithms and data structures with time complexity. Thus, they can use Python or Java and such programming languages to calculate the execution time but should integrate any environments such as hardware and software to get accurate performance.

Consequently, developers use a virtual machine to measure the performance with the isolated computational model. The modern computer architecture follows Von Neumann's based on the Turing Machine, and the most used virtual machine model is the Random Access Machine, RAM. As a lighter note, and as you know, RAM also refers to Random Access Memory. Both are similar, but, as you can guess, the machine contains the concept of memory.

Random Access Machine comprises three things: CPU, memory, and primitive operation. CPU executes operations and commands. The memory consists of unlimited registers that can save any number. Primitive operation is a set of operations performed during a unit time—for example, an assignment operator, arithmetic operator, etc.

Pseudo language is a kind of programming languages like Python and Java but is much more straightforward. So then, pseudo-code is a code written by pseudo-language.

## Time Complexity

Now check the below pseudo-code and count the primitive operation executions if `A` equals an array sorted `4`, `1`, `5`, `3`, `9`, `10`, and `8`, and `n` equals `7`. The answer is `10` because there is one count when the `currentMax` value is assigned by an element indexed `0` in array `A`. The `if` conditional statement also increases count because this is a comparison operation which means a primitive operator. Finally, if `currentMax` is smaller than an element indexed `i`, which is increased from `1` to `n - 1` by for loop in the array `A`, it increased count twice to check the `if` conditional statement and assign a value from the array element to variable `currentMax`.

As a result, an element `4` in the array `A` is assigned to variable `currentMax`, which increases the primitive operation count. `1` is smaller than `currentMax`, which is `4`, so it increases primitive operation count once. `5` is bigger than `currentMax`, so it increases primitive operation twice, and now `currentMax` is `5`.

```
algorithm arrayMax(A, n)
	currentMax = A[0]
	for i = 1 to n-1 do
		if currentMax < A[i]
			currentMax = A[i]
	return currentMax
```

We suppose to simulate this pseudo-code in the virtual machine. However, infinite inputs can make it impossible to calculate the performance average. It is why the worst-case time complexity appears, and this concept is the base of Big-O notation.

## Worst-case Time Complexity and Big-O Notation

There are two examples of pseudo-codes below. I won’t describe details as I did above.

The below code is executed in the worst-case if all elements in an array `A` is an even number. The worst-case time complexity is $4n + 1$.

```
algorithm evenNumSum(A, n)
	sum = 0
	for i = 0 to n-1 do
		if A[i] % 2 == 0 do
			sum += A[i]
	return sum
```

The below code is always executed in the worst-case. The worst-case time complexity is $3/2*n(n-1)+1$.

```
algorithm arraySum(A, B, n)
	sum = 0
	for i = 0 to n-1 do
		for j = i to n-1 do
			sum = sum + A[i] * B[j]
	return sum
```

It is essential to measure the worst-case time complexity if you need to develop on the very safety domains such as a program in a satellite or need to control the real-time. However, most cases are enough only to calculate a rate of growth. It is why the Big-O notation appears.

Big-O notation is also called an asymptotic notation because it omits all except the dominant terms. Hence, the above time complexities are $O(n)$ and $O(n^2)$.
