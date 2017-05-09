# Questo codesto e quello

#### dove si scopre come si utilizza `this`

<hr>

Caro Gatto, in uno degli esempi precedenti avevamo creato un oggetto con una proprietà ed un metodo, arieccolo:

```javascript
var gatto = {
	vite: 9,
	muore: function() {
		this.vite -= 1;
	}	
}

```

`this.vite` in questo caso corrisponde quindi a `gatto.vite`, sembra abbastanza intuitivo, ma a cosa corrisponde davvero `this`?

Un modo facile è pensare a `this` come se fosse il pronome `questo`.

Il `gatto` è un oggetto e `questo` ha 9 `vite` e quando `questo` `muore()` `questo` perde una vita. 


`this` è quindi un modo comodo di rappresentare l' **oggetto** chiamato durante l'esecuzione di una funzione, e visto che una funzione può essere invocata in contesti diversi, anche `this` può cambiare valore.

Facciamo un esempio pratico con un `cane` ed un `gatto`. Entrambi, per loro sfortuna, hanno il metodo muore. 

```javascript
var gatto = {
	vite: 9,
	muore: function() {
		this.vite -= 1
	}
};

var cane = {
	vite: 1,
	muore: function() {
		this.vite -= 1
	}
};

```

Grazie a `this` possiamo evitare di scrivere il metodo `muore()` due volte.

```javascript
function sottraiUnaVita() {
	this.vite -= 1;
}

var gatto = {
	vite: 9,
	muore: sottraiUnaVita
};

var cane = {
	vite: 1,
	muore: sottraiUnaVita
};

gatto.muore();
console.log(gatto.vite); // 8

cane.muore();
console.log(cane.vite); // 0

```

Come descritto poco prima, `this` cambia in base al contesto in cui è chiamato. In questo caso `this` è una volta il `gatto` e una volta il `cane`.

Come avrai già capito `this` è assegnato in maniera automatica in Javascript, ma niente ci vieta di manipolarlo a piacere per *forzarlo* ad assumere il valore che più ci piace. 

Guarda questo esempio, questo cane non può morire, è immortale (o meglio non ha il metodo `muore()`)

```javascript
var gatto = {
	vite: 9,
	muore: function() {
		this.vite -= 1
	}
};

var cane = {
	vite: 1
};

```

Le funzioni in javascript sono degli oggetti, e quindi hanno dei metodi, ma questo dovresti già saperlo. Grazie ai metodi `call()`, `apply()` e `bind()` possiamo prendere in prestito un metodo da un altro oggetto e *forzare* il valore di `this`.

```javascript
gatto.muore.call(cane);
// muore è una funzione certo ed è anche un oggetto
// call() non è altro che uno dei suoi metodi.

console.log(cane.vite); // 0

```

`call()` e `apply()` si comportano nello stesso identico modo, la differenza riguarda la quantità di parametri.

```javascript
var gatto = {
	caratteristiche: function(nome, razza, colore) {
		this.nome = nome;
		this.razza = razza;
		this.colore = colore;
	}
}

var cane = {};

```

`call()` accetta l'oggetto del contesto e a seguire gli stessi parametri della funzione d'origine.

```javascript
gatto.caratteristiche.call(cane, "fido", "husky", "grigio"); // call(); 

console.log(cane); // {nome: "fido", razza: "husky", colore: "grigio"}

```

`apply()` accetta solo 2 parametri. L'oggetto del contesto come per `call()` e i parametri della funzione d'origine in forma di `array`.


```javascript
gatto.caratteristiche.apply(cane, ["fido", "husky", "grigio"]);

console.log(cane); // {nome: "fido", razza: "husky", colore: "grigio"}

```

`bind()` fa qualcosa di simile a `call()` e `apply()`, ma mentre questi due eseguono le funzioni immediatamente, `bind()` restiuisce una funzione che dovrà essere eseguita in un secondo momento.


```javascript
var creaUnCane = gatto.caratteristiche.bind(cane, "fido", "husky", "grigio");

creaUnCane();

console.log(cane); // {nome: "fido", razza: "husky", colore: "grigio"}

```


[this]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this


[index]: ../index.md
