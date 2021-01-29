
# Important

- Terms for Big-O:
  - Complexity
  - Time Complexity
  - Algorithmic Complexity
  - Asymptotic Complexity

- We are measuring **scalability**.

## Thought Process
- Identify your code
- Identify N
- Count the steps in a typical run
- Keep the most significant part

# Runtimes

## Constant Time - O(1)


## Linear Time O(N)
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