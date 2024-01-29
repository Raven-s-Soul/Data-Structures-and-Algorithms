# Trees

They are really like lists, but they have more pointers to other nodes.
    
    There is the Root (the head of the tree)
    There are nodes (Like the Root, but they are "Roots" of other "Sub-Trees")
    There are in the end leafs (They are nodes, but they are at the end of the tree)
    Nodes have grades based on their position and height based from the root,
    the root of the tree is at height 0.
    
### There are differents kinds like:

## Binary
> [!NOTE]
>>     Each Node has pointets to nodes: sx, dx. //Tecnicaly u can have a parent too...
>>     Like list you can do list->next ... you can do tree->sx or tree->dx
>>     If each node has at max 2 node sons is binary, 
>>     and if each node has exactly 2 node is a complete binary.
>>     In the complete binary case 2^h = leafs and h = log2(leafs) where h is the height.

```c
typedef struct nodo{
    int info;
    struct nodo *dx;
    struct nodo *sx;
} nodo;

typedef nodo * tree;
```

## Searching
> [!WARNING]
> ### *Associative Array* (map or dictionary)
>     They ask for a key that can be a int or string ecc and he gave back a value or answer
>     The best is Only one key to only one answer [Linear]
>
>### Abr or Bst (binary search trees)
> 
>     Really similar to the Binary but they the info inside each node is based on the position on the tree, 
>     on the left you have lower numbers and on right you have higher numbers.
>     In this way you can search a value using the binary search (log) much more faster then linear.
> #### General complexity = Theta log(n)
>### [Tree Sort](../SortingAlgorithms/SortingAlgorithms.md#tree-sort)

## Arbitrary Grade

    There are differents way to have Arbitrary but the easies is the "Left Son, Right Brother":
    basicly when you tree->sx you are moving down the tree to a higher deep.
    Insted doing tree->dx you are moving into a same grade node.

## Black&Red

> [!IMPORTANT]
>>     Their concept is to keep the searching tree bilanced, every node can be Red or Black.
>>     The root and sentinels are all black, and if a node is red both the sons are black.
>>     Every path from the root to the sentinel has K black nodes, where the path/arch at min K-1 or 2(K-1) at max.
>>     Thats's why the height is the path-1.

> [!CAUTION]
> #### Height, Insert, delete = Theta log(n)
> #### Rotate = Theta 1;
>>
>>     Attention when insert and delete nodes may break the rules that keep a the tree balanced.
>>     In case of Break the fix function may take up to Theta log(n).

## Priority Queue and Heap 

Priority Queue: the user can insert the element with his priority and when needed can ask the element with the higher priority

    Each element has his own priority value, that define the sorting.

### Heap
>[!TIP]
>>     Is a "Special Array" where the value of each element rappresent the position in the array.
>>     There are max-heap or min-heap versions
>#### You got an Array, now display it like a tree, so the nodes with the same grade has a close priority to the other.
>    Now chose ***i*** a node in the tree, the sons are at 2***i*** +1 and 2***i***+2,
>    and the parent if ***i*** != 0 is at (***i***-1)/2.
>
>    The max-heap has at element ***i*** a higher priority then every descending node,
>    for the min-heap is the opposite.
>
>    The function **Max-heapify** make node ***i*** the highest priority of the sub tree it cost at max Theta log(n).
>
>    The function **Build_Max_Heap** make a heap from an array it cost up to Big-O n*log(n).
>### [Heap Sort](../SortingAlgorithms/SortingAlgorithms.md#heap-sort)

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
