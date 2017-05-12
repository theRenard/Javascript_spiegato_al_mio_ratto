# Promesse da marinaio

#### Dove si capisce che una volta che hai fatto una promessa questa va mantenuta. O anche no.

<hr>

Prima di parlare però delle promesse tocca rivedere un concetto importante ovvero l'asincronicità. 

Sincronicità in javascript è del tipo: 

```
esegui A;
esegui B;
esegui C;

```

Asincronicità è piuttosto: 

```
esegui A;
collegati col server Z e recupera i dati;
	quindi esegui B;
esegui C;
collegati col server Y e recupera i dati;
	quindi esegui A 
		quindi esegui una operazione complicatissima;
			quindi esegui B;

```

Va da sé che questi processi non sono eseguiti uno appresso all'altro, prima di eseguire B tocca collegarsi col server, aspettare la risposta, ricevere la risposta, elaborarla, e quant'altro. 

Per aiutarci in questo ingrato compito, possiamo usare le famose, rullo di tamburi, **promesse** <sup>[(MDN)][Promise]</sup>.

La **promessa** in javascript è un *oggetto* utilizzato nelle computazioni asincrone, rappresenta un valore che sarà disponibile *subito*, oppure *nel futuro*, oppure *mai*.

Questa è la sua sintassi.

```javascript
new Promise( /* executor */ function(resolve, reject) { ... } );

```

Ogni promessa ha una proprietà interna `[[PromiseStatus]]` che può avere tre valori:  

1. `"pending"` (di default)
2. `"fulfilled"`
3. `"rejected"`

Nel momento in cui la promessa viene eseguita essa si trova in uno stato di attesa `"pending"`. 

In seguito a questa attesa lo stato può cambiare in `"fulfilled"` o `"rejected"` e quando questo valore cambia, si attiva la coda di esecuzione dei suoi metodi `then()` e/o `catch()`.

Daglie con l'esempio pratico!

Diciamo che siamo Schroedinger, e che infiliamo un gatto qualunque in una scatola d'acciaio e che dopo cinque secondi andiamo a vedere se è vivo o morto.

La `scatola` è quindi la nostra promessa. Le due funzioni *vivo* e *morto* saranno *resolve* e *reject*. 

```javascript
var scatola = new Promise((vivo, morto) => {});
```

Per farla semplice per simulare una operazione straordinariamente lunga mettiamo un timeout di 5 secondi e sepre per comodità per ora il gatto è sempre vivo quindi la promessa, sarà sempre `"fulfilled"` 😸.

```javascript
var scatola = new Promise((vivo, morto) => {

  setTimeout(() => {
    vivo('il gatto è vivo!');
  }, 5000);

});
```

Nota bene, `vivo()` ha come **payload** una stringa ma potrebbe essere un oggetto, una funzione quello che te pare.

Ora, visto che `scatola` è una instanza di `Promise()` questa si porta appresso due metodi: `then()` e `catch()`. 

```javascript
scatola.then((msg) => {
    console.log(msg);  // dopo 5 secondi 'il gatto è vivo!'
});

```
Dopo 5 secondi la funzione `vivo()` della promessa `scatola` cambierà il proprio stato in `"fulfilled"`, e attiverà così il metodo `then`. 

La cosa pratica è che `then()` e `catch()` restituiscono entrambi delle promesse quindi i metodi si possono *incatenare*

Facciamo ora l'esempio del gatto morto 😿. 

Visto che la promessa è ora `"rejected"` solo il metodo `catch()` sarà eseguito. 

```javascript
var scatola = new Promise((vivo, morto) => {

  setTimeout(() => {
    morto('il gatto è morto!');
  }, 5000);

});

scatola
  .then((msg) => {
    console.log(msg); // mai eseguita
  })
  .catch((msg) => {
    console.log(msg); // dopo 5 secondi 'il gatto è morto!'

  });

```

Per dirla tutta `then()` accetta due callback. Il secondo risponde allo stato `"rejected"` come `catch()`.

```javascript

scatola
  .then(
  	(msg) => {
    	console.log(msg); // mai eseguita
  	},
  	(msg) => {
    	console.log(msg); // dopo 5 secondi 'il gatto è morto!'
  });

```
[Promise]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise

