
# Common Runtimes

<a href="https://www.codecogs.com/eqnedit.php?latex=O(n)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?O(n)" title="O(n)" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=O(1)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?O(1)" title="O(1)" /></a>


<a href="https://www.codecogs.com/eqnedit.php?latex=O(log&space;N)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?O(log&space;N)" title="O(log N)" /></a>


<a href="https://www.codecogs.com/eqnedit.php?latex=O(N^2)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?O(N^2)" title="O(N^2)" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=O(ab)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?O(ab)" title="O(ab)" /></a>


<a href="https://www.codecogs.com/eqnedit.php?latex=O(N&space;log&space;N)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?O(N&space;log&space;N)" title="O(N log N)" /></a>


<a href="https://www.codecogs.com/eqnedit.php?latex=O(A&space;&plus;&space;B)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?O(A&space;&plus;&space;B)" title="O(A + B)" /></a>

# Important

Any programmer can solve a problem given time... what matters is how well the problem is solved. Big O tells us how well the problem is solved.

Good code is `readable` and `scalable`.

- Terms for Big-O:
  - Complexity
  - Time Complexity
  - Algorithmic Complexity
  - Asymptotic Complexity

- We are measuring **scalability**.

To do a simple performannce test with JavaScript one could use.

```javascript
(function performanceTest() {
  const t0 = performance.now();
  for (let i = 0; i < 100000; i++) {
    console.log(i);
  }
  const  let t1 = performance.now()
  console.log(t1 - t0);
})();
```

This test only tells us how fast the code runs on this dataset on this machine. But this might run faster on another machine, it might run slower. One might have a super duper computer that runs really fast with the datasets that we provide it. When the code goes out in the real world, it might not run as well with larger datasets on slower computers.

> Big O - How much does your code slow as your data grows.

## Thought Process
- Identify your code
- Identify N
- Count the steps in a typical run
- Keep the most significant part

# Big O Rule Book

- **Rule 1:** Worse Case
- **Rule 2:** Remove Constants
- **Rule 3:** Different terms for inputs
- **Rule 4:** Drop Non Dominants

# Runtimes

## Constant Time - O(1)


## Linear Time O(N)

As the number of inputs increase, so do the number of operations.

Take a real life example as in you're reading a novel. If someone asked you to keep reading until you find the first occurence of horse in novel, you'd read every word until you come across the word horse, and then you'd stop. However, the worst case scenario is that the first and last occurence of the word horse is the last word in the novel. Since we have to take the worst case scenario into account, this equates to $O(n)$.


## O(log N)

Take a real life example of an encyclopedia. Open it in the middle, if the word you're looking for is earlier in the book you do another divide and conquer until you find the word horse. If I give you a book twice as large, you're going to perform one more divide and conquer step to find it. This equates to O(n log N).

## Quadratic Time - O(N^2)

### What to look for in code
You're looking for nested loops on the same data. Something like this...
```javascript
function func(array) {
  for (let i = 0; i < array.length; i++) {
    for (let j = i + 1; j < array.length; j++) 			{
        ...
}
```