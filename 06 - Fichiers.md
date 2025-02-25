### **Lire un fichier texte, ligne par ligne**

```c
char** readLines(char* filename) 
{
    char** lines = (char**) malloc(101 * sizeof(char*));

    if (lines == NULL) {
        return NULL;  // Vérification de l'allocation
    }

    FILE* file = fopen(filename, "r");
    if (file == NULL) {
        free(lines);  // Libération en cas d'erreur
        return NULL;
    }

    char buffer[200];
    int lineCount = 0;

    for (lineCount = 0; lineCount < 100; lineCount++) {
        if (fgets(buffer, sizeof(buffer), file) == NULL) {
            break;
        }

        int length = 0;

        while (buffer[length] != '\0' && buffer[length] != '\n') {
            length++;
        }

        lines[lineCount] = (char*) malloc((length + 1) * sizeof(char));
        if (lines[lineCount] == NULL) {
            for (int i = 0; i < lineCount; i++) {
                free(lines[i]);
            }
            free(lines);
            fclose(file);
            return NULL;
        }

        for (int i = 0; i < length; i++) {
            lines[lineCount][i] = buffer[i];
        }

        lines[lineCount][length] = '\n';  // Ajout du caractère nul à la fin
    }

    lines[lineCount] = NULL;

    fclose(file);

    return lines;
}
```

**But de l'algorithme** : Lire un fichier texte et stocker chaque ligne dans un tableau de chaînes de caractères.

**Entrée** : 
- `filename` : nom du fichier texte à lire.

**Sortie** :
- `char**` : un tableau de chaînes de caractères contenant chaque ligne du fichier. La dernière ligne est marquée par `NULL`.

**Description** :
L'algorithme alloue de la mémoire pour un tableau de chaînes de caractères. Il ouvre le fichier en mode lecture, puis lit chaque ligne du fichier et l'ajoute dans le tableau jusqu'à un maximum de 100 lignes. Si une erreur d'allocation de mémoire se produit, le programme libère les ressources et renvoie `NULL`.

---

### **Lire un tableau d'entiers dans un fichier binaire**

```c
int* readIntArray(char* filename, int* N)
{
    FILE* file = fopen(filename, "rb");
    
    if (file == NULL) 
    {
        return NULL; 
    }

    if (fread(N, sizeof(int), 1, file) != 1) 
    {
        fclose(file);
        return NULL; 
    }

    int* array = (int*) malloc(sizeof(int) * (*N));
    
    if (array == NULL) 
    {
        fclose(file);
        return NULL; 
    }

    if (fread(array, sizeof(int), *N, file) != *N) 
    {
        free(array); 
        fclose(file);
        return NULL; 
    }

    fclose(file);

    return array;
}
```

**But de l'algorithme** : Lire un tableau d'entiers à partir d'un fichier binaire.

**Entrée** : 
- `filename` : nom du fichier binaire à lire.
- `N` : un pointeur vers un entier où sera stocké le nombre d'éléments dans le tableau.

**Sortie** :
- `int*` : un tableau d'entiers contenant les données lues du fichier.

**Description** :
L'algorithme ouvre un fichier binaire en mode lecture. Il lit d'abord la taille du tableau d'entiers (stockée dans `N`), puis alloue dynamiquement de la mémoire pour le tableau. Ensuite, les éléments sont lus du fichier et stockés dans le tableau. Si une erreur survient lors de l'une des étapes (lecture ou allocation), l'algorithme nettoie les ressources et retourne `NULL`.

---

### **Écrire un tableau d'entiers dans un fichier binaire**

```c
void writeIntArray(char* filename, int* tab, int N)
{
    FILE* file = fopen(filename, "wb");
    
    if (file == NULL)
    {
        return;
    }
    
    fwrite(&N, sizeof(int), 1, file);
    
    fwrite(tab, sizeof(int), N, file);
    
    fclose(file);
}
```

**But de l'algorithme** : Écrire un tableau d'entiers dans un fichier binaire.

**Entrée** :
- `filename` : nom du fichier binaire dans lequel écrire.
- `tab` : tableau d'entiers à écrire.
- `N` : taille du tableau.

**Sortie** :
- Aucune (l'algorithme modifie le fichier en écrivant dedans).

**Description** :
Cet algorithme ouvre un fichier binaire en mode écriture. Il écrit d'abord la taille du tableau, puis les éléments du tableau dans le fichier. Si l'ouverture du fichier échoue, l'algorithme termine sans rien écrire.

---

### **Ajouter un tableau d'entiers dans un fichier binaire**

```c
void appendIntArray(char* filename, int* tab, int N)
{
    FILE* file = fopen(filename, "rb+");
    
    if (file == NULL)
    {
        file = fopen(filename, "wb+");
        
        if (file == NULL)
        {
            return;
        }
        
        fwrite(&N, sizeof(int), 1, file);
        fwrite(tab, sizeof(int), N, file);
    }
    else
    {
        int oldSize;
        
        fread(&oldSize, sizeof(int), 1, file);
        
        fseek(file, 0, SEEK_END);
        
        int newSize = oldSize + N;
        fwrite(tab, sizeof(int), N, file);
        fseek(file, 0, SEEK_SET);
        fwrite(&newSize, sizeof(int), 1, file);
    }
    
    fclose(file);
}
```

**But de l'algorithme** : Ajouter un tableau d'entiers à un fichier binaire existant.

**Entrée** :
- `filename` : nom du fichier binaire à modifier.
- `tab` : tableau d'entiers à ajouter.
- `N` : taille du tableau à ajouter.

**Sortie** :
- Aucune (l'algorithme modifie le fichier).

**Description** :
L'algorithme ouvre un fichier binaire en mode lecture-écriture (`rb+`). Si le fichier n'existe pas, il est créé. Dans tous les cas, l'algorithme lit la taille du tableau déjà existant, ajoute les nouveaux éléments à la fin du fichier, puis met à jour la taille totale du fichier.

---

### **Écrire un tableau de structures simples dans un fichier binaire**

```c
void writePointArray(char* filename, Point* tab, int N)
{
    FILE* file = fopen(filename, "wb");
    
    if (file == NULL)
    {
        return;
    }
    
    fwrite(&N, sizeof(int), 1, file);
    
    fwrite(tab, sizeof(Point), N, file);
    
    fclose(file);
}
```

**But de l'algorithme** : Écrire un tableau de structures simples dans un fichier binaire.

**Entrée** :
- `filename` : nom du fichier binaire.
- `tab` : tableau de structures `Point` à écrire.
- `N` : nombre d'éléments dans le tableau.

**Sortie** :
- Aucune (le fichier est modifié).

**Description** :
L'algorithme ouvre un fichier binaire en mode écriture, écrit d'abord le nombre d'éléments (`N`), puis les éléments du tableau de structures `Point`. Si le fichier ne peut être ouvert, aucune donnée n'est écrite.

---

### **Lire un tableau de structures simples dans un fichier binaire**

```c
Point* readPointArray(char* filename, int* N)
{
    FILE* file = fopen(filename, "rb");
    
    if (file == NULL)
    {
        return NULL;
    }
    
    fread(N, sizeof(int), 1, file);
    
    if (*N <= 0)
    {
        fclose(file);
        return NULL;
    }
    
    Point* points = (Point*) malloc(sizeof(Point) * (*N));
    
    if (points == NULL)
    {
        fclose(file);
        return NULL;
    }
    
    fread(points, sizeof(Point), *N, file);
    
    fclose(file);
    
    return points;
}
```

**But de l'algorithme** : Lire un tableau de structures simples depuis un fichier binaire.

**Entrée** :
- `filename` : nom du fichier binaire à lire.
- `N` : pointeur vers un entier qui sera mis à jour avec la taille du tableau lu.

**Sortie** :
- `Point*` : tableau de structures `Point` lu depuis le fichier.

**Description** :
L'algorithme ouvre un fichier binaire en mode lecture. Il lit d'abord le nombre d'éléments dans le tableau et alloue de la mémoire pour stocker ces éléments. Ensuite, il lit les éléments du tableau et les place dans un tableau de structures `Point`. Si des erreurs surviennent à n'importe quelle étape (lecture ou allocation), les ressources sont nettoyées et `NULL` est renvoyé.

---

### **Écrire une structure contenant des allocations dynamiques dans un fichier**

```c
void writePeople(char* filename, People* p)
{
    FILE* file = fopen(filename, "wb");
    
    if (file == NULL)
    {
        return;
    }
    
    for (int i = 0; p -> firstname[i] != '\0'; i++)
    {
        fputc(p -> firstname[i], file);
    }
    fputc('\0', file);
    
    for ( int i = 0; p -> lastname[i] != '\0'; i++)
    {
        fputc(p -> lastname[i], file);
    }
    fputc('\0', file);

    for (int i = 0; i < sizeof(int); i++)
    {
        fputc(((char*) &(p -> age))[i], file);
    }
    
    fclose(file);
}
```

**But de l'algorithme** : Écrire une structure contenant des allocations dynamiques dans un fichier binaire.

**Entrée** :
- `filename` : nom du fichier où la structure sera sauvegardée.
- `p` : pointeur vers la structure `People` contenant des champs alloués dynamiquement (`firstname`, `lastname`, `age`).

**Sortie** :
- Aucune (le fichier est modifié).

**Description** :
Cet algorithme écrit les données d'une structure `People` dans un fichier binaire. Il écrit les chaînes de caractères `firstname` et `lastname` caractère par caractère, suivi de leur terminaison `'\0'`. Ensuite, il écrit la valeur entière `age` en utilisant son adresse en mémoire pour la convertir en octets. Le fichier est ensuite fermé.

---

### **Lire une structure contenant des allocations dynamiques depuis un fichier**

```c
char* readString(FILE* f){
    char buffer[1000];
    int index=0;
    do{
        fread(buffer+index, sizeof(char), 1, f);
    }
    while(buffer[index++]!='\0');
    char * res = (char*)malloc(sizeof(char)*index);
    strcpy(res, buffer);
    return res;
}

People* readPeople(char* filename){
    FILE* f = fopen(filename, "r");
    People* p = (People*)malloc(sizeof(People));
    p->firstname = readString(f);
    p->lastname = readString(f);
    fread(&(p->age), sizeof(int), 1, f);
    return p;
}
```

**But de l'algorithme** : Lire une structure contenant des allocations dynamiques depuis un fichier binaire.

**Entrée** :
- `filename` : nom du fichier à lire.

**Sortie** :
- Un pointeur vers la structure `People` contenant les données lues depuis le fichier.

**Description** :
Cet algorithme ouvre un fichier binaire en mode lecture, puis lit les chaînes de caractères `firstname` et `lastname` ainsi que la valeur entière `age` dans la structure `People`. Les chaînes sont lues à l'aide d'une fonction `readString` qui alloue dynamiquement de la mémoire pour les stocker. Après la lecture, un pointeur vers la structure `People` contenant les données lues est retourné.

---

### **Lire un tableau de bits depuis un fichier binaire**

```c
int ceil(float num) {
    int inum = (int)num;
    if (num == (float)inum) {
        return inum;
    }
    return inum + 1;
}

char* readBitArray(char* filename, int* n) {
    FILE *f;
    char *bits = NULL;
    int i;
    int j;

    f = fopen(filename, "rb");

    if (f != NULL) {
        fread(n, sizeof(int), 1, f);
        bits = malloc(*n * sizeof(char));

        if (bits != NULL) {
            char byte;
            short index;

            for (i = 0; i < ceil((float)*n / 8); i++) {
                fread(&byte, sizeof(char), 1, f);

                for (j = 7; 0 <= j; j--) {
                    index = i * 8 + j;
                    if (index < *n) {
                        bits[index] = (byte >> j) & 0x01;
                        bits[index] += '0';
                    }
                }
            }
        }
    }

    return bits;
}
```

**But de l'algorithme** : Lire un tableau de bits depuis un fichier binaire.

**Entrée** :
- `filename` : nom du fichier contenant les données binaires.
- `n` : pointeur vers un entier qui recevra la taille du tableau de bits.

**Sortie** :
- Un tableau de caractères représentant les bits (0 ou 1).

**Description** :
Cet algorithme ouvre un fichier binaire en mode lecture et lit d'abord la taille du tableau de bits (`n`). Ensuite, il alloue dynamiquement de la mémoire pour stocker les bits. Le fichier est lu octet par octet, chaque bit de chaque octet étant extrait et stocké dans le tableau `bits` sous forme de caractères (`'0'` ou `'1'`). La fonction `ceil` est utilisée pour calculer le nombre d'octets nécessaires pour stocker tous les bits. Enfin, le tableau de bits est retourné.