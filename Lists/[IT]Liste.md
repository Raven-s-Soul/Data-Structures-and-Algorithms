# Liste

Per la maggior parte è la stessa cosa del corso di fondamenti di informatica.

## RAM - Random Access Machine

    RAM è una macchina astratta ancora più elementare della macchina di Von Neumann.
    La memoria è alla base di una RAM, infatti tutte le operazioni vengono eseguite direttamente in memoria.
    Gli input e gli output sono gestiti in maniera sequenziale.
    Ogni operazione è costante e le istruzioni si susseguono in maniera lineare.

## Puntatori

```c
int a = 0; // define a
int * A = NULL; //define a pointer (not wild)
A = &a; // A now points to a
*A = 5; // a = 5 because the pointer modifies the integer by reference
```

## Strutture or ADT(Abstract Data Type)

```c
struct nodo{
    int info;
    struct nodo * next;
}
```
## "Pile" o Stack :

>    ### [LIFO - Last in First out]
>     Puoi immaginarle come normali array di elementi,
>     usando funzioni come "Push" inserisci l'elemento nel primo spazio disponibile,
>     e usando "POP" ottieni e rimuovi l'ultimo elemento.

## Crescita Telescopica & Complessità ammortizzata:
> [!NOTE]
>
>     Quando la Stack ha esaurito il suo spazio, puoi riallocare lo spazio originale moltiplicato per 2,
>     facendo questo hai un picco  Theta(N) di quell'istanza,
>     ma puoi ammortizzare quel picco, pensando che comunque quel lavoro lo dovrai fare nel tempo 
>     ad ogni inserimento, quindi la costante Theta(N) diventa Theta(1). In pratica lo faccio tutto insieme adesso per non doverlo fare dopo.

## Codice:

>    ### [FIFO - First in First out]
>     Puoi immaginarlo come un array circolare (se provi ad aggiungere una "coda" e superi gli N valori massimi dell'array,
>     in pratica esegui un (indice+1 % N) della dimensione N-1, poi usando funzioni come "Enqueue" puoi inserire l'elemento in coda
>     mentre usando la funzione "Dequeue" ottieni e rimuovi l'elemento di testa e l'inserimento è fatto. 

## [Nodo sentinella](https://en.wikipedia.org/wiki/Sentinel_node)
> [!TIP]
> Molto utile per gli alberi Rosso-Neri
```c
nodo head = null;
// set the 1st element to be a sentinel
head->next = 1 element;
// the actual head of the list
head->prev = last element;
// the tail of the list if has to be double connected
head->info = NULL;
// since is a sentinel, it should be a NULL value
//or a Special Value like -1 if you don't have negative elsewhere. 
```

## Complessità:
> [!CAUTION]
>#### Notazione O-grande (limite superiore)
>
>#### Notazione Theta (limite superiore ed inferiore contemporaneamente)
>
>#### Notazione Ω (limite inferiore)
>
>#### [Complessità nel tempo](https://en.wikipedia.org/wiki/Time_complexity): Costante , Logaritmica , Lineare , Esponenziale, Fattoriale. 

### Metodi veloce ed oneroso:
>  - Il metodo oneroso è basato sulla attenta analisi di ogni passaggio dello pseudocodice.
>  - Il metodo veloce (e più semplice) è quello di aggiungere i diversi costi di ogni pezzo di codice e il risultato è il valore asintotico di tutti i pezzi analizzati.
