# Una ricca eredità

<hr>

Una delle cose più interessanti in Javascript, Gatto, è l'ereditarietà e la catena dei prototipi <sup>[(MDN)][prototypeChain]</sup>. Che detto così di interessante ha ben poco MA ASPETTA, ora mi spiego meglio. 

La spiego facile con un esempio Darwiniano. Tu sei un gatto, della famiglia dei felini. Mettiamo che anche i felini siano un oggetto e nel tuo caso diciamo che il felino è il tuo progenitore. Un oggetto dal quale erediti tutte le caratteristiche.
	
```javascript
var felino = {
	coda: true,
	fusa() {
		console.log('RonRooooon')// il felino fa le fusa
	}
}
```

Per creare questa relazione tra te Gatto e l'oggetto Felino usiamo il metodo `.create()` <sup>[(MDN)][Object.create]</sup>.

```javascript
var gatto = Object.create(felino);
```

Guarda che bello, hai ereditato, gratis, tutte le caratteristiche del tuo progenitore e quindi hai una coda e fai le fusa.

```javascript
console.log(gatto.coda); // true
gatto.fusa(); // RonRooooon

```

Ma come funziona questa MAGIA ? 

Ogni oggetto in javascript ha un proprietà speciale `.prototype`<sup>[(MDN)][Object.prototype]</sup> che la lega all'oggetto che lo ha creato, e all'oggetto che lo ha creato a sua volta, e così via...

Quando cerchiamo una proprietà o metodo in un oggetto, javascript fa un tentativo per vedere se questo esiste, e se non lo trova comincia un percorso a ritroso in questa catena di prototipi, fino ad arrivare al generatore di tutti gli oggetti, che nella fattispecie si chiama, rullo di tamburi, Object <sup>[(MDN)][Object]</sup>.

Per verificare se una proprietà esiste (ereditata o meno) puoi usare l'operatore `in`.

```javascript
console.log('coda' in gatto); // true

```

Ma se vuoi sapere se una proprietà è esistente nel tuo oggetto, infischiandone del fatto che sia stata ereditata, allora devi usare il metodo `.hasOwnProperty()`.

```javascript
gatto.nome = 'Dorakiki';

console.log(gatto.hasOwnProperty('nome')); // true
console.log(gatto.hasOwnProperty('coda')); // false

```

Tutto chiaro fin qui ? Passiamo alla parte 3, ovvero "[Chiodi e martello][3]".



[index]: ../index.md
[3]: ./chiodi_e_martello.md

[Object]: (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)

[__proto__]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/proto


[prototypeChain]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain

[Object.prototype]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype

[Object.create]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/create

[Object]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object
