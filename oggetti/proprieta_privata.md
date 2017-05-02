# Proprietà privata

#### Ovvero, come creare, modificare, smontare gli oggetti.

<hr>

Ogni proprietà che aggiungi ad un oggetto ha sei sotto-proprietà con cui puoi perfezionare il loro comportamento. 

Per spiegarti cosa fa ciascuna di queste, usiamo un metodo di `Object` che si chiama `.defineProperty()` <sup>[(MDN)][defineProperty]</sup> e che fa esattamente quello che dice, ovvero definire una proprietà.

Come nella pagina precedente vogliamo aggiungere la proprietà `vite` al nostro `gatto`, vediamo come.

```javascript
var gatto = {};

Object.defineProperty(gatto, 'vite', {
  value: 9,
  enumerable: true,
  configurable: true,
  writable: true,
});

```



1. `value` È il valore della proprietà, può essere un numero, un oggetto, una funzione, qualsiasi valore valido in JS. <br>Valore di default `undefined`.
2. `enumerable ` Se è `true` la proprietà sarà accessibile quando facciamo una enumerazione ad esempio `for ... in` oppure `Objects.key()`. <br>Valore di default `true`.
3. `configurable` Se è `true` la proprietà può essere rimossa con `delete` e può essere ri-configurata. <br>Valore di default `true`.
4. `writable `Se è `true`, indovinate un po', il valore della proprietà può essere riscritto.<br>Valore di default `true`.
 
Per capirci, quello che abbiamo fatto qui sopra è equivalente a 

```javascript
gatto.vite = 9;

```

E per concludere, due metodi: **get** e **set**. Sono molto pratici per elaborare il valore di una proprietà prima di assegnarla. Facciamo l'esempio del gatto miracolato. Quando assegniamo `vita` ne raddoppiamo il valore.


```javascript
var gatto = {};

Object.defineProperty(gatto, 'vite', {
	// assegno 'vite' ad una proprietà transitoria che chiamo '_vite'.
  set: function(value) { this._vite = value * 2; },
	// aggiungo un simpatico messaggio
  get: function() { return 'Gatto miracolato hai ben ' + this._vite + ' vite!'; }
});

gatto.vite = 9;

console.log(gatto.vite); // "Gatto miracolato hai ben 18 vite!"


```


[defineProperty]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty
