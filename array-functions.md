```js
const countries = [
  {
    name: "USA",
    cities: [
      {
        name: "New York",
        population: 9
      },
      {
        name: "Los Angeles",
        population: 4
      },
      {
        name: "Chicago",
        population: 3
      }
    ]
  },
  {
    name: "Russia",
    cities: [
      {
        name: "Moscow",
        population: 12
      },
      {
        name: "Saint Petersburg",
        population: 5
      }
    ]
  },
  {
    name: "China",
    cities: []
  }
];

// Можно использовать ES6+
// Нужно написать выборки данных из массива.
// Желательно использовать цепочки вызовов функций (методов) без явного создания временных переменных.

// 1. Получить массив названий всех городов
// Ожидаемый результат: ["New York", "Los Angeles", "Chicago", "Moscow", "Saint Petersburg"]

// 2. Получить сумму населения (population) всех городов
// Ожидаемый результат: 33

// 3. Получить название первой страны, в которой есть город с населением больше 10
// Ожидаемый результат: Russia

// 4. Есть ли хотя бы одна страна с пустым массивом городов
// Ожидаемый результат: true


let getCities = function(countries) {
  return countries.map((counrty) => counrty.cities).flat().map((city) => city.name);
}

console.log('getCities', getCities(countries));

let getTotalPopulation = function(countries) {
  return countries.map((counrty) => counrty.cities).flat().map((city) => city.population).reduce((acc, cur) => acc + cur);
}

console.log('getTotalPopulation', getTotalPopulation(countries));

let getCountry = function(countries) {
	let countriesIndex;
	
	countries.map((counrty) => counrty.cities).forEach((cities, index) => { 
		 cities.forEach((city) => { if (city.population > 10) { countriesIndex = index; }}); 
	});
	
  return countries[countriesIndex].name;
}

console.log('getCountry', getCountry(countries));

let getEmptyCountry = function(countries) {
  return countries.map((counrty) => counrty.cities).some((cities) => cities.length === 0);
}

console.log('getEmptyCountry', getEmptyCountry(countries));

```
