# Graphs

> [!TIP]
>
> ### Directed: `Oriented`
>    - Binary relations
>
> ### Indirect:
> Where there is no orientation and connections are just bi-directional
> 
> ### Path:
> Is a sequence of nodes that leads from one to another across arcs.
>    - Simple `if all nodes are differents`
>    - Lenght `is the sum of the arcs`
>    - Cycle `where first and last node are the same`
>       - Simple `if last and first node is the only one that is the same`
>       - Loop `if only one node and one arch pointing to itself`
>>      A simple graph has no loop, and is called acyclic if has no cycles.
>




## Gaph lists:

## Gaph matrix:
> [!NOTE]
> - Space used Theta n^2
> - Fast
>>       Can tell you easly if there is an arch from node to node
>

## Gaph objects:

### Graphs by objects (Struct) - Example form the tests

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

### Example of solution

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

### Setup - Color all to 0

```c
void set(grafo_o * g){
    for(elem_nodo * n = g->nodi; n!=0 ; n=n->next){
        n->info->color = 0;
    }
}
```

### Count & "Color" linked nodes [DFS]

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
