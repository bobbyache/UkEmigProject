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