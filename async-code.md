setTimeout(function(){
	console.log("setTimeout")
}, 0);

let fn = function(resolv, reject){
	let a = resolv();
	console.log("fn");
}

let promise = new Promise(fn);

fn2();

async function M() {
	let a = await console.log("await");
}

promise
	.then(function () {console.log("then 1"); let i = "let"; return {a: 1, b: 2}})
	.then(function (x) {console.log("then 2", x); return reject()})
	.then(function (x) {console.log("then 3", x); return 3})
	.catch((msg) => console.log('custom error', msg));

function fn2() {
	console.log("fn2 is called");

	function fn3() {
		console.log("fn3 is called");
	};

	fn3();
}

M();
