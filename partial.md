
```javascript
function test(a, b, c) { return 'a=' + a + ',b=' + b + ',c=' + c; }

function partialAny(fn) {
	const args = [...arguments].slice(1);
	const indexs = [];

	args.forEach(function(arg, i) {

		if (typeof arg === "undefined") {
			indexs.push(i);
		}
	});

	return function() {

		[...arguments].forEach(function(arg, i) {
			args[indexs[i]] = arg;
		});

		return fn(...args);
	}
}

let test1_3 = partialAny(test, 1, undefined, 3);
console.log(test1_3(5)); // a=1,b=5,c=3

let test_1_ = partialAny(test, undefined, 1, undefined);
console.log(test_1_(7, 3)); // a=7,b=1,c=3

let test18_ = partialAny(test, 1, 8, undefined);
console.log(test18_(3)); // a=1,b=8,c=3
```
