# Javascript-interview-programs-and-questions

**Click star if you like the project. Pull Request are highly appreciated. **

| No  | Questions |
| ------------- | ------------- |
|  1 |   [Find the Length of a Nested Array](#Find-the-Length-of-a-Nested-Array)|
|  2 |   [Given the month and year as numbers, return whether that month contains a Friday 13th. ](#Date-Question)|
|  3 |   [Broken Keyboard Problem. ](#Broken-Keyboard-Problem)|
|  4 |   [Write a mul function which will produce the following outputs when invoked. ](#Write-a-mul-function-which-will-produce-the-following-outputs-when-invoked)|

1. ## Find the Length of a Nested Array.

Explanation:- getLength([1, [2, [3, [4, [5, 6]]]]]) ➞ 6

``` 
function getLength(arr) {
	return arr.reduce((acc,el, index) => {
		return Array.isArray(el) ? acc + getLength(el) : acc + 1
	} , 0)
}
```

or We can use [Array. prototype. flat()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flat)

``` 
const getLength = arr => arr.flat(Infinity).length;
```

2. ## Date Question

## Given the month and year as numbers, return whether that month contains a Friday 13th. 

``` 
function hasFriday13(month, year) {
	const date=new Date( `${year}-${month}-13` )
	return date.getDay() === 5
}
```

3. ## Broken Keyboard Problem

Given what is supposed to be typed and what is actually typed, write a function that returns the broken key(s). The function looks like:

findBrokenKeys(correct phrase, what you actually typed)
Examples
findBrokenKeys("happy birthday", "hawwy birthday") ➞ ["p"]

findBrokenKeys("starry night", "starrq light") ➞ ["y", "n"]

findBrokenKeys("beethoven", "affthoif5") ➞ ["b", "e", "v", "n"]

``` 
function findBrokenKeys(str1, str2) {
	const str1Array = [...new Set(str1.split(''))]
	const str2Array = [...new Set(str2.split(''))]
	const result = str1Array.filter((item, i)=>{
		return !(item === str2Array[i]) && item
	})
	return result;
}

```

4. ## Write a mul function which will produce the following outputs when invoked

``` 
function mul (x) {
    return function (y) { // anonymous function
        return function (z) { // anonymous function
            return x * y * z;
        };
    };
}

console.log(mul(2)(3)(4)); // output : 24
console.log(mul(4)(3)(4)); // output : 48

```

*Explanation:- Here the mul function accepts the first argument and returns an anonymous function, which takes the second parameter and returns another anonymous function that will take the third parameter and return the multiplication of the arguments that have been passed.*
