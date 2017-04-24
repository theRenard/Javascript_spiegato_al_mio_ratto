# Una ricca eredità

<hr>

Una delle cose che più ti piacerà di Javascript è l'ereditarietà e la catena dei prototipi <sup>[(MDN)][1]</sup>.

Per spiegare il concetto caro Gatto, tiriamo in ballo Darwin e la teoria dell'evoluzione. Tu sei un gatto, della famiglia dei felini. Anche i felini sono un oggetto e nel tuo caso diciamo che il felino è il tuo progenitore. Lo descriviamo qui in modo facile facile.
	
```javascript
var felino = {
	coda: true,
	fusa() {
		console.log('RonRooooon')// fa le fusa
	}
}
```

Per aiutarci usiamo la proprietà `__proto__`<sup>[(MDN)][__proto__]</sup> che è presente in ogni oggetto. Attento Gatto questo è un solo un esempio, ci sono modi migliori di creare questo legame. 
 
```javascript
// creiamo l'oggetto gatto
var gatto = {};

// assegnamo felino come suo __proto__
gatto.__proto__ = felino; 
```

Potremmo dire, Gatto, che tu hai ereditato tutte le caratteristiche del tuo genitore, quindi hai una coda e fai le fusa.

```javascript
console.log(gatto.coda); // true

gatto.fusa(); // RonRooooon

```

Ogni oggetto in javascript ha un proprietà <sup>[(MDN)][Object.prototype]</sup> speciale che la lega all'oggetto che lo ha creato, e all'oggetto che ha creato l'oggetto, e così via, fino ad arrivare all'ogetto principale [Object][object]




Avrai già intuito Gatto che la ricerca di una tua proprietà o metodo ripercorre tutta la catena dei prototipi fino ad arrivare all'oggetto principale (che si chiama Object <sup>[(MDN)][Object]</sup>)

Fortunatamente ogni tua proprietà può essere riscritta, magari hai perso la coda anni fa...

```javascript
gatto.coda = false;
console.log(gatto.coda); // false

```

Così Gatto, ora tu hai un link con il felino <sup>[(MDN)][Object.create]</sup>.

```javascript
var gatto = Object.create(felino);
```


[__proto__]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/proto


[1]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain

[Object.prototype]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype

[Object.create]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/create

[Object]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object
