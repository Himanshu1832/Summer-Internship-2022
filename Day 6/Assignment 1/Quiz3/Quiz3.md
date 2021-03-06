# JavaScript Quiz Basic Level 3


### Theory

1. Explain as much as you know about objects in javascript? (A long answer expected)
    * Objects, in JavaScript, is the most important data-type and forms the building blocks for modern JavaScript. These objects are quite different from JavaScript’s primitive data-types(Number, String, Boolean, null, undefined and symbol) in the sense that while these primitive data-types all store a single value each (depending on their types).
    * OLoosely speaking, objects in JavaScript may be defined as an unordered collection of related data, of primitive or reference types, in the form of “key: value” pairs. These keys can be variables or functions and are called properties and methods, respectively, in the context of an object.
    * Objects are more complex and each object may contain any combination of these primitive data-types as well as reference data-types.
    * Even though the keys are restricted to the data type of string, the values are not. Hence, we can have an `int`, `string`, `array` or even another object as the value of a key.
   * We can access any element with this syntax `objectName.keyName` or `objectName['keyName']`
   * We can iterate through the keys in any object in the following two ways :-
   ```js
   for (let myObjKey in myObj) {
       console.log(myObjKey) // Output :- first \n second \n third \n fourth
   }
   
   console.log(Object.keys(myObj)) // Output :- ['first', 'second', 'third', 'fourth']
   ```
    * We can iterate through the values in any object in the following two ways :-
   ```js
   for (let myObjKey in myObj) {
       console.log(myObj[myObjKey]) // Output :- 1 \n 	two \n 	{ name: 'Kshipra', age: 19 } \n  [ 1, 2, 3, 4 ]
   
   }
   
   console.log(Object.values(myObj)) // Output :- [ 1, 'two', { name: 'Kshipra', age: 19 }, [ 1, 2, 3, 4 ] ]
   ```
   * We can extract only the values we need from an object by destructuring it. Example :- 
   ```js
   let { first, second } = myObj
   
   console.log(first, second) // Output:- 1 two
   ```
   * We can convert the object to an array and then traverse it with a `forEach()` method like this :- 
   ```js
   console.log(Object.entries(myObj))
   /*
   Output :-
   [
       [ 'first', 1 ],
       [ 'second', 'two' ],
       [ 'third', { name: 'Kshipra', age: 19 } ],
       [ 'fourth', [ 1, 2, 3, 4 ] ]
   ]
   */
   ```

2. Make a "class" based alternative to the object based vector template.
```js
class Vector {
	constructor () {
		this.x = 0
		this.y = 0
	}

	set setX(x) {
		this.x = x
	}

	set setY(y) {
		this.y = y
	}

	create(x, y) {
		let obj = Object.create(this)
		obj.setX = x
		obj.setY = y
		return obj
	}
}

let vec1 = new Vector()
console.log(vec1.create(1, 2)) // Output:- Vector { x: 1, y: 2 }
```

3. Do you think JavaScript is the language of the future?
   * Yes. I do think JS is the language of the future.
   * Currently, there are a lot of weird behaviours of JavaScript that cannot be explained. 
   * Due to them, JS has been tagged with an infamous saying :- _"There are a lot of ways to shoot yourself in the foot with JavaScript"_
   * But if these issues are fixed, then surely due to the flexibility of JS, it can become the language of the future.



### Programs

1. Write code implementations for the following Array methods :-
   * Array :- `const arr = [1, 2, 3, 4, 5]`
   * forEach :- 
   ```js
   const arr = [1, 2, 3, 4, 5]
   
   arr.forEach(item => console.log(item)) // Output:- 1 \n 2 \n 3 \n 4 \n 5
   ```
   * map :-
   ```js
   const arr = [1, 2, 3, 4, 5]
   
   console.log(arr.map(num => num * 2)) // Output :- [ 2, 4, 6, 8, 10 ]
   ```
   * filter :- 
   ```js
   const arr = [1, 2, 3, 4, 5]
   
   console.log(arr.filter(num => ((num % 2) == 0))) // Output :- [ 2, 4 ]
   ```
   * reduce :- 
   ```js
   const arr = [1, 2, 3, 4, 5]
   
   console.log(arr.reduce((prev, initial) => prev+initial, 0)) // Output :- 15
   ```
   * includes :- 
   ```js
   const arr = [1, 2, 3, 4, 5]
   
   console.log(arr.includes(2)) // Output :- true
   ```
   * some :-
   ```js
   const arr = [1, 2, 3, 4, 5]
   
   console.log(arr.some(element => element % 2 === 0)) // Output :- true
   ```
   * every :-
   ```js
   const arr = [1, 2, 3, 4, 5]
   
   console.log(arr.every(element => element % 2 === 0)) // Output :- false
   ```
   
2. Simple Array Implementation
```js
const arr = [1, 2, 3, 4, 5, 6]

console.log(arr) // Output:- [1, 2, 3, 4, 5, 6]
```

3. To Do List Task
```js
let ToDo = []
let Completed = []

function add(title) {
	if(title === "") return -1

	const id = Math.floor(Math.random() * 10)
	const task = {
		id,
		'task': title
	}
	ToDo.push(task)
	return id
}

function remove(id) {
	let result = false
	ToDo.forEach(item => {
		if(id in item) {
			result = true
			const idx = ToDo.indexOf(item)
			ToDo.splice(idx, idx+1)
		}
	})
	return result
}

function update(id, title) {
	let result = false
	ToDo.forEach(item => {
		if(id in item) {
			result = true
			item.task = title
		}
	})
	return result
}

function markAsCompleted(id) {
	let result = false
	ToDo.forEach(item => {
		if(id in item) {
			result = true
			const idx = ToDo.indexOf(item)
			const task = ToDo.splice(idx, idx+1)
			Completed.push(task)
		}
	})
	return result
}
```
