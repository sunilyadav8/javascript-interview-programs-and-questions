# Javascript-interview-programs-and-questions

**Click star if you like the project. Pull Request are highly appreciated.**

| No  | Questions |
| ------------- | ------------- |
|  1 |   [Find the Length of a Nested Array](#Find-the-Length-of-a-Nested-Array)|

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
