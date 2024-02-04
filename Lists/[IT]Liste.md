# Liste

Per la maggior parte è la stessa cosa del corso di fondamenti di informatica.

## RAM - Random Access Machine

    RAM è una macchina astratta ancora più elementare della macchina di Von Neumann.
    La memoria è alla base di una RAM, infatti tutte le operazioni vengono eseguite direttamente in memoria.
    Gli input e gli output sono gestiti in maniera sequenziale.
    Ogni operazione è costante e le istruzioni si susseguono in maniera lineare.

## Puntatori

```c
int a = 0; // define and set a
int * A = NULL; //define a pointer not wild
A = &a; // A now point to a
*A = 5; // a = 5 using a pointer
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

## Code:

>    ### [FIFO - First in First out]
>     You can immagine it like an circolar array (if you try to add in tail and exced the N value,
>     basicly you index+1 % N) of size N-1, using functions like "Enqueue" you can insert the element in the tail,
>     and using "Dequeue" you get and remove the head element.  

## [Sentinel node](https://en.wikipedia.org/wiki/Sentinel_node)
> [!TIP]
> Usefull for Black&Red tree
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

## Complextity:
> [!CAUTION]
>#### Big-O notation (higher bind)
>
>#### Theta notation (higher and lower bind)
>
>#### Omega notation (lower bind)
>
>#### [Time_complexity](https://en.wikipedia.org/wiki/Time_complexity): Constant , Logarithmic, Linear , Exponential, Factorial. 

### Onerous & Faster Method:
    The Onerous method is based on the sharp analisys of the pseudocode.
    Meanwhile the Faster method add the different costs of each pice of code and the result is the asymptotic value of it.
