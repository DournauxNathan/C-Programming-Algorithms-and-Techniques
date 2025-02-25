# Pointeurs

## Fonction Swap

```c
void swap(int* a, int* b)
{
    int temp = *a;
    *a = *b;
    *b = temp;
}
```

### **But de l'algorithme** :
Permet d'échanger les valeurs de deux entiers.

### **Entrée** :
- Deux entiers, passés par référence (pointeurs).

### **Sortie** :
- Les deux entiers ont été échangés.

### **Description** :
Cette fonction échange les valeurs de deux variables entières en utilisant des pointeurs. Elle prend en paramètres les adresses de ces entiers et effectue l'échange via un pointeur temporaire.

---

## Minimum d'un tableau

```c
int minimum(int *array, int N)
{
    if (N <= 0)
    {
        return 0;    
    }
    
    int min = array[0];
    
    for (int i = 0; i < N; i++)
    {
        if (array[i] < min)
        {
            min = array[i];
        }
    }
    
    return min;
}
```

### **But de l'algorithme** :
Trouver et retourner la valeur minimale d'un tableau d'entiers.

### **Entrée** :
- Un tableau d'entiers `array` et un entier `N` représentant la taille du tableau.

### **Sortie** :
- La valeur minimale du tableau.

### **Description** :
Cette fonction parcourt chaque élément du tableau pour déterminer le minimum. Si le tableau est vide ou invalide (`N <= 0`), la fonction retourne 0.