# Algoritmi di ordinamento
> [!TIP]
> ## Disclaimer
> ***Non fidarti troppo di questi pezzi di codice, potrebbero essere presenti degli errori***
> 
> Se gli algoritmi di ordinamento non sono corretti sentiti libero di modificarli, sono solo esempi di funzionamento.

> [!IMPORTANT]
> ## Algoritmi greedy(golosi)
> - Questo tipo di approccio cerca sempre il caso migliore al momento anche se alla lunga è il peggiore.
>     - [Selection sort]([IT]SortingAlgorithms.md#selection-sort)
> ## Algoritmi iterativi
> - Algoritmi semplici che riescono a risolvere problemi più grandi. 
>     - [Insertion sort]([IT]SortingAlgorithms.md#insertion-sort)
>     - [Heap sort]([IT]SortingAlgorithms.md#heap-sort)
> ## Proprietà
> - *in loco* `non hanno bisogno di spazio extra`
> - *stabile* `non scambia l'ordine di valori uguali`
> - *adattivo* `più veloce se una parte è già ordinata`
> - *online* `può essere usato se i numeri vengono inseriti uno alla volta`
> - *efficiente su piccole istanze*
>
> ## Formula di ricorrenza
> Equazioni o disequazioni che descrivono il suo valore asintotico.
> ## Divide Et Impera
> - Dividi il problema in più problemi più piccoli e semplici.
> - [Iterative]([IT]SortingAlgorithms.md#algoritmi-greedygolosi)
>   -  [Merge Sort]([IT]SortingAlgorithms.md#merge-sort)
>   -  [Quick Sort]([IT]SortingAlgorithms.md#quick-sort)
> ## Master theorem
> - a,b > 1 
> - a numbero di sotto-ricorsioni 
> - b numbero di elementi nelle sotto-ricorsioni.
> - T(n) = { Theta 1                    if n = 0
> -            { a*T(n/b) + O(n^k)   if n > 0
>>     se a < b^k -> T(n) = Theta n^k        | Il primo livello ha la complessità più alta
>>     se a = b^k -> T(n) = Theta n^k log(k) | Tutti i livelli hanno la stessa complessità
>>     se a > b^k -> T(n) = Theta n^logb(a)  | L'ultimo livello ha la complessità più alta

## Selection sort
>  [!NOTE]
> Esempio: Cambia sempre il valore con il minimo disponibile poi vai avanti.
> ### Theta n^2  
>  -  *[Greedy]([IT]SortingAlgorithms.md#algoritmi-greedygolosi)*
>  -  *in loco*
>  -  *stabile*

## Insertion sort
>  [!NOTE]
> Esempio: Lentamente prova a fare ordine in una parte e con il tempo aggiungi le altre parti a quella già ordinata.
> ### Best case Theta n and others Theta n^2  
>  -  *[Iterativo]([IT]SortingAlgorithms.md#algoritmi-greedygolosi)*
>  -  *in loco*
>  -  *stabile*

## Merge Sort
>  [!NOTE]
> Esempio: Dividi l'array in parti più piccole finché sono solo due numeri poi ordina e unisci con le altre coppie ordinate.
> ###  Theta n*log(n)
>  -  *[Divide Et Impera]([IT]SortingAlgorithms.md#divide-et-impera)*
>  -  *non in loco*
>  -  *stabile*

## Quick Sort
>  [!NOTE]
> Esempio: Dividi l'array in due dove ogni elemento del primo array è <= degli elementi del secondo, poi ordina e combina.
>>     L'array 1 ha elementi da p a q-1, e l'array 2 ha elementi da q+1 a r.
>>     Se p = r l'array è già ordinato, se p > r dovrebbe esserci un errore.
> Per dividere serve un valore q necessario a eseguire una *PARTITION* dell'array usando i valori maggiore e minore.
>
> Come funziona la *PARTITION*? **Theta n**
>   - Prendi l'elemento con *indice massimo = Array[r]*
>   - Conta quanti sono <= *a* quell'elemento, la somma sarà *q*
>   - Scambia *Array[counter]* con *Array[q]* e esegui *q++* 
>   - Ad ogni iterazione del ciclo, scambia *Array[q]* con *Array[r]* e *ritorna q*.
>>      Quando ottieni q puoi Quick_Sort(Array,p,q-1) e Quick_Sort(Array,q+1,r).
> ###  Theta n*log(n) o Theta n^2
>  -  *[Divide Et Impera]([IT]SortingAlgorithms.md#divide-et-impera)*
>  -  *In loco*
>  -  *non stabile*

## [Heap](../Trees/[IT]Alberi.md#coda-di-priorità-e-heap) Sort
```c
h.A = A; //New Heap
h.size = A.lenght;
Build_Max_Heap(h); //make a heap from an array
for( i = h.A.length-1; i > 1 ; i--) {
  exchange_slots(A,0,i);
  h.size = h.size – 1;
  Max-heapify(h,0); //make node i the highest priority of the sub tree
}
```
>  [!NOTE]
>  Rircoda Heap e le code di priorità!
>
>  Come funziona:
>  - Da un'array crei un albero, poi prendi la dimensione dell'array.
>  - Nel ciclo:
>      -  scambi i valori di *array[0]* e *array[contatore]* ogni volta
>      -  usa la funzione *heapify* per essere sicuro di avere quello con la massima priorità.
>      -  deincrementi il contatore siccome hai già eseguito lo scambio su quel valore.
>
> 
> ### Theta n*log(n)
>  -  *[Iterativo]([IT]SortingAlgorithms.md#algoritmi-greedygolosi)*
>  -  *non stabile*
>  -  *in loco*

## [Tree](../Trees/[IT]Alberi.md#ricerca-negli-alberi) Sort
```c
TREE_SORT(A){
  t.root = NULL;
  for (int i = 1; a < A.length-1; a++){
    INSERISCI(t,A[i]);
  }
  TREE_TO_ARRAY(A,t,0);
}
```
>  [!NOTE]
>  Come funziona:
>  - Crei un albero.
>  - Nel ciclo che itera la dimensione dell'array da ordinare:
>      -  Inserisci il valore dell'array nell'albero binario.
>      -  `tenendo sempre a sinistra i valori più piccoli e a destra i valori più grandi` 
>  -  Leggi nell'ordine che preferisci l'albero e inseriscilo nell'array
> ### 
>  - Theta n^2 (non bilanciato)
>  - O-grande(n log n) (balanced)
>  - *non in loco*
>  - [Wikipedia](https://en.wikipedia.org/wiki/Tree_sort)

##  Counting Sort
>  [!NOTE]
>  - Ci sono *K* contatori per ogni valore possibile ***i***
>  - per ogni ***i*** conta quanti sono i valori uguali a ***i***
>  - conta quanti sono minori di ***i***
>  - dopo inserisci gli elementi ***i*** in ordine nell'array.
>
>  **Tutte le operazioni hanno complessità Theta n**
>  - *stabile*
>  - *non in loco*
>  - *non online*
>  - ***Theta n+k***

##  Bucket Sort
>  [!NOTE]
>  - Crea una lista per ogni ***i*** <= *k*
>  - Leggi l'array e inserisci il valore sulla lista in posizione corrispondente al suo valore
>  - Svuota la lista mentre riempi nuovamente l'array
> 
>  **Tutte le operazioni sono di complessità Theta n**
>  - *stabile*
>  - *non in loco*
>  - *non online*
>  - ***Theta n+k***

##  Radix Sort
>  [!NOTE]
>  Vogliamo ordinare valori che sappiamo a priori avere ***d*** caratteri.
>
>     Quando vogliamo ordinare valori usando più criteri dobbiamo prima considerare
>     il criterio più significante poi il meno significante.
>  - Ordina per ogni ***d***.
> 
>  **All operation are Theta n**
>  - *stabile*
>  - ***Theta d(n+k)*** `k è il valore massimo nel carattere`
