## Objects
### Press start to play 🎮

What is an Object[*][1] ?

*An object is an unordered collection of primitive or reference data types (properties) and functionality (methods) that is stored as a series of name-value pairs.*

Let's say we are going to play a new game. 
We can use an object to set a new player.

```javascript
var player = {};
```
Or we can set an object with some properties and methods like the number of lives and a death method.

```javascript
var player = {

	// a property
	lives: 3,

	// a method, 'this' is the object itself
	losesOneLife: function() {
		this.lives -= 1;
	}	
}

```
We can **get** its methods and properties like that:

```javascript
// dot notation
console.log( player.lives ); // 3

player.losesOneLife();

// bracket notation
console.log( player['lives'] ); // now 2

```
And of course we can **set** new properties/methods in the very same way.

```javascript
// redefine an existing property
player.name = 'Player 1';

// and a brand new method
player['getsOneLife'] = function() {
	this.lives += 1;
}

```

Dot notation is maybe easier to read but with bracket notation you can get/set keys dynamically:

```javascript
// dot
player.property_1.property_2.method().value;
	
// brackets
var dynamicValue = 'name';
player[dynamicValue] = 'Player 1';
```

next : object initializer es2015
next : references and primitives

[1]: (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)