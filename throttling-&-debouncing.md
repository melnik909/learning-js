```js
function throttle(f, t) {
  return function (args) {
    let previousCall = this.lastCall;
    this.lastCall = Date.now();
		//console.log("previousCall", previousCall, "lastCall", lastCall);
    if (previousCall === undefined || (this.lastCall - previousCall) > t) { // throttle time has elapsed
			//console.log("t", this.lastCall - previousCall);
      f(args);
    }
  }
}

let logger = (args) => console.log(`My args are ${args}`);
// throttle: функция logger вызывется с аргументом [1, 2, 3] один раз за 12 секунд после первого вызова. 
let throttledLogger = throttle(logger, 12000); 

throttledLogger([1, 2, 3]);
throttledLogger([15, 4, 3]);
throttledLogger([1, 2, 3]);
throttledLogger([4, 5, 6]);
throttledLogger([7, 8, 9]);


function debounce(f, t) {
  return function (args) {
    let previousCall = this.lastCall;
    this.lastCall = Date.now();
		///console.log("previousCall", previousCall, "lastCall", lastCall);
    if (previousCall && ((this.lastCall - previousCall) <= t)) {
			//console.log("condition true");
      clearTimeout(this.lastCallTimer);
    }
    this.lastCallTimer = setTimeout(() => f(args), t);
  }
}

 // debounce: функция logger вызывется с аргументом [7, 8, 9] по истечению 12 секунд после первого вызова. 
let debouncedLogger = debounce(logger, 12000);

debouncedLogger([1, 2, 3]);
debouncedLogger([4, 5, 6]);
debouncedLogger([7, 8, 9]);
/*
https://medium.com/nuances-of-programming/что-такое-throttling-и-debouncing-4f0a839769ef
*/
```
