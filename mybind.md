
```javascript
let sum = 100;

let sumFunction = function() {

  return [].reduce.call(arguments, function(result, current) {
    return result + current;
  }, this.sum);
};

function mybind (func, obj) {

	let args = [].slice.call(arguments, 2);

	return function () {
		return func.apply(obj, args.concat([].slice.call(arguments)));
	}
}

let bindedSum = mybind(sumFunction, {sum: 10}, 20, 30);
console.log(bindedSum(40, 50)); // 10 + 20 + 30 + 40 + 50 === 150
```
