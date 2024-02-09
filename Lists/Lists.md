# Lists

Mostly the same material as for IT-Fundamentals.

## RAM - Random Access Machine

    RAM is an abstract machine model even more fundamental than Von Neumann's Machine.
    Data is stored through a RAM (Random Access Memory) model.
    Input and Output are sequences of data.
    Every operation has a constant cost and the istructions are executed sequentially.

## Pointers

e.g.:
```c
int a = 0;  //define and initialize a variable 'a'
int * A = NULL;  //define a 'non-wild' pointer
A = &a;  //'A' now points to 'a'
*A = 5;  //'a' is now set to 5, by updating the pointer 'A'
```

## Structs or ADT(Abstract Data Type)

e.g.:
```c
struct nodo{
    int info;
    struct nodo * next;
}
```
## "Pile" or Stack :

>    ### [LIFO - Last in First out]
>     You can immagine it like a normal array of elements.
>     Using the function "PUSH" you insert the element in the first slot available,
>     and using "POP" you obtain and then remove the last element from the Stack.

## Telescopic Growth & Amortized analysis:
> [!NOTE]
>
>     Whenever you reach the end of the Stack, you can allocate new memory
>     to double its size, in order to make space for the new element.
>     This is known as Telescopic Growth.
> 
>     By doing this, the complexity of the algorithm spikes to `Θ(n)`,
>     where n is the number of elements already in the stack, when n reaches the end of the Stack.
>     If you spread out the spike over the entire graph, you can find that the average cost for every value of n is `Θ(1)`.

## "Code" or Queue:

>    ### [FIFO - First in First out]
>     You can imagine it like a circular list of size N-1.
>     Using the function "ENQUEUE" you can insert an element in the tail,
>     and using "DEQUEUE" you obtain and remove the head element.  

## [Sentinel node](https://en.wikipedia.org/wiki/Sentinel_node)
> [!TIP]
> Useful for Red-black trees
```c
nodo head = null;
//set the 1st element to be a sentinel
head->next = 1 element;
//the actual head of the list
head->prev = last element;
//the tail of the list, assuming it is a doubly linked list
head->info = NULL;
//since it is a sentinel, it should have a value of NULL or -1 
```

## Complexity:
> [!CAUTION]
>#### Big-O notation (upper bound)
>
>#### Theta notation (upper and lower bound)
>
>#### Omega notation (lower bound)
>
>#### [Time_complexity](https://en.wikipedia.org/wiki/Time_complexity): Constant, Logarithmic, Linear, Exponential, Factorial, etc. 

### Taxing & Faster Method:
    Taxing method: explicitly calculate the complexity based on the pseudocode and then study its an asymptotic behaviour.
    Faster method: calculate the asymptotic cost of each portion of the pseudocode and then add them all up. 

