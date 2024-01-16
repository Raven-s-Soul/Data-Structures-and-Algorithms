# Graphs

## Gaph lists

## Gaph matrix

## Gaph objects

# Code:

### Setup as 0

```c
void setup(grafo_l *g){
    for(int i = 0; i< g->size ; i++)
        g->nodi[i]->color = 0;
}
```

### Color all arround

```c
void dfs(grafo_l *g, int nodo; int *color){
    color[nodo]=1;
    elem* c = g->a[nodo];
    while(x != 0){
        if(color[x->info] == 0)
            dfs(g, x->info , color);
        x = x->next;
    }
}
```
