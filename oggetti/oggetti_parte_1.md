# Gli oggetti

<hr>

Caro gatto, Javascript è un linguaggio ad oggetti, gli oggetti li userai spesso, sempre. Questo corso inizia facile, spiegando cosa è un oggetto <sup>[(MDN)][1]</sup>.

Un oggetto è una collezione non ordinata di dati (proprietà) e funzioni (metodi) definiti come coppie nome **nome** e **valore**. 

Per farla semplice, facciamo che tu sei un oggetto. Si lo so, non è bello da dire, sei un animale, ma facciamo che per descriverti usiamo un oggetto.

```javascript
var gatto = {};
```
Ora, come tutti i gatti hai nove vite, e senza dubbio la capacità di perderne una a settimana. Una proprietà e un metodo che potremmo aggiungere all'oggetto che ti descrive. 

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

Per accedere ai tuoi metodi e alle tue proprietà, [**get**] puoi utilizzare il punto o la parentesi quadra.

```javascript
// con il punto, detto anche dot notation
console.log( gatto.vite ); // 9

gatto.muore();  // avvelenato ?

// con le parentesi quadre, o bracket notation
console.log( gatto['vite'] ); // 8

```
E con lo stesso sistema caro Gatto, puoi aggiungere nuove proprietà e nuovi metodi. 

```javascript
// ecco una nuova proprietà
gatto.nome = 'Dorakiki';

// un nuovo valore a un proprietà esistente
gatto.vite = 5;

// e un nuovo medoto
gatto['rivive'] = function() {
	this.vite += 1; // che può tornarti tanto, tanto utile.
}

```

A mio modesto parere la *dot notation* è più semplice da leggere, ma con le parentesi quadre puoi usare una variabile per recuperare un valore, cosa pratica, credimi.

```javascript
// carino no?
gatto.proprieta_1.sotto_proprieta_2.metodo().valore;
	
// 
var valoreDinamico = 'nome';
gatto[valoreDinamico] = 'Dorakiki';
```

1. [Oggetti parte 2, Come si crea un oggetto ?][2]
2. [Oggetti parte 3, cosa succede nel 2015 ?][2]
3. [Oggetti parte 4, una ricca eredità][3]


[1]: (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)

[2]: ./oggetti_parte_2.md
[3]: ./oggetti_parte_3.md
