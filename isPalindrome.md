```js
/** * Является ли строка палиндромом * @param {string} str * @return {boolean} */ 


console.log('a man d nama', '--true', isPalindrome('a man d nama'));
console.log('table', '--false', isPalindrome('table'));

function isPalindrome(str) { 
	let res = str.replace(/\s/g, '');
	return res === res.split('').reverse().join('');
}
```
