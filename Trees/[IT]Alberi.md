# Alberi

Gli alberi sono come liste, ma hanno più di un puntatore ai nodi successivi.

Riconosciamo in un albero varie parti:    
-  La radice (la testa dell'albero)
-  I nodi (come la radice, ma sono "radici" di altri "sottalberi")
-  Le foglie (sono nodi, ma sono alla fine dell'albero)
    
-  I nodi hanno gradi basati sulla loro posizione e altezza dalla radice,
    l'altezza della radice è ad altezza 0.
    
### Ci sono vari tipi di albero:

## Alberi binari
> [!NOTE]
>>     Ogni nodo ha puntatori a nodi successivi: sx, dx. //Teoricamente potresti avere anche un nodo parent
>>     Analogamente alle liste puoi fare list->next ... solo che negli alberi è tree->sx o tree->dx
>>     Se ogni nodo ha 2 nodi figli allora l'albero si definisce binario, 
>>     e se ogni nodo ha esattamente 2 nodi è un albero binario completo.
>>     Nel caso dell'albero binario completo le foglie sono "2^altezza = foglie" e altezza = log2(foglie)

```c
typedef struct nodo{
    int info;
    struct nodo *dx;
    struct nodo *sx;
} nodo;

typedef nodo * tree;
```

## Ricerca negli alberi
> [!WARNING]
> ### *Array Associativo* (map or dictionary)
>     Danno una chiave (che può essere int, string ecc) e ritornano un valore o una risposta
>     La cosa migliore è una chiave per ogni risposta [Lineare]
>     Può essere fatta usando 2 Array, liste e alberi.
>### Abr or Bst (Alberi binari di ricerca)
> 
>     Molto simile agli alberi binari ma le informazioni in ogni nodo sono basate sulla posizione del nodo nell'albero, 
>     Sulla sinistra hai numeri più bassi e sulla destra hai i numeri più alti.
>     In questo modo puoi cercare valori usando la ricerca binaria che è molto più veloce di quella lineare (log).
> #### Complessità generale = Theta log(n)
>### [Tree Sort](../SortingAlgorithms/[IT]SortingAlgorithms.md#tree-sort)

## Alberi di grado arbitrario

    Ci sono vari modi per creare alberi di grado arbitrario ma il più facile e il più comune è il metodo "Figlio sinistro, fratello destro":
    in pratica quando ti muovi usando tree->sx ti muovi più in profondità nell'albero.
    Invece usando tree->dx ti muovi in un nodo dello stesso grado.

## Alberi Rosso-Neri

> [!IMPORTANT]
>>     Il loro obiettivo è tenere l'albero di ricerca bilanciato, ogni nodo può essere rosso o nero.
>>     Le radici o le sentinelle possono essere solo nere, e se un nodo è rosso entrambi i figli devono essere neri.
>>     Ogni percorso dalla radice alla sentinelkla ha K nodi neri, in cui il percorso è minimo (K-1) o massimo 2(K-1).
>>     Ecco perché l'altezza è percorso-1.

> [!CAUTION]
> #### Altezza, Inserimento, Rimozione = Theta log(n)
>>     Attenzione, l'inserimento, rimozione di nodi potrebbe rompere le regole che tengono l'albero bilanciato.
>>     In caso di rottura delle regole la funzione di riparazione potrebbe occupare fino a Theta log(n).
> #### Rotazione = Theta 1;
>
>>     La funzione di rotazione riduce il percorso più lungo di uno e incrementa il più corto di uno.
>>     Facendo diverse rotazioni può far ribilanciare l'albero, ma bisogna stare attenti che
>>     the other node are kept in order, just node X and Y change
>>     from parent to son -> son to parent. Always left lower values and right higher and parent in the middle! 
>

## Coda di priorità e Heap 

Coda di priorità: l'utente può inserire l'elemento con la sua priorità e quando mi serve posso richiedere l'elemento con la priorità più alta.

    Ogni elemento ha il suo grado di priorità, che ne definisce l'ordine.

### Heap
>[!TIP]
>>     È un array "speciale" dove il valore di ogni elemento rappresenta la posizione nell'array.
>>     Ci sono versioni max-heap o min-heap.
>#### Hai un Array, ora mostralo come un albero, così che i nodi dello stesso grado abbiano una priorità più vicina alle altre. 
>    Ora scegli ***i*** un nodo nel tuo albero, i figli sono 2***i*** +1 e 2***i***+2,
>    e il parent se ***i*** != 0 è a (***i***-1)/2.
>
>    Il max-heap ha all'elemento ***i*** una priorità maggiore di ogni nodo discendente,
>    per il min-heap è il contrario.
>
>    La funzione **Max-heapify** rende il nodo ***i*** la probabilità più alta nel sottalbero costa al max Theta log(n).
>
>    La funzione **Build_Max_Heap** crea un heap da un array e costa al massimo "O-grande: n*log(n)".
>### [Heap Sort](../SortingAlgorithms/[IT]SortingAlgorithms.md#heap-sort)

# Funzioni che dovresti conoscere:

### ContaNodi

```c
int count(tree T){
    if(T == 0) return 0; // if(T == NULL) is the same since in C, NULL is a macro to 0.
    return 1 + count(T->sx) + count(T->dx);
}
```

### ContaFoglie
```c
int leafs(tree T){
    if(T == 0) return 0;
    if(T->sx == NULL & T->sx == NULL) return 1;
    return leafs(T->sx) + leafs(T->dx);
}
```

### ContaAltezza

```c
int height(tree T){
    if(T == 0) return -1;
    int s = height(T->sx);
    int d = height(T->dx);
    return (d > s)? d+1 : s+1;
}
```

### Ricerca nel sottalbero

```c
//Example of sub search by int values.
//Return true if any node has the same value of antother one.
int func(tree T, int value){
    if(T == 0) return 0;
    return (T->info == value) || func(T->sx, value) || func(T->dx, value) ||
    func(T->sx, T->info) || func(T->dx, T->info) ;
}
```
<!--
### Add on the tree

### Remove from the tree
