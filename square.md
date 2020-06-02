
```javascript
function square(x) { return x * x; } // возведение в квадрат

function map (func, arr) {
	let arrLen = arr.length;
	let resultArr = [];

	if (arrLen === 0) return resultArr;

	arr.forEach(function(item, i, arr){
		resultArr.push(func(item));		
	});

	return resultArr;
}

console.log(map(square, [1, 2, 3, 4])); // [1, 4, 9, 16]
console.log(map(square, [100])); // [10000]
console.log(map(square, [])); // []
```
