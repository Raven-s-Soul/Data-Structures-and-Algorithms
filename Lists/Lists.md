# Lists

Is mostly doing the same for IT-Fundamentals

## RAM - Random Access Machine

    RAM is an abstract machine even more elemental then Von Neumann's Machine
    The memory is on the base of the RAM-Random Access Memory.
    Sequenzial Imput and Output.
    Every operation is constant, and the istructions are followed in linerity.

## Pointers

```c
int a = 0; // define and set a
int * A = NULL; //define a pointer not wild
A = &a; // A now point to a
*A = 5; // a = 5 using a pointer
```

## Struct or ADT(Abstract Data Type)

```c
struct nodo{
    int info;
    struct nodo * next;
}
```
## "Pile" or Stack :

>    ### [LIFO - Last in First out]
>     You can immagine like a normal array of elements,
>     using functions like "Push" you insert the element in the first slot avaible,
>     and using "POP" you get and remove the last element.

## Crescita Telescopica & Complessità ammortizzata:
> [!NOTE]
>
>     Whenever you reach the end of the Stack, you can Re-allocate by x2 the slots/size,
>     doing this you have a spike of Theta(N) of on that istance,
>     but you can think of amortize the spike, thinking to do the same work of that instance 
>     over time so it basicly become a constant Theta(1).

## "Code" or Queue:

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

