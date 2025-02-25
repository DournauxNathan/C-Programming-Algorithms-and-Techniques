### **Affichage inverse de tableau dynamique**

```c
#include <stdio.h>

int main()
{
    int N;
    
    // Lire l'entier N
    scanf("%d", &N);
    
    // Allocation d'un tableau de taille N
    int* tab = (int*) malloc(sizeof(int)* N);
    
    // Stockage de i dans tab
    for(int i = 0; i < N; i++)
    {
        // Lit et stock N entier dans tab
        scanf("%d", &tab[i]);
    }

    // Affichage de tab en ordre inverse
    for(int i = N - 1; i >= 0; i--)
    {
        if (i == 0) 
        {
            printf("%d\n", tab[i]);
        }
        else
        {
            printf("%d,", tab[i]);
        }
    }

    // Libération de la mémoire allouée pour tab
    free(tab);
    
    return 0;
}
```

- **But de l'algorithme** : Afficher les éléments d'un tableau dynamique dans l'ordre inverse.
- **Entrée** : Un entier `N` représentant la taille du tableau, puis `N` entiers à stocker dans le tableau.
- **Sortie** : Les éléments du tableau affichés dans l'ordre inverse.
- **Description** : Le programme alloue dynamiquement un tableau de `N` entiers, les remplit avec des valeurs saisies par l'utilisateur, puis affiche ces éléments en ordre inverse.

---

### **Allocation d'un tableau 2D en N+1 malloc**

```c
int** initMatrix(int N, int M){
    
    // Allocation d'un tableau de taille N
    int** tab = (int**) malloc(sizeof(int*)* N);
    
    for (int i = 0; i < N; i++)
    {
        // Allocation de chaque ligne
        tab[i] = (int*) malloc(sizeof(int)* M);
    }
    
    // Affichage du tableau
    for (int i = 0; i < N; i++)
    {
        for (int j = 0; j < M; j++)
        {
            tab[i][j]= i + j;
            printf("%d ", tab[i][j]);
        }
        printf("\n");
    }
    
    return tab;
}
```

- **But de l'algorithme** : Allouer dynamiquement un tableau 2D de taille `N`x`M` et l'afficher.
- **Entrée** : Deux entiers `N` et `M` représentant les dimensions du tableau.
- **Sortie** : Le tableau affiché avec des valeurs calculées comme la somme des indices de ligne et de colonne.
- **Description** : Cette fonction alloue un tableau 2D en utilisant une allocation dynamique par `malloc` pour chaque ligne. Les valeurs de chaque élément sont calculées et affichées.

---

### **Libération d'un tableau à deux dimensions alloué en N+1 mallocs**

```c
void freeMatrix(int*** ptab, int N){
    
    if(ptab == NULL || *ptab == NULL)
    {
        return 0;
    }
    
    for (int i = 0; i < N; i++)
    {
        free((*ptab)[i]);
    }
    
    free(*ptab);
    
    *ptab = NULL;
}
```

- **But de l'algorithme** : Libérer la mémoire d'un tableau 2D alloué dynamiquement.
- **Entrée** : Un pointeur vers le tableau 2D `ptab` et l'entier `N` représentant le nombre de lignes.
- **Sortie** : Aucune sortie (libération de la mémoire).
- **Description** : Cette fonction libère la mémoire de chaque ligne du tableau, puis libère la mémoire de l'ensemble du tableau 2D.

---

### **Cloner un tableau**

```c
int* clone(int* tab, int N){
    
    // Allocation d'un tableau de taille N
    int* newTab = (int*) malloc(sizeof(int)* N);
    
    for(int i = 0; i < N; i++)
    {
        newTab[i] = tab[i];
    }
    
    return newTab;
}
```

- **But de l'algorithme** : Cloner un tableau dynamique.
- **Entrée** : Un tableau `tab` d'entiers et sa taille `N`.
- **Sortie** : Un nouveau tableau `newTab` avec les mêmes éléments que `tab`.
- **Description** : Cette fonction alloue un nouveau tableau et copie chaque élément du tableau d'origine dans le tableau cloné.

---

### **Concaténer deux tableaux**

```c
int* concat(int* tabA, int sizeA, int* tabB, int sizeB){
    
    // Allocation d'un tableau de taille N
    int* newTab = (int*) malloc(sizeof(int) * (sizeA + sizeB));
    
    for(int i = 0; i < sizeA; i++)
    {
        newTab[i] = tabA[i];
    }
    
    for (int i = 0; i < sizeB; i++)
    {
        newTab[sizeA + i] = tabB[i];
    }
    
    for (int i = 0; i < (sizeA + sizeB); i++)
    {
        debug("%d", newTab[i]);
    }
    
    return newTab;
}
```

- **But de l'algorithme** : Concaténer deux tableaux en un seul.
- **Entrée** : Deux tableaux `tabA` et `tabB`, et leurs tailles respectives `sizeA` et `sizeB`.
- **Sortie** : Un tableau `newTab` contenant tous les éléments de `tabA` suivis de ceux de `tabB`.
- **Description** : Cette fonction crée un nouveau tableau de taille égale à la somme des tailles des deux tableaux d'entrée et copie les éléments des deux tableaux dans le tableau final.

---

### **Concaténer N tableaux**

```c
int* concat(int** tabs, int* sizes, int N){
    
    int totalSize = 0;
    
    // Trouver la taille du nouveau tableau
    for (int i = 0; i < N; i++)
    {
        totalSize += sizes[i];
    }
    debug("%d", totalSize);
    
    // Allocation d'un tableau de taille N
    int* newTab = (int*) malloc(sizeof(int)* totalSize);
    
    int currentIndex = 0;
    
    for (int i = 0; i < N; i++)
    {
        for (int j = 0; j < sizes[i]; j ++)
        {
           newTab[currentIndex++] = tabs[i][j];
        }
    }
    
    return newTab;
}
```

- **But de l'algorithme** : Concaténer N tableaux dynamiques en un seul tableau.
- **Entrée** : Un tableau de tableaux `tabs`, un tableau `sizes` contenant les tailles des tableaux, et l'entier `N` représentant le nombre de tableaux.
- **Sortie** : Un tableau `newTab` contenant tous les éléments des tableaux concaténés.
- **Description** : Cette fonction calcule la taille totale nécessaire pour contenir tous les éléments des tableaux, puis concatène tous les tableaux en un seul tableau.

---

### **Triangle de Pascal**

```c
int** pascal(int N){
    
    // Allocation d'un tableau de taille N
    int** triangle = (int**) malloc(sizeof(int*)* N);
    
    for (int i = 0; i < N; i++)
    {
        // Allocation de chaque ligne
        triangle[i] = (int*) malloc(sizeof(int) * (i + 1));
        
        triangle[i][0] = 1;
        triangle[i][i] = 1;
        
        // Remplir le tableau 
        for(int j = 1; j < i; j++)
        {
            triangle[i][j] =  triangle[i - 1][j - 1] + triangle[i - 1][j];
        }
    }
    
    return triangle;
}
```

- **But de l'algorithme** : Générer un triangle de Pascal de taille `N`.
- **Entrée** : Un entier `N` représentant le nombre de lignes du triangle.
- **Sortie** : Un tableau 2D représentant le triangle de Pascal.
- **Description** : Cette fonction alloue un tableau 2D et remplit chaque ligne du triangle de Pascal en utilisant la formule classique de chaque élément, où chaque élément est la somme des deux éléments précédents.

---

### **Allocation d'un tableau 2D en 2 malloc**

```c
int** initMatrix(int N, int M){
    
    // Allocation d'un tableau de taille N
    int** tab = (int**) malloc(sizeof(int*)* N);
    
    // Allocation de chaque ligne
    int* tab2 = (int*) malloc(sizeof(int) * (N*M));
    
    for (int i = 0; i < N; i++)
    {
        tab[i] = tab2 + i * M;
    }
    
    // Affichage du tableau
    for (int i = 0; i < N; i++)
    {
        for (int j = 0; j < M; j++)
        {
            tab[i][j] = i + j;
        }
    }
    
    return tab;
}
```

- **But de l'algorithme** : Allouer dynamiquement un tableau 2D en utilisant deux appels à `malloc`.
- **Entrée** : Deux entiers `N` et `M` représentant les dimensions du tableau.
- **Sortie** : Le tableau 2D alloué et rempli avec des valeurs calculées comme la somme des indices de ligne et de colonne.
- **Description** : Cette fonction utilise deux allocations de mémoire, une pour l'ensemble des pointeurs de ligne et une

 autre pour les données elles-mêmes.

---

### **Allocation d'un tableau 2D en 1 seul malloc**

```c
int** initMatrix(int N, int M){
    
    // Allocation combinée d'un tableau 2D en une seule allocation
    int** tab = (int**) malloc(sizeof(int*)* N + sizeof(int) *(N * M));
    
    for (int i = 0; i < N; i++)
    {
        // Initialiser chaque pointeur de ligne
        tab[i] = (int*) (tab + N) + i * M;
    }
    
    // Affichage du tableau
    for (int i = 0; i < N; i++)
    {
        for (int j = 0; j < M; j++)
        {
            tab[i][j] = i + j;
        }
    }
    
    return tab;
}
```

- **But de l'algorithme** : Allouer dynamiquement un tableau 2D en une seule allocation mémoire.
- **Entrée** : Deux entiers `N` et `M` représentant les dimensions du tableau.
- **Sortie** : Le tableau 2D alloué et rempli avec des valeurs calculées.
- **Description** : Cette fonction combine les allocations pour les pointeurs et les données en un seul bloc mémoire.