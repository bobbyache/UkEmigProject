
# Big O Examples

## Sequential operation on a single dataset

### Example X

There will be O(n) calls to pairSum. So time is O(n). These calls do not exist simmultaneously on the stack,
    so you only need O(1) of space.

```typescript
function pairSumSequence(n: number): number {
    let sum: number = 0;

    for (let i: number = 0; i < n; i++) {
        sum += pairSum(i, i + 1);
        // console.log(sum);
    }
    return sum;
}
```

If one were to measure `pairSum` it would be O(1). The values of the inputs do not change the time the function will take to run.

```typescript
function pairSum(a: number, b: number): number {
    return a + b;
}
```

### Example X

> Source: Cracking the Code Interview - Example 6

Below algorithm runs in O(n) time. The fact that it goes half way through the array does not impact big O time. Remember Big O is about **scale**.

```java
void reverse(int[] array) {
	for (int i = 0; i < array.length / 2; i++) {
		int other = array.length - i - 1;
		int temp = array[i];
		array[i] = array[other];
		array[other] = temp;
	}
}
```

## Sequential operations on different datasets

### Example 1
Since we cannot establish a relationship between `boxes1` and `boxes2` we must take both inputs into account in our answer.

```javascript
const boxes1 = [1,2,3,4,5];
const boxes2 = [5,7,8,9,10, 11, 12];

function compressBoxes(boxes1: number[], boxes2: number[]): void {
    boxes1.forEach(box => {
        console.log(`Box ${box} - Compressed`);
    });
    boxes2.forEach(box => {
        console.log(`Box ${box} - Compressed`);
    });
}

compressBoxes(boxes1, boxes2);
```

## Looping multiple times over the same dataset
N is the size of the array and in the following examples, both will take (roughly) the same amount of time to execute based on the size of the array. So the runtime is NOT O(2N)... you drop the constant "2", so in both cases it will always be O(N).

```javascript
function MinMax1(array)
{
	min, max = NULL
	
	foreach (c in array)    // O(n)
		min = MIN(c, min)
		
	foreach (c in array)    // O(n)
		max = MAX(c max)
}

function MinMax2(array)
{
	min, max = NULL
	
	foreach ( c in array)   // O(n)
		MIN(c, min)
		MAX(c,  max)
}
```

## Nesting operations on the same data

An outer and inner nested array operating on the same dataset has a runtime of$N^2$.

### Example 1
Square the size of the array. Will always evaluate to $O(n^2)$.

```javascript
const boxes = [1,2,3,4,5];

function logAllPairsInArray(boxes: number[]): void {
    for (let x: number = 0; x < boxes.length; x++) {
        for (let y: number = 0; y < boxes.length; y++) {
            console.log(`${boxes[x]}, ${boxes[y]}`);
        }
    }
}

logAllPairsInArray(boxes);
```

### Example 2

```javascript
const boxes = [1,2,3,4,5];

function logAllPairsInArray(boxes: number[]): void {
    boxes.forEach(firstBox => {
        boxes.forEach(secondBox => {
            console.log(`${firstBox}, ${secondBox}`);
        });
    });
}

logAllPairsInArray(boxes);
```

### Example 2

> Source: Cracking the Code Interview - Example 3

```javascript
function printUnorderedPairs(array) {
  for (let i = 0; i < array.length; i++) {
    for (let j = i + 1; j < array.length; j++) 			{
		// console.log(`${array[i]}, ${array[j]}`)
		console.log(`Indeces ${i}, ${j}`)
    }
  }
}

printUnorderedPairs([1, 2, 3, 4]);
```
#### Logical walk-through
There are $N^2$ possible total pairs (the loops are nested). And yet, roughly half of those will have i < j and the remaining half will have i > j. This code goes roughly $\frac{N^2}{2}$ pairs so it does $O(n^2)$ work. Since we remove all constants and non-dominant terms, we're left with `N(N)` which is $N^2$.

When visualized, looks like half of an $x(x)$ matrix which has size (roughly of $\frac{N^2}{2}$. So looking from an *average* perspective, the inner loop does half the work therefore one can also come to the conclusion that the total work of this loop is x which also brings one back to $O(n^2)$ work.

#### Mathematical reasoning
The sum of 1 through `N-1` is $\frac{N(N-1)}{2}$. This is simply a formula to sum integers 1 through `N`.

However, one can use this to get the `O(x)` of this function.

#### References

- Example: Cracking the Code Interview  - P630, Location 642.
- [Sum of first n natural numbers - Derivation of a formula](https://www.youtube.com/watch?v=aaFrAFZATKU).
- Cracking the Code Interview - P630, Location 642


## Nesting operations with unrelated datasets

### Example 1
> Source: Cracking the Code Interview - Example 4

Study the following code:

```javascript
function printUnorderedPairs(arrayA, arrayB) {
	for (let i = 0; i < arrayA.length; i++) {
		for (let j = 0; j < arrayB.length; j++) {
			console.log(`${arrayA[i]}, ${arrayB[j]}`);
		}
	}
}
```
Do you see the catch? There are two inputs here, so if you thought $O(n^2)$ you would be incorrect.

It's $O(ab)$ where `a` = Array A size, and `b` = Array B size.

```javascript
function printUnorderedPairs(arrayA, arrayB) {			// O(n)
	for (let i = 0; i < arrayA.length; i++) {			// O(n)
		for (let j = 0; j < arrayB.length; j++) {		// O(1)
			console.log(`${arrayA[i]}, ${arrayB[j]}`);
		}
	}
}
```

### Example 2
There are two different inputs at play here. There is no established relationship between A and B, so we have to keep both variables.

```javascript
function intersectionSize(arrayA, arrayB) {
	int count = 0;
	
	for (a in arrayA) {
		for (b in arrayB) {
			if (a == b)
				count = count + 1;
		}
	}
	return count
}
```

The answer is $O(a*b)$.

### Example 3
> Source: Cracking the Code Interview - Example 5

Study the following code:

```javascript
function printUnorderedPairs(arrayA, arrayB) {
	for (let i = 0; i < arrayA.length; i++) {
		for (let j = 0; j < arrayB.length; j++) {
			// This is constant
			for (let k = 0; k < 100000; k++) {
				console.log(`${arrayA[i]}, ${arrayB[j]}`);
			}
		}
	}
}
```

What's the Big O? It's $O(ab)$ where `a` = Array A size and `b` = Array B size. The long running code in the deep nested loop will run at a constant time. The size of the arrays are what really add time to the runtime, and we are measuring scalability!

## Dropping the non-dominant terms

Study the following code:

```javascript
function WhyWouldIDoThis(array)
{
	max = NULL
	
	// O(n)
	foreach(a in array)
	{
		max = MAX(a, max)
	}
	print max
	
	// O(n^2)
	foreach(a in array)
	{
		foreach(b in array)
		{
			print a,b
		}
    }
}
```
Perhaps you're tempted to answer $O(n + n^2)$ because of the two loops at play. However, in this case the runtime will be $O(n^2)$ as we always drop the non-dominant terms.

Why? We're measuring scalability, and as the data grows the first loop will become less and less consequential in the overall picture as the dominant runtime eats up the time.


## Recursive Operations

### Example 1

> Source: Cracking the Code Interview - Recursive runtimes

Examine this code.

```javascript
function sum(n: number): number {
    if (n <= 0) return 0;
    console.log(n);
    return n + sum(n - 1);
}
```

Firstly, draw the tree structure of the recursive calls. Examine it and take particular interest in the no. of levels (depth) and the number of branches from each node. 

How many calls are in the tree. Each node (function call) has two children. The tree will have a depth of N and each level will have twice as many calls as the one above it.

- N = depth of tree (no. of levels)
- A node has 2 brances

There will be $2^0 + 2^1 + 2^3 + 2^4 + ... + 2^N$ nodes.

A function like this will take $O(2^N)$ of time.
It will only take $O(n)$ space because only a part of the tree will be loaded into the stack at any one time. 

## Internal Functions and Properties

> Source: Cracking the Code Interview
> 
If you're presented with something like this. What is the answer?

```javascript
'34834547dfkfddskdfdsf'.length // what is the Big O?
```
The answer is that you can't know unless you know about the internal implementation. How does the language calculate length? For JavaScript and C# it is a built in property O(1). Some languages may calculate it differently.

## Simplifying Big O runtimes

> Source: Cracking the Code Interview - Example 7

Which of the following are equivalent to O(N)? Why?

- O(N + P), where P < $\frac{N}{2}$
- O(2N)
- O(N = log N)
- O(N + M)
  
Hint: Remember to think about the following:

- Drop the constants
- Drop the non-dominant terms
- What are the inputs? Is there a relationship between them?

### Answers

> O(N + P), where P < $\frac{N}{2}$

If P < $\frac{N}{2}$ we know that N is the dominant term so we can drop the O(P). So yes, this is equivalent of O(n).

> O(2N)

O(2N) is O(n) since we drop constants.

> O(N = log N)

O(N) dominates O(log N), so we can drop the O(log N).

> O(N + M)

There is no established relationship between N and M, so we have to keep both variables in there. Therefore, all but the last one are equivalent to O(N).  