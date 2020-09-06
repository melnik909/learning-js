  ```html
  <div class="js-skills">
	<div class="char">
		<div class="char__graph">
			<!--<div class="char__sector-four"></div>
 <div class="char__sector-two"></div>
-->
			<div class="char__sector-one"></div>

			<div class="char__sector-three"></div>
			<div class="char__arrow-wrap">
				<div class="char__arrow js-char__arrow" style="transform: rotate(150deg);"></div>
			</div>
			<div class="char__sector-circle"></div>
		</div>
	</div>
	<div class="skills__container">
		<label class="skills__group">
			<input type="checkbox" class="js-skills__toggle">
			<span class="skills__name">HTML</span>
		</label>
		<label class="skills__group">
			<input type="checkbox" class="js-skills__toggle">
			<span class="skills__name">CSS</span>
		</label>
		<label class="skills__group">
			<input type="checkbox" class="js-skills__toggle">
			<span class="skills__name">JS</span>
		</label>
	</div>
</div>
<button class="btn">go</button>
  ```
  
  ```css
  
/*
https://codepen.io/pavfilin/full/xLKoov
*/

.char{
	margin: auto;
	width: 254px;
	height: 254px;
	/*background-image: url("https://stas-melnikov.ru/1.png");*/
	background-repeat: no-repeat;
}

.char__graph{
	/*opacity: .5;*/
	width: 254px;
	height: 128px;
	border-radius: 84% 84% 0 0 / 165% 165% 0 0;
	position: relative;
	overflow: hidden;
	background-color: #a3cd3b;
}

.char__sector-one{
	width: 100%;
	height: 115px;

	background-color: red;
	position: absolute;
	top: 60px;
	left: -72px;
	transform: rotate(50deg);	
	background-color: #ffc815;
	z-index: 1;
}

.char__sector-two{
	width: 100%;
	height: 145px;
	background-color: #a3cd3b;
	position: absolute;
	top: 40px;
	left: -1px;
	transform: rotate(90deg);
}

.char__sector-four{
	width: 80%;
	height: 100px;
	background-image: linear-gradient(to right, #a3cd3b 50%, #0093d7 50%);
	position: absolute;
	top: 77px;
	right: -98px;
	transform: rotate(40deg);
}

.char__sector-three{
	width: 80%;
	height: 100px;
	background-color: #0093d7;
	position: absolute;
	top: 77px;
	right: -98px;
	transform: rotate(40deg);
}


.char__sector-circle::before,
.char__sector-circle::after{
	content: "";
	width: 74%;
	height: 7px;
	background-color: #fff;
	position: absolute;
}

.char__sector-circle::before{	
	top: -10px;
	left: -37px;
	transform: rotate(51deg);
}

.char__sector-circle::after{	
	top: -9px;
	right: -38px;
	transform: rotate(-52deg);
}

.char__sector-circle{
	width: 143px;
	height: 100%;
	border-radius: 90% 90% 0 0 / 108% 108% 0 0;
	background-color: #fff;
	position: absolute;
	left: 50%;
	bottom: 0;
	z-index: 4;
	transform: translate(-50%, 43%);
}

.char__arrow-wrap{
	width: 100%;
	height: 50%;
	display: flex;
	justify-content: center;
	position: absolute;
	left: 0;
	bottom: 0;
	overflow: hidden;
}

.char__arrow{
	content: "";
	width: 100px;
	height: 5px;
	background-color: #000;
	
	position: absolute;
	bottom: 5px;
	transform-origin: center bottom;
	z-index: 5;
	transition: transform 1s ease-out;
}
  ```

```js
var btn = document.querySelector("button");

var demoGraph = new Skills({
	skillsNode: document.querySelector(".js-skills")
});

demoGraph.skillsNode.addEventListener("change", function(event) {
	if(event.target.classList.contains("js-skills__toggle")) {
		demoGraph.drawGraph();
	}
});

function Skills(settings) {
	this.skillsNode = settings.skillsNode;
	this.items = [].slice.call(settings.skillsNode.querySelectorAll(".js-skills__toggle"));
	this.itemsLength = this.items.length;
	this.graphArrowNode = settings.skillsNode.querySelector(".js-char__arrow");
	this.maxAngle = settings.maxAngle || 180;
}

Skills.prototype.getChekedItems = function(items) {	

	var checkedItems;

	if (!Array.isArray(items)) {
		return console.log("items is not an array");
	}

	checkedItems = items.filter(function(node) {
		return node.checked === true;
	});	

	return checkedItems.length;
}

Skills.prototype.getNewAngle = function(checkedSkillsNumber, skillsNumber, maxAngle) {
	var newAngle; 
	if (typeof checkedSkillsNumber !== "number" || typeof skillsNumber !== "number" || typeof maxAngle !== "number") {
		return console.log("checkedSkillsNumber is not a number");
	}
	newAngle = checkedSkillsNumber * maxAngle / skillsNumber;
	return newAngle.toFixed(1);
}

Skills.prototype.setGraphAngle = function(graphValue) {
	return this.graphArrowNode.style.transform = "rotate(" + graphValue + "deg)";
}

Skills.prototype.drawGraph = function() {
	var newAngle = this.getNewAngle(this.getChekedItems(this.items), this.itemsLength, this.maxAngle);
	this.setGraphAngle(newAngle);
}

/*
97 minute
32:40
23:30
https://medium.com/devschacht/javascript-typeof-43591ab15bef
*/
```
