# Grafi

> [!TIP]
>
> ### Grafo orientato
>    - Relazioni binarie
>
> ### Indiretto:
> Le relazioni sono non orientate e bidirezionali
> 
> ### Percorso:
> È una sequenza di nodi da un nodo ad un altro in un determinato percorso.
>    - Semplice `se tutti i nodi sono differenti`
>    - Lunghezza `è la somma di tutti gli archi`
>    - Ciclo `il primo e l'ultimo nodo coincidono`
>       - Semplice `se il primo e l'ultimo nodo sono gli unici identici`
>       - Loop `se è presente solo un nodo e un arco punta al nodo stesso`
>>      Un grafo semplice non ha loops, ed è chiamato aciclico se non ha cicli.
>  

## Liste dei grafi:
> [!NOTE]
> È un array e ogni elemento è una lista doppiamente concatenata che ha un indice di collegamenti agli altri nodi. 
> 
> - Spazio usato O-grande n + O-grande m `m = numero di archi, che al massimo può essere n^2`
>>       Continua a scorrere la lista finché il puntatore è NULL. 
> - Inserimento e cancellazione sono un disastro da implementare e inefficienti

## Matrice dei grafi:
> [!NOTE]
> È una matrice n*n `n = numero di nodi` e se il valore (i,k) della matrice è uguale a 1 c'è un arco da i a k. 
> 
> - Spazio usato: Theta n^2
> - Veloce
>>       Può facilmente dirti se c'è un arco.
> - L'inserimento può essere inefficiente

## Oggetti dei grafi:
> [!IMPORTANT]
> Nodi e archi sono conservati in liste doppiamente concatenate
> - Ogni nodo ha una lista di archi collegata a sé.
> - Ogni arco ha una connessione "from" e "to"
>   
> Quando lavoriamo con oggetti tipicamente **segnamo** i nodi visitati per non andare in loop con le visite (diciamo che "coloriamo" i nodi visitati).
>
> Ci sono varie tecnice per la visita dei grafi come: bfs e dfs.
>
> - Il nodo è ***raggiungibile*** se c'è un percorso che lo raggiunge.
>
> - Se ogni paio di nodi sono connessi, il grafo è ***fortemente connesso***.
>
> - **Componenti** sono un pò di nodi tutti connessi, potrebbero esserci più componenti in un grafo.
>
> - Ogni componente può essere una componentee ***fortemente connessa***.

### Grafi da oggetti (Struct) - Esempi dagli esami

```c
typedef struct struct_nodo nodo;  // forward declaration
typedef struct struct_arco arco;  // forward declaration

typedef struct struct_elem_arco {  // list of arcs
   struct struct_elem_arco* prev;
   struct struct_elem_arco* next;
   arco* info;

} elem_arco;

typedef struct struct_elem_nodo {  // list of nodes
   struct struct_elem_nodo* prev;
   struct struct_elem_nodo* next;
   nodo* info;
} elem_nodo;

typedef struct struct_nodo {  // node
   int color;
   elem_arco* archi;  // list of arcs incident on the node
   elem_nodo* pos;    // position in the list of graph nodes
} nodo;

typedef struct struct_arco {  // arc
   nodo* from;
   nodo* to;
   elem_arco* pos;     // position in the graph list
   elem_arco* frompos; // position in the from node list
   elem_arco* topos;   // position in the to node list
} arco;

typedef struct struct_grafo {  // graph
   int numero_nodi;     //number_of_nodes
   int numero_archi;    //number_of_arcs
   elem_nodo* nodi;
   elem_arco* archi;
} grafo_o;
```

### Esempio di soluzione

```c
int test(grafo_o* g) {
    if(g->numero_nodi <= 1) return 0;
    set(g);
    for(elem_nodo *n = g->nodi; n != 0; n=n->next){
            if( "<Conditions here>" )
                return 1;
        }
    }
    return 0;
}
```

### Setup - Colora tutti con uno "0"

```c
void set(grafo_o * g){
    for(elem_nodo * n = g->nodi; n!=0 ; n=n->next){
        n->info->color = 0;
    }
}
```

### Conta & "colora" nodi connessi [DFS]

```c
int dfs(nodo *n){    // or dfs(nodo *n, inv color)
    n->color = 1;    // n->color = color; #for different colors
    int a = 0; //Set at 0, found error answers without.
    int b = 0; //The same for b.
    for(elem_arco * arc = n->archi; arc!=0; arc = arc->next){
        if(arc->info->to->color == 0)
            a =dfs(arc->info->to);
        if(arc->info->from->color == 0)
            b =dfs(arc->info->from);
    }
    return 1 + a + b;
}
```
