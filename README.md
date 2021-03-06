<div align="center">
    <img src="https://res.cloudinary.com/dddnhychw/image/upload/v1598718831/Icons/JS_eqbfi5.png" alt="JavaScript Banner" width="500"/>
</div>

## Summary
With this respository, I am solving Algorithms in JavaScript with notes including Big O time complexity analyisis. I am also writing tests for my solutions with Jest.

### Core Concepts
- Iterative vs Recursive
- Variables/Pointers Manipulation
- Binary Search
- Hashmap
- Stack
- Array
- Linked List
- Sorting
- Depth First Search
- Breadth First Search
- Memoization


## Big O Notes Table of Contents


- [Drop the Constants](#drop-the-constants)
- [Drop Non Dominant Terms](#drop-non-dominant-terms)
- [Multi Part Algorithms](#multi-part-algorithms-add-vs-multiply)
- [Log N Runtimes](#log-n-runtimes)
- [Recursive Run Times](#recursive-run-times)
- [Loop Through Two Inputs Of Varying Length](#loop-through-two-inputs-of-varying-length)

## Run Times

- O(1) Constant Time
- O(n) Linear Time
- O(n^2) Quadratic Time
- O(n^3)	Cubic Time
- O(2^n) Exponential Time
- O(log n) Logarithmic Time
- O(n log n) Linearithmic Time
- O(n!) Factorial Time

## Drop The Constants

> O(2n) is O(n)

```JavaScript
const printAllItemsTwice = (arr, size) =>  {
    for(let i = 0; i < size; i++) {
        console.log(arr[i]);
    }

    for(let j = 0; j < size; j++) {
        console.log(arr[j]);
    }
}
```

> O(1 + n/2 + 100) becomes O(n)

```JavaScript
const printFirstItemThenFirstHalfThenSayHi100Times = (arr, size) => {
    console.log("First element of array:", arr[0]);

    for (let i = 0; i < size/2; i++) {
        console.log(arr[i]);
    }

    for (let j = 0; j < 100; j++) {
        console.log("Hi");
    }
}
```

## Drop Non-Dominant Terms
- O(n^2 + n) becomes O(n^2)
- O(n + log n) becomes O(n)
- O(5 * 2^n + 1000n^100) becomes O(2^n)

## Multi Part Algorithms Add vs. Multiply

### Add the Runtimes
If your algorithm is in the form "do this, then, when you're all done, do that" then you add the run times.

> O(A + B)

```JavaScript
let array1 = [1, 2, 3];
let array2 = [2, 3, 4];

for (let i = 0; i < array1.length; i++) {
    console.log(array1[i]);
}

for (let value of array2) {
    console.log(value);
}
```

> O(A + B)

```Java
int[] arrA = {1, 2, 3};
int[] arrB = {4, 5, 6};

for (int a : arrA) {
    print(a);
}

for (int b : arrB) {
    print(b);
}

```

### Multiply the Runtimes
If your algorithm is in the form "do this for each time you do that" then you multiply the runtimes.

> 0(A * B)

```JavaScript
let array1 = [1, 2, 3];
let array2 = [2, 3, 4];

for (let i = 0; i < array1.length; i++) {
    for (let j = 0; j < array2.length; j++) {
        console.log(`${i}, ${j}`);
    }
}
```

> 0(A * B)

``` Java
//Example 1
int[] arrA = {1, 2, 3};
int[] arrB = {4, 5, 6};

for (int a : arrA) {
    for (int b : arrB) {
        print(a + ", " + b);
    }
}

// Example 2
char[] arrC = {"a", "b" };
char[] arrD = {"c", "d"};

for (int j = 0; j < arrC.length; j++) {
    for (int k = 0; k < arrD.length; k++) {
        print(j + ", " + k);
    }
}

```
## Log N Runtimes

> O(log n)

```JavaScript
/*
Write function that takes input values(a sorted array) and n (an integer) and find the index of integer in sorted array;
If the integer is not in the array return -1;
*/
const binarySearch = (values, n) => {
    let left = 0;
    let right = values.length - 1;

    while(left < right) {
        let midIndex = Math.floor((left + right)/2);
        if(values[midIndex] === n) return midIndex;

        if(values[midIndex] < n) {
            left = midIndex + 1;
        } else {
            right = midIndex - 1;
        }
    }
    return values[left] === left ? left : -1;
}

```

```Java
public class BinarySearch {

    int binarySearchDemo(int arr[], int x){
        // int[] values = {0, 1, 2, 3, 4, 5, 6 };
        int left = 0, right = arr.length -1;

        while(left < right) {
            double mid = (left + right)/2;
            //explicitly cast double to int,
            int midIndex = (int) Math.floor(mid);

           if(arr[midIndex] == x) return midIndex;

           if(arr[midIndex] > x) {
               right = midIndex - 1;
           } else {
               left = midIndex + 1;
           }
        }
        return arr[left] == x ? left : -1;
    }
    public static void main(String[] args) {
        int[] values = {11, 12, 13, 14, 15, 16, 17 };
        BinarySearch demo = new BinarySearch();

        int result = demo.binarySearchDemo(values, 11);

        System.out.println("index of x:" + result);
    }
}
```

## Recursive Run Times

Often looks like O(branches^depth)

Fibonacci Example

> O(2^n) Exponential Time Complexity

```JavaScript
function recursiveFibo(n) {
    if (n < 2) return n;
    return recursiveFibo(n-1) + recursiveFibo(n-2);
}
```

```Java
int fibo(int n) {
    if (n < 2) return n;
    return fibo(n - 1) + fibo(n - 2);
}
```

## Loop Through Two Inputs Of Varying Length

```JavaScript
const loopThroughTwoInputsOfVaryingLength = (array1, array2) => {
    for (let i = 0; i < array1.length; i++) {
        for (let j = 0; j < array2.length; j++) {
            if(array1[i] === array2[j]) {
                console.log(`Match found at indices: ${i}, ${j}`);
            }
        }
    }
}
```
> Is this O(n^2)?

> Only if both arrays are equal in length, or n.
> Because we don’t know what we don’t know, we need to treat each value separately.
> So this is O(a * b) or O(ab)