## Les Fonctions en Langage C

Cette section aborde la définition de fonctions en C, ainsi que la conception de fonctions récursives. Chaque fonction est expliquée avec ses objectifs, son fonctionnement, et les cas où elle peut être utilisée.

---

### 1. Fonction Puissance
```c
int puissance(x, n) {
    int outcome = x;

    if (n == 0) {
        return 1;
    }

    for (int i = 1; i < n; i++) {
        outcome *= x;
    }
    return outcome;
}
```
- **But de l'algorithme** : Calculer la puissance `x^n` (x élevé à la puissance n).
- **Entrée** : 
  - `x` : La base.
  - `n` : L'exposant.
- **Sortie** : La valeur de `x` élevé à la puissance `n`.
- **Description** : Cette fonction calcule la puissance en multipliant `x` par lui-même `n` fois. Si l'exposant est 0, le résultat est 1 (cas spécial).

---

### 2. Fonction PGCD (Plus Grand Commun Diviseur)
```c
int pgcd(a, b) {
    if (a < 0) a = -a;
    if (b < 0) b = -b;

    while (a != b) {
        if (a > b) {
            a = a - b;
        } else {
            b = b - a;
        }
    }
    return a;
}
```
- **But de l'algorithme** : Calculer le plus grand commun diviseur (PGCD) de deux nombres.
- **Entrée** : 
  - `a` et `b` : Les deux nombres pour lesquels calculer le PGCD.
- **Sortie** : Le PGCD de `a` et `b`.
- **Description** : Cette fonction utilise l'algorithme d'Euclide pour calculer le PGCD de deux nombres. Elle applique une série de soustractions répétées jusqu'à ce que les deux nombres deviennent égaux.

---

### 3. Fonction Récursive Factorielle
```c
int factorielle(n) {
    if (n > 0) {
        return n * factorielle(n - 1);
    }

    return 1;
}
```
- **But de l'algorithme** : Calculer la factorielle de `n` (n!).
- **Entrée** : 
  - `n` : Le nombre pour lequel calculer la factorielle.
- **Sortie** : La factorielle de `n`.
- **Description** : Cette fonction utilise la récursion pour calculer la factorielle de `n`. Si `n` est 0 ou 1, la factorielle est 1, sinon la fonction s'appelle elle-même avec `n-1`.

---

### 4. Fonction Récursive Fibonacci
```c
int fibonacci(n) {
    if (n == 0) {
        return 0;
    } else if (n == 1) {
        return 1;
    } else {
        return fibonacci(n-1) + fibonacci(n-2);
    }

    return 0;
}
```
- **But de l'algorithme** : Calculer le n-ième nombre de la suite de Fibonacci.
- **Entrée** : 
  - `n` : L'indice du nombre dans la suite de Fibonacci.
- **Sortie** : Le n-ième nombre de la suite de Fibonacci.
- **Description** : Cette fonction utilise la récursion pour calculer un nombre dans la suite de Fibonacci. Si `n` est 0 ou 1, elle retourne respectivement 0 ou 1. Sinon, elle effectue une récursion pour additionner les deux termes précédents.

---

### 5. Test de Primalité
```c
int isPrimeNumber(int n) {
    if (n <= 0) {
        return 0;
    } else {
        for (int i = 2; i < n; i++) {
            if (n % i == 0) {
                return 0;
            }
        }
    }
    return 1; // Aucun diviseur trouvé
}
```
- **But de l'algorithme** : Vérifier si un nombre est premier.
- **Entrée** : 
  - `n` : Le nombre à tester.
- **Sortie** : Retourne 1 si le nombre est premier, sinon retourne 0.
- **Description** : Cette fonction teste si un nombre `n` est divisible par un autre nombre entre 2 et `n-1`. Si un diviseur est trouvé, elle retourne 0 (non premier), sinon elle retourne 1 (nombre premier).

---

### 6. Décomposition en Facteurs Premiers
```c
int factors(int n) {
    if (n <= 1) {
        return 0;
    }

    int firstFactor = 1;

    while (n % 2 == 0) {
        if (firstFactor) {
            printf("%d = 2", n);
            firstFactor = 0;
        } else {
            printf(" x 2");
        }

        n /= 2;
    }

    for (int i = 3; i * i <= n; i += 2) {
        while (n % i == 0) {
            if (firstFactor) {
                printf("%d = %d", n, i);
                firstFactor = 0;
            } else {
                printf(" x %d", i);
            }
            n /= i;
        }
    }

    if (n > 1) {
        if (firstFactor) {
            printf("%d est premier", n);
        } else {
            printf(" x %d\n", n);
        }
    } else {
        printf("\n");
    }
}
```
- **But de l'algorithme** : Décomposer un nombre en ses facteurs premiers.
- **Entrée** : 
  - `n` : Le nombre à décomposer.
- **Sortie** : Affiche les facteurs premiers de `n`.
- **Description** : Cette fonction décompose le nombre `n` en ses facteurs premiers. Elle commence par diviser par 2, puis teste les autres facteurs impairs jusqu'à la racine carrée de `n`. Si `n` reste supérieur à 1, il est lui-même un facteur premier.

---
