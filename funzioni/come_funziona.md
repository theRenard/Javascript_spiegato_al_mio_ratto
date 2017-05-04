# Come Funziona la Funzione

#### dove si scopre chi fa cosa 
<hr>

Ciao Gatto, benvenuto nella pagina dove si parla di come funziona la funzione. 

In javascript la funzione è importante come l'oggetto, per dirla tutta la funzione **è** un oggetto, si dice infatti che sia un **oggetto di prima classe** ed ha, come ogni altro oggetto, delle proprietà e dei metodi. Inoltre, questa cittadinanza onoraria, permette alle funzioni di essere come il prezzemolo. 

Puoi assegnarle ad una variabile, puoi passarle come argomenti ad altre funzioni, possono essere il risultato di altre funzioni. In pratica ci fai quello che ti pare.

Quello che la distingue dagli altri oggetti è la presenza di una proprietà interna `[[Call]]`, che indica che questo oggetto può essere eseguito. 

La funzione idealmente è composta da una sequenza di istruzioni, può accettare dei parametri e restituisce sempre un valore.

Si dichiara così:

```javascript
function nome(parametri) {
	... istruzioni
};
```

Ma vediamone una che facciamo prima.

```javascript
function faiQualcosa() {}; // ciao sono una funzione!
```

Questa funzione è piuttosto inutile, non fa niente, e il valore che restituisce è `undefined`. Una noia totale. 

Creiamo allora una funzione che accetti almeno un parametro e che lo restituisca modificato. Tramite `return` possiamo rendere esplicito il risultato della funzione. Diciamo di avere una data quantità di "croccantini", vogliamo che la nostra funzione ne raddoppi il valore. Gnam!

```javascript
var croccantini = 50;

function raddoppia(valore) {
	// valore è il parametro atteso dalla funzione
	return valore * 2;
};

// eseguiamo raddoppia passando croccantini come argomento
var molti_croccantini = raddoppia(croccantini);

console.log(molti_croccantini); // 100

```

Bravo Gatto, hai creato la tua prima funzione, che tra l'altro fa una cosa molto utile, raddoppia i croccantini.


[Object]: (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)


[index]: ../index.md
