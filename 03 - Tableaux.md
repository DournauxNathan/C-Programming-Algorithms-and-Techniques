# Tableaux

## Affichage d'un tableau

```c
void display(int* tab, int taille)
{
    for(int i = 0; i < taille; i++) {
        printf("%d ", tab[i]);
    }
}
```

### **But de l'algorithme** :
Afficher tous les éléments d'un tableau d'entiers.

### **Entrée** :
- Un tableau d'entiers `tab` et un entier `taille` représentant la taille du tableau.

### **Sortie** :
- Affichage des éléments du tableau sur la sortie standard.

### **Description** :
Cette fonction parcourt le tableau et affiche chaque élément à l'écran.

---

## Egalité de tableaux triés

```c
int equals(int *tab, int *tab2, int N)
{
    for (int i = 0; i < N; i++)
    {
        if (tab[i] != tab2[i])
        {
            return 0;  
        }
    }
    
    return 1;
}
```

### **But de l'algorithme** :
Comparer deux tableaux d'entiers pour vérifier s'ils sont égaux.

### **Entrée** :
- Deux tableaux d'entiers `tab` et `tab2`, et un entier `N` représentant la taille des tableaux.

### **Sortie** :
- `1` si les tableaux sont égaux, `0` sinon.

### **Description** :
Cette fonction compare les éléments correspondants de deux tableaux triés. Si tous les éléments sont identiques, elle retourne `1`, sinon elle retourne `0`.

---

## Inverser tableau

```c
void invert(int *array, int N)
{
    int temp;
    
    for (int i = 0; i < N/2; i++)
    {
        temp = array[i];
        array[i] = array[N-1-i];
        array[N-1-i] = temp;
    }
}
```

### **But de l'algorithme** :
Inverser l'ordre des éléments d'un tableau.

### **Entrée** :
- Un tableau d'entiers `array` et un entier `N` représentant la taille du tableau.

### **Sortie** :
- Le tableau est modifié avec ses éléments dans l'ordre inverse.

### **Description** :
Cette fonction inverse un tableau d'entiers en échangeant les éléments du début et de la fin jusqu'à atteindre le milieu du tableau.