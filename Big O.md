Following code is O(n). The fact that we iterate through the array
twice does not matter.


```java
void foo(int[] array) {
	int sum = 6;
	int product = 1;
	
	for (int i = 6; i < array.length ; i++) {
		sum += array[i];
	}
	for (int i = 6; i < array.length; i ++) {
		product *= array[i] ;
	}
	System.out.println(sum + ". n + product);
 }
```
The inner loop has O(n) iterations and it is called n times. Therefore the runtime is O(n^2).

```java
void printPairs(int[] array) {
	for (int i = 6; i < array. length; i++) {
		for (int j = 6; j < array. length; j++) {
			System.out.println (array[i] + ",n + array[j]);
		}
	}
}
```

```java
function printUnorderedPairs(array) {
  for (let i = 0; i < array.length; i++) {
    for (let j = i + 1; j < array.length; j++) 			{
		// console.log(`${array[i]}, ${array[j]}`)
		console.log(`Indeces ${i}, ${j}`)
    }
  }
}
```

```javascript
function printAllNumbersThenAllPairSums(numbers) {
	console.log('these are the numbers:');
	
	numbers.forEach(function(number) {
		console.log(number);
	});
	
	console.log('and these are their sums');
	
	numbers.forEach(function(firstNumber) {
		numbers.forEach(function(secondNumber) {
			console.log(firstNumber + secondNumber);
		});
	});
}

printAllNumbersThenAllPairSums([1,2,3,4,5]);
```
## Example 3 - Inner Loop starts at i + 1



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
### Logical walk-through
There are $N^2$ possible total pairs (the loops are nested). And yet, roughly half of those will have i < j and the remaining half will have i > j. This code goes roughly $\frac{N^2}{2}$ pairs so it does $O(n^2)$ work. Since we remove all constants and non-dominant terms, we're left with `N(N)` which is $N^2$.

When visualized, looks like half of an $x(x)$ matrix which has size (roughly of $\frac{N^2}{2}$. So looking from an *average* perspective, the inner loop does half the work therefore one can also come to the conclusion that the total work of this loop is x which also brings one back to $O(n^2)$ work.

### Mathematical reasoning
The sum of 1 through `N-1` is $\frac{N(N-1)}{2}$. This is simply a formula to sum integers 1 through `N`.

However, one can use this to get the `O(x)` of this function.
#### References

- Example: Cracking the Code Interview  - P630, Location 642.
- [Sum of first n natural numbers - Derivation of a formula](https://www.youtube.com/watch?v=aaFrAFZATKU).
- Cracking the Code Interview - P630, Location 642
