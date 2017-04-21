# Una ricca eredità

<hr>

Una delle cose che più ti piacerà di Javascript è l'ereditarietà e la catena dei prototipi <sup>[(MDN)][1]</sup>. 

Per spiegare il concetto caro Gatto, tiriamo in ballo Darwin e la teoria dell'evoluzione. Tu sei un gatto, della famiglia dei felini. Anche i felini sono un oggetto e nel tuo caso diciamo che il felino è il tuo prototipo.
	
```javascript
var felino = {
	coda: true,
	fusa() {
		console.log('RonRooooon')// fa le fusa
	}
}
```

Ogni oggetto in javascript ha un link al prototipo che lo ha creato e così Gatto, ora tu hai un link con il felino.

```javascript
var gatto = Object.create(felino);
```

Potremmo dire, Gatto, che tu hai ereditato tutte le caratteristiche del tuo genitore, quindi hai una coda e fai le fusa.

```javascript
console.log(gatto.coda); // true

gatto.fusa(); // RonRooooon

```

Avrai già intuito Gatto che la ricerca di una tua proprietà o metodo ripercorre tutta la catena dei prototipi fino ad arrivare all'oggetto principale (che si chiama Object <sup>[(MDN)][object]</sup>)

Fortunatamente ogni tua proprietà può essere riscritta, magari hai perso la coda anni fa...

```javascript
gatto.coda = false;
console.log(gatto.coda); // false

```


[1]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain

[object]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object
