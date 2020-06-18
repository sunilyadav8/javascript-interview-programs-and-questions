# Javascript-interview-programs-and-questions

**Click star if you like the project. Pull Request are highly appreciated. **

| No  | Questions |
| ------------- | ------------- |
|  1 |   [Find the Length of a Nested Array](#Find-the-Length-of-a-Nested-Array)|
|  2 |   [Given the month and year as numbers, return whether that month contains a Friday 13th. ](#Date-Question)|
|  3 |   [Broken Keyboard Problem. ](#Broken-Keyboard-Problem)|
|  4 |   [Write a mul function which will produce the following outputs when invoked. ](#Write-a-mul-function-which-will-produce-the-following-outputs-when-invoked)|
|  5 |   [Seven Boom!](#Seven-Boom)|
|  6 |   [Round to Closest N](#Round-to-Closest-N)|
|  7 |   [Pandigital Numbers](#Pandigital-Numbers)|
|  8 |   [Scoring a Field Goal](#Scoring-a-Field-Goal)|
|  9 |	 [Remove Duplicate Values from a JavaScript Array. ](#Remove-Duplicate-Values-from-a-JavaScript-Array)|
|  10 |   [Sort array without using predefine method](#Sort-array-without-using-predefine-method)|

1\. ## Find the Length of a Nested Array\. 

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

2\. ## Date Question

## Given the month and year as numbers, return whether that month contains a Friday 13th. 

``` 
function hasFriday13(month, year) {
	const date=new Date( `${year}-${month}-13` )
	return date.getDay() === 5
}
```

3\. ## Broken Keyboard Problem

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

4\. ## Write a mul function which will produce the following outputs when invoked

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

*Explanation:- Here the mul function accepts the first argument and returns an anonymous function, which takes the second parameter and returns another anonymous function that will take the third parameter and return the multiplication of the arguments that have been passed. *

5\. ## Seven Boom

Create a function that takes an array of numbers and return "Boom!" if the number 7 appears in the array. Otherwise, return "there is no 7 in the array". 

Examples
sevenBoom([1, 2, 3, 4, 5, 6, 7]) ➞ "Boom!"

sevenBoom([8, 6, 33, 100]) ➞ "there is no 7 in the array"

sevenBoom([2, 55, 60, 97, 86]) ➞ "Boom!"

``` 
function sevenBoom(arr) {
	return /7/.test(arr.join('')) ? 'Boom!' : 'there is no 7 in the array'
}
```

or

``` 
const sevenBoom = (arr) => arr.join("").indexOf('7') >= 0 ? "Boom!" : "there is no 7 in the array";
```

6\. ## Round to Closest N

Creates a function that takes two integers, num and n, and returns an integer which is divisible by n and is the closest to num. If there are two numbers equidistant from num and divisible by n, select the larger one. 

Examples
roundNumber(33, 25) ➞ 25

roundNumber(46, 7) ➞ 49

roundNumber(133, 14) ➞ 140

``` 
const roundNumber = (num, n) => Math.round(num / n) * n;
```

or (Without using Math object)

``` 
function roundNumber(num, n) {
	const lessMultiple = n*parseInt(num/n);
	const greaterMuliple = n * (parseInt(num/n) + 1);
	return num - lessMultiple >= greaterMuliple - num ? greaterMuliple : lessMultiple;
}
```

7\. ## Pandigital Numbers

A pandigital number contains all digits (0-9) at least once. Write a function that takes an integer, returning true if the integer is pandigital, and false otherwise. 

Examples
isPandigital(98140723568910) ➞ true

isPandigital(90864523148909) ➞ false
// 7 is missing. 

isPandigital(112233445566778899) ➞ false

``` 
function isPandigital(num) {
	return [...new Set(num.toString().split(''))].sort((a,b)=>a-b).length === 10
}

```

or

``` 
function isPandigital(num) {
	return [...new Set(num.toString().split(''))].sort((a,b)=>a-b).length === 10
}
```

8\. ## Scoring a Field Goal

In (American) Football, a team can score if they manage to kick a ball through the goal (i. e. above the crossbar and between the uprights). 

Create a function that returns true if the ball 0 goes through the goal. You will be given an array of arrays. 

### Examples

``` 
isGoalScored([
  ["  #     #  "],
  ["  #  0  #  "],
  ["  #     #  "],
  ["  #######  "],
  ["     #     "],
  ["     #     "],
  ["     #     "]
]) ➞ true

isGoalScored([
  ["  #0    #  "],
  ["  #     #  "],
  ["  #     #  "],
  ["  #######  "],
  ["     #     "],
  ["     #     "],
  ["     #     "]
]) ➞ true

isGoalScored([
  ["  #     #  "],
  ["  #     #  "],
  ["  #     # 0"],
  ["  #######  "],
  ["     #     "],
  ["     #     "],
  ["     #     "]
]) ➞ false
```

Solution 1. 

``` 
function isGoalScored(goal) {
	for(let i = 0; i < 3; i++){
		for(let j = 3; j < 9; j++){
			if(goal[i][0][j] === '0') return true;
		}
	}
	return false;
}
```

Solution 2. 

``` 
function isGoalScored(goal) {
	const isGoal = goal.some(item=>{
		 const occurenceOfHash =item[0].match(/#/g) &&  item[0].match(/#/g) && item[0].match(/#/g).length
		if(item[0].indexOf('#') < item[0].indexOf('0') && item[0].indexOf('0')<item[0].lastIndexOf("#") && occurenceOfHash < 3) {
			return true
		}
		return false
	})
	return isGoal
}
```

9\. ## Remove Duplicate Values from a JavaScript Array

Solution 1. Using set. 

``` 
funtion  getUnique(arr) {
	return [...new Set(arr)]
}
```

Solution 2. Using for loop. 

``` 
    function getUnique(array){
        const uniqueArray = [];
        for(i=0; i < array.length; i++){
            if(uniqueArray.indexOf(array[i]) === -1) {
                uniqueArray.push(array[i]);
            }
        }
        return uniqueArray;
    }

    const names = ["Sunil", "Mohan", "Ram", "Ram", "John", "Alice"];
    const uniqueNames = getUnique(names);
    console.log(uniqueNames);
```

10. ## Sort array without using predefine method

``` 
getSortedArray=(arr)=>{
  for(let i=0;i<arr.length; i++) {
    for(let j=i; j<arr.length; j++) {
      if(arr[i]>arr[j]) {
        let temp = arr[i];
        arr[i]=arr[j];
        arr[j]=temp;
      }
    }
  }
}
const arrData = [5,6,1,0,4,0,10];

getSortedArray(arrData)

```
