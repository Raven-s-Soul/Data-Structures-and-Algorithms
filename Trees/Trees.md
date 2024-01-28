# Trees

They are really like lists, but they have more pointers to other nodes.
    
    There is the Root (the head of the tree)
    There are nodes (Like the Root, but they are "Roots" of other "Sub-Trees")
    There are in the end leafs (They are nodes, but they are at the end of the tree)
    Nodes have grades based on their position and height based from the root.

### There are differents kinds like:

## Binary

    Each Node has pointets to nodes: sx, dx. //Tecnicaly u can have a parent too...
    Like list you can do list->next ... you can do tree->sx or tree->dx

```c
typedef struct nodo{
    int info;
    struct nodo *dx;
    struct nodo *sx;
} nodo;

typedef nodo * tree;
```

## Serching

    Really similar to the Binary but they the info inside each node is based on the position on the tree, 
    on the left you have lower numbers and on right you have higher numbers.
    In this way you can serch a value using the binary search much more faster then linear.

## Arbitrary Grade

    There are differents way to have Arbitrary but the easies is the "Left Son, Right Brother":
    basicly when you tree->sx you are moving down the tree to a higher deep.
    Insted doing tree->dx you are moving into a same grade node.

## Black&Red

    Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. 
    Nunc sed augue lacus viverra vitae. 
    Odio aenean sed adipiscing diam donec adipiscing tristique. Vulputate dignissim suspendisse in est ante in nibh mauris. 
    Sed vulputate odio ut enim blandit volutpat. 
    Purus in mollis nunc sed id semper risus in. Et sollicitudin ac orci phasellus egestas tellus rutrum. 
    In fermentum posuere urna nec tincidunt praesent semper. 
    Tincidunt id aliquet risus feugiat in ante metus. Proin libero nunc consequat interdum varius sit amet mattis. 
    Facilisi nullam vehicula ipsum a arcu. Aliquam faucibus purus in massa tempor nec feugiat nisl. Risus sed vulputate odio ut enim. 
    Bibendum at varius vel pharetra vel turpis nunc. Eu ultrices vitae auctor eu augue ut lectus arcu.

# Functions that you should know:

### Count nodes

```c
int count(tree T){
    if(T == 0) return 0; // if(T == NULL) is the same since in C, NULL is a macro to 0.
    return 1 + count(T->sx) + count(T->dx);
}
```

### Count leafs

```c
int leafs(tree T){
    if(T == 0) return 0;
    if(T->sx == NULL & T->sx == NULL) return 1;
    return leafs(T->sx) + leafs(T->dx);
}
```

### Count height

```c
int height(tree T){
    if(T == 0) return -1;
    int s = height(T->sx);
    int d = height(T->dx);
    return (d > s)? d+1 : s+1;
}
```

### Sub tree search

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
