### **Inversion des bits d'un nombre**

```c
unsigned char reverseBits(unsigned char  x){
    
    unsigned char reverseX = 0;
    
    for (int i = 0; i < 8; i++)
    {
        reverseX <<= 1;
        
        reverseX |= (x & 1);
        
        x >>= 1;
    }
    
    return reverseX;
}
```

**But de l'algorithme** : Inverser l'ordre des bits d'un octet.

**Entrée** :
- `x` : un caractère non signé de 8 bits.

**Sortie** :
- L'octet avec les bits inversés.

**Description** :
Cet algorithme prend un octet et inverse l'ordre de ses bits. Pour chaque bit de l'octet, il le place à la position correspondante dans le résultat en décalant les bits à gauche et en utilisant l'opérateur `|=` pour ajouter le bit actuel. L'octet est décalé vers la droite pour examiner chaque bit.

---

### **Affichage binaire d'un entier**

```c
void binaryDisplay(int x){
    int i = 0;
    
    for (i = 31; i >= 0; i--)
    {
        printf("%d", (x >> i) & 1);
        
        if (i % 8 == 0 && i != 0)
        {
            printf(" ");
        }
    }
}
```

**But de l'algorithme** : Afficher la représentation binaire d'un entier.

**Entrée** :
- `x` : un entier à afficher en binaire.

**Sortie** :
- Aucun, mais l'entier est affiché en binaire sur la sortie standard.

**Description** :
Cet algorithme parcourt les 32 bits d'un entier, décalant les bits vers la droite et utilisant l'opérateur `&` avec `1` pour extraire chaque bit. Il affiche les bits sous forme de `0` ou `1` et insère des espaces tous les 8 bits pour une lecture plus facile.

---

### **Cryptage par XOR**

```c
char* cryptoXOR(char* text, int N, char* password, int M)
{
    // Allocation d'un tableau de taille N
    char* result = (char*) malloc(sizeof(char) * N);

    for (int i = 0; i < N; i++)
    {
        result[i] = text[i] ^ password[i % M];
    }

    result[N] = '\n';

    return result;
}
```

**But de l'algorithme** : Crypter un texte en utilisant l'opérateur XOR avec un mot de passe.

**Entrée** :
- `text` : le texte à crypter.
- `N` : la taille du texte.
- `password` : le mot de passe utilisé pour le cryptage.
- `M` : la taille du mot de passe.

**Sortie** :
- Le texte crypté.

**Description** :
Cet algorithme applique un cryptage XOR sur chaque caractère du texte avec un caractère du mot de passe (en utilisant l'index modulo la taille du mot de passe). Chaque caractère du résultat est le résultat de l'opération XOR entre le caractère du texte et le caractère du mot de passe. Le texte crypté est retourné.

---

### **Composer une recette avec des ingrédients à l'aide d'opérations sur les bits**

```c
unsigned int recette1 = SALADE | TOMATE | OIGNON | KETCHUP | MAYO;
unsigned int recette2 = OIGNON | SAMURAI | ARISSA | PITA | FROMAGE;
```

**But de l'algorithme** : Composer une recette à l'aide des ingrédients et des opérations sur les bits.

**Entrée** :
- `SALADE`, `TOMATE`, `OIGNON`, etc. : des constantes représentant des ingrédients.

**Sortie** :
- Des variables `recette1` et `recette2` composées d'ingrédients par l'usage d'opérations `|` (OR) pour combiner les ingrédients.

**Description** :
Cet algorithme utilise des opérations sur les bits pour composer une recette à partir d'ingrédients. Chaque ingrédient est représenté par un bit différent, et la combinaison des ingrédients se fait avec l'opération `|`, qui ajoute un bit pour chaque ingrédient.

---

### **Afficher une recette**

```c
void displayKebab(unsigned int recette)
{
    int first = 1;
    
    for (int i = 1; i <= FROMAGE; i <<= 1) 
    { 
        switch (i) 
        {
            case SALADE:
                if (recette & SALADE)
                {
                    if (!first) printf(" ");
                    printf("SALADE");
                    first = 0;
                }
                break;
            case TOMATE:
                if (recette & TOMATE) 
                {
                    if (!first) printf(" ");
                    printf("TOMATE");
                    first = 0;
                }
                break;
            case OIGNON:
                if (recette & OIGNON) 
                {
                    if (!first) printf(" ");
                    printf("OIGNON");
                    first = 0;
                }
                break;
            case KETCHUP:
                if (recette & KETCHUP) 
                {
                    if (!first) printf(" ");
                    printf("KETCHUP");
                    first = 0;
                }
                break;
            case MAYO:
                if (recette & MAYO) 
                {
                    if (!first) printf(" ");
                    printf("MAYO");
                    first = 0;
                }
                break;
            case SAMURAI:
                if (recette & SAMURAI) 
                {
                    if (!first) printf(" ");
                    printf("SAMURAI");
                    first = 0;
                }
                break;
            case BLANCHE:
                if (recette & BLANCHE) 
                {
                    if (!first) printf(" ");
                    printf("BLANCHE");
                    first = 0;
                }
                break;
            case ARISSA:
                if (recette & ARISSA)
                {
                    if (!first) printf(" ");
                    printf("ARISSA");
                    first = 0;
                }
                break;
            case PITA:
                if (recette & PITA) 
                {
                    if (!first) printf(" ");
                    printf("PITA");
                    first = 0;
                }
                break;
            case FRITES:
                if (recette & FRITES)
                {
                    if (!first) printf(" ");
                    printf("FRITES");
                    first = 0;
                }
                break;
            case FROMAGE:
                if (recette & FROMAGE) 
                {
                    if (!first) printf(" ");
                    printf("FROMAGE");
                    first = 0;
                }
                break;
        }
    }

    printf("\n");
}
```

**But de l'algorithme** : Afficher une recette sous forme de chaîne lisible en fonction des ingrédients représentés par des bits.

**Entrée** :
- `recette` : un entier représentant la combinaison des ingrédients sous forme de bits.

**Sortie** :
- Aucun, mais affiche la recette sur la sortie standard.

**Description** :
Cet algorithme parcourt les différents ingrédients représentés par des bits dans l'entier `recette` et affiche les ingrédients présents dans la recette. Il utilise des opérateurs de masque (`&`) pour vérifier la présence de chaque ingrédient et les affiche en conséquence.

---

### **Modifier une recette**

```c
unsigned int modifKebab(unsigned int recette, char* modifs){
    
    for (int i= 0; modifs[i] != '\0'; i += 2)
    {
        char operation = modifs[i]; // +, -, ou ~
        char ingredient = modifs[i + 1]; // S, T, O, k, m, s, b, a, p, f, c
        int flag = 0;
        
        switch (ingredient)
        {
            case 'S': flag = SALADE; break;
            case 'T': flag = TOMATE; break;
            case 'O': flag = OIGNON; break;
            case 'k': flag = KETCHUP; break;
            case 'm': flag = MAYO; break;
            case 's': flag = SAMURAI; break;
            case 'b': flag = BLANCHE; break;
            case 'a': flag = ARISSA; break;
            case 'p': flag = PITA; break;
            case 'f': flag = FRITES; break;
            case 'c': flag = FROMAGE; break;
            default: break; 
        }
        
        switch(operation)
        {
            case '+':
                recette |= flag;
                break;
            case '-':
                recette &= ~flag;
                break;
            case '~':
                recette ^= flag;
                break;
            default:
                break;
        }
        
    }
    
    return recette;
}
```

**But de l'algorithme** : Modifier une recette en fonction des instructions fournies.

**Entrée** :
- `recette` : la recette à modifier.
- `modifs` : une chaîne de caractères contenant des opérations (`+`, `-`, `~`) et des ingrédients.

**Sortie** :
- La recette modifiée.

**Description** :
Cet algorithme permet de modifier une recette en fonction des instructions fournies dans `modifs`. Chaque modification consiste à appliquer une opération binaire (`|`, `&`, `^`) sur les ingrédients de la recette. L'opération correspond à l'ajout (`+`), la suppression (`-`) ou l'inversion (`~`) de l'ingrédient dans la recette.