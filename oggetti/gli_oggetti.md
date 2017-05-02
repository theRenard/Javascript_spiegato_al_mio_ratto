# Gli oggetti

#### Ovvero dove un gatto non è più un animale 🙀 
<hr>

Caro gatto, Javascript è un linguaggio ad oggetti. Va da sé che gli oggetti li userai <strike>spesso</strike> sempre e questo corso per gatti inizia quindi spiegando cosa è un  oggetto <sup>[(MDN)][Object]</sup>.

Un oggetto non è altro che una collezione non ordinata di dati (proprietà) e funzioni (metodi) definiti come coppie **chiave** e **valore**. 

In pratica:

```javascript
{ chiave: 'valore' };  // eccomi, sono un oggetto.
```

Per spiegarla semplice, creiamo un gatto. 

Ovvero, creiamo un oggetto che somigli a un gatto, e per comodità assegniamo a questo oggetto una variabile `gatto`.

```javascript
var gatto = { chiave: 'valore' };
```

Aspetta no, ancora meglio... come tutti i gatti il nostro deve avere nove vite, e senza dubbio la sfiga di perderne una a settimana. 

Facciamo allora che al tuo oggetto `gatto` aggiungiamo una proprietà `vite` e un metodo `muore()`. 

```javascript
var gatto = {

	// una proprietà
	vite: 9,

	// un metodo
	muore: function() {
		// this in questo caso è l'oggetto stesso, è
		// come se scrivessimo gatto.vite;
		// ma parleremo di this più in là
		this.vite -= 1;
	}	
}

```

Bravo Gatto, hai creato il tuo primo oggetto! Sei tu sputato! 

Aspetta, aspetta, giochiamo un po' con questo `gatto`. Cominciamo per esempio ad accedere ai suoi metodi e alle sue proprietà, `[[get]]` .

Per farlo, possiamo usare il **punto** `.___` o le **parentesi quadre** `[___]` .

Vuoi sapere quante vite gli restano? Facile.

```javascript
// col punto, detto anche la dot notation
console.log( gatto.vite ); // 9
```

Vuoi vedere che succede quando finisce sotto una macchina? 

```javascript
gatto.muore();  // eseguiamo il metodo con il punto

// accediamo di nuovo al parametro ma con la bracket notation
console.log( gatto['vite'] ); // 8

```

E con lo stesso sistema caro Gatto, puoi aggiungere nuove proprietà e nuovi metodi `[[set]]`. 


```javascript
// ecco una nuova proprietà
gatto.nome = 'Dorakiki';

// ... e un nuovo valore a un proprietà pre-esistente
gatto.vite = 5;

// ... e un nuovo metodo
gatto['rivive'] = function() {
	this.vite += 1; // viva la resurrezione felina.
}

```

La *dot notation* è probabilmente più semplice da leggere, ma con le parentesi quadre puoi usare una variabile come chiave per recuperare un valore, cosa piuttosto pratica.

```javascript
// piuttosto leggibile
gatto.proprieta_1.sotto_proprieta_2.metodo().valore;
	
// meno rapido da leggere, ma pratico assai
var valoreDinamico = 'nome';
gatto[valoreDinamico] = 'Dorakiki';
```

Un altro metodo per accedere alle proprietà di un oggetto è utilizzare un ciclo `for ... in `.


```javascript
var gatto = {
	vite: 9, 
	coda: true, 
	colore: 'nero'
}

for (var chiave in gatto) {
	var valore = gatto[chiave];
	console.log('la proprietà ' + chiave + ' ha il valore ' + valore);
}

// la proprietà vite ha il valore 9
// la proprietà coda ha il valore true
// la proprietà colore ha il valore nero

```

E se vuoi avere una lista delle sole chiavi puoi usare `Object.keys()`.

```javascript
var gatto = {
	vite: 9, 
	coda: true, 
	colore: 'nero'
}

console.log(Object.keys(gatto)); // ['vite', 'coda', 'colore']

```

Tutto chiaro fin qui Gatto ? Lo spero. 

Perché è tempo di passare al capitolo successivo, dove parleremo in modo più approfondito delle proprietà di un oggetto, ovvero nella "[Proprietà Privata][2]".


[Object]: (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)



[index]: ../index.md
[2]: ./proprieta_privata.md
