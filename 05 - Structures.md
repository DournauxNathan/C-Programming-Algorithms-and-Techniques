### **Structure Point**
```c
#ifndef _POINT_H_
#define _POINT_H_

typedef struct 
{
    float x;
    float y;
} Point;

#endif
```

- **But de l'algorithme** : Définir une structure pour représenter un point dans un plan à 2 dimensions.
- **Entrée** : Aucune, il s'agit d'une déclaration de type de structure.
- **Sortie** : Aucune, c'est juste une définition de type.
- **Description** : Cette structure définit un point par ses coordonnées x et y.

---

### **Structure Point, allocation**
```c
#ifndef _POINT_H_
#define _POINT_H_

typedef struct 
{
    float x;
    float y;
} Point;

Point* createPoint(float x, float y);
void freePoint(Point** p);

#endif
```

- **But de l'algorithme** : Créer une fonction d'allocation dynamique pour un point.
- **Entrée** : Les coordonnées `x` et `y` d'un point.
- **Sortie** : Un pointeur vers la structure `Point` allouée dynamiquement.
- **Description** : La fonction `createPoint` alloue de la mémoire pour un objet `Point` et initialise ses coordonnées. `freePoint` libère cette mémoire.

---

### **Structure Point, affichage**
```c
#ifndef _POINT_H_
#define _POINT_H_

typedef struct 
{
    float x;
    float y;
} Point;

Point* createPoint(float x, float y);
void freePoint(Point** p);
void displayPoint(Point* p);

#endif
```

- **But de l'algorithme** : Ajouter une fonction pour afficher les coordonnées d'un point.
- **Entrée** : Un pointeur vers un `Point`.
- **Sortie** : Affichage des coordonnées `x` et `y` du point.
- **Description** : La fonction `displayPoint` affiche les valeurs des coordonnées `x` et `y` d'un point.

---

### **Structure Point, addition**
```c
#ifndef _POINT_H_
#define _POINT_H_

typedef struct 
{
    float x;
    float y;
} Point;

Point* createPoint(float x, float y);
void freePoint(Point** p);
void displayPoint(Point* p);
Point* add(Point* p1, Point* p2);

#endif
```

- **But de l'algorithme** : Ajouter une fonction pour additionner deux points.
- **Entrée** : Deux pointeurs vers des `Point`.
- **Sortie** : Un pointeur vers un nouveau `Point`, résultat de l'addition des deux autres.
- **Description** : La fonction `add` additionne les coordonnées des deux points et retourne un nouveau point avec les coordonnées résultantes.

---

### **Structure Array**
```c
#ifndef _ARRAY_H_
#define _ARRAY_H_

typedef struct
{
    int* tab;
    int size;
} Array;

#endif
```

- **But de l'algorithme** : Définir une structure pour représenter un tableau dynamique d'entiers.
- **Entrée** : Aucune, il s'agit d'une déclaration de type de structure.
- **Sortie** : Aucune, c'est juste une définition de type.
- **Description** : Cette structure contient un tableau d'entiers (`tab`) et la taille du tableau (`size`).

---

### **Structure Array, allocation et initialisation**
```c
#ifndef _ARRAY_H_
#define _ARRAY_H_

typedef struct
{
    int* tab;
    int size;
} Array;

#endif
```

- **But de l'algorithme** : Allouer et initialiser un tableau dynamique dans une structure `Array`.
- **Entrée** : La taille du tableau et une valeur d'initialisation.
- **Sortie** : Un pointeur vers une structure `Array` avec le tableau initialisé.
- **Description** : La structure `Array` est allouée dynamiquement avec l'espace nécessaire pour contenir les éléments.

---

### **Structure Array, concaténation**
```c
#ifndef _ARRAY_H_
#define _ARRAY_H_

typedef struct
{
    int* tab;
    int size;
} Array;

Array* createArray(int size, int value);
void freeArray(Array** array);
Array* concat(Array* p1, Array* p2);

#endif
```

- **But de l'algorithme** : Concaténer deux tableaux dynamiques dans une nouvelle structure `Array`.
- **Entrée** : Deux pointeurs vers des structures `Array`.
- **Sortie** : Un pointeur vers une nouvelle structure `Array` contenant la concaténation des deux tableaux.
- **Description** : La fonction `concat` fusionne les tableaux contenus dans les deux structures et crée une nouvelle structure qui les contient tous les deux.

---

### **Structure Array, statistiques**
```c
#ifndef _ARRAY_H_
#define _ARRAY_H_

typedef struct
{
    int* tab;
    int size;
} Array;

Array* createArray(int size, int value);
void freeArray(Array** array);
Array* concat(Array* p1, Array* p2);

int minArray(Array* a);
int maxArray(Array* a);
int sumArray(Array* a);
int averageArray(Array* a);

#endif
```

- **But de l'algorithme** : Fournir des fonctions statistiques sur le tableau.
- **Entrée** : Un pointeur vers une structure `Array`.
- **Sortie** : Les valeurs statistiques demandées (min, max, somme, moyenne).
- **Description** : Les fonctions `minArray`, `maxArray`, `sumArray`, et `averageArray` permettent de calculer les valeurs respectives à partir des éléments du tableau contenu dans une structure `Array`.

---

### **Structure People**
```c
#ifndef _PEOPLE_H_
#define _PEOPLE_H_

typedef struct
{
    char* firstname;
    char* lastname;
    int age;
} People;

#endif
```

- **But de l'algorithme** : Définir une structure pour représenter une personne.
- **Entrée** : Aucune, il s'agit d'une déclaration de type de structure.
- **Sortie** : Aucune, c'est juste une définition de type.
- **Description** : La structure `People` contient les informations d'une personne : prénom, nom de famille et âge.

---

### **Structure People, initialisation**
```c
#ifndef _PEOPLE_H_
#define _PEOPLE_H_

typedef struct
{
    char* firstname;
    char* lastname;
    int age;
} People;

People* createPeople(char* firstname, char* lastname, int age);

#endif
```

- **But de l'algorithme** : Allouer et initialiser une structure `People`.
- **Entrée** : Le prénom, le nom de famille et l'âge de la personne.
- **Sortie** : Un pointeur vers une structure `People` allouée dynamiquement.
- **Description** : La fonction `createPeople` crée une nouvelle structure `People` avec les informations données.

---

### **Structure People, âme soeur**
```c
#ifndef _PEOPLE_H_
#define _PEOPLE_H_

typedef struct people
{
    char* firstname;
    char* lastname;
    int age;
    struct people* soulmate;
} People;

People* createPeople(char* firstname, char* lastname, int age);
void bindPeoples(People* a, People* b);
void removePeople(People** p);

#endif
```

- **But de l'algorithme** : Lier deux personnes et créer des fonctions de gestion de la mémoire.
- **Entrée** : Deux pointeurs vers des structures `People`.
- **Sortie** : La fonction `bindPeoples` établit une relation de "soulmate" entre deux personnes.
- **Description** : La fonction `bindPeoples` lie deux structures `People` en assignant l'un à l'autre comme âme soeur.

---

### **Structure People, comparateurs**
```c
#ifndef _PEOPLE_H_
#define _PEOPLE_H_

typedef struct people
{
    char* firstname;
    char* lastname;
    int age;
    struct people* soulmate;
} People;

People* createPeople(char* firstname, char* lastname, int age);
void bindPeoples(People* a, People* b);
void removePeople(People** p);

int  comparePeoplesByAge(People* a, People* b);
int  comparePeoplesByName(People* a, People* b);

#endif
```

- **But de l'algorithme** : Comparer deux personnes sur la base de leur âge ou de leur nom.
- **Entrée** : Deux pointeurs vers des structures `People`.
- **Sortie** : Un entier indiquant l'ordre entre les deux personnes comparées.
- **Description** : Les fonctions `comparePeoplesByAge` et `comparePeoplesByName` comparent deux structures `People` en fonction de leur âge ou de leur nom.

---

### **Structure People, PeopleList**
```c
#ifndef _PEOPLE_H_
#define _PEOPLE_H_

typedef struct people
{
    char* firstname;
    char* lastname;
    int age;
    struct people* soulmate;
} People;

People* createPeople(char* firstname, char* lastname, int age);

void removePeople(People** p);

void bindPeoples(People* a, People* b);

int comparePeoplesByAge(People* a, People* b);

int comparePeoplesByName(People* a, People* b);
#endif
```

- **But de l'algorithme** : Gérer une liste de personnes et leurs relations.
- **Entrée** : Aucune entrée spécifique pour la structure, mais des fonctions pour lier, retirer et comparer les personnes.
- **Sortie** : Aucune sortie spécifique, mais gestion de la mémoire et des comparaisons entre les personnes.
- **Description** : Cette structure et les fonctions associées permettent de manipuler des objets `People` dans un contexte de gestion d'une liste, avec des fonctions de comparaison et de gestion des relations.

Il semble que tu souhaites simplement la version "retirée" de la structure `People` sans certaines fonctions. Voici une version mise à jour de ton code :

---

### **Structure People, PeopleList : retrait**

```c
#ifndef _PEOPLE_H_
#define _PEOPLE_H_

typedef struct people
{
    char* firstname;
    char* lastname;
    int age;
    struct people* soulmate;
} People;

People* createPeople(char* firstname, char* lastname, int age);
void removePeople(People** p);
void bindPeoples(People* a, People* b);
int comparePeoplesByAge(People* a, People* b);
int comparePeoplesByName(People* a, People* b);

#endif
```

- **But de l'algorithme** : Définir une structure `People` représentant des personnes avec des attributs de base et des fonctions pour gérer les relations et effectuer des comparaisons.
- **Entrée** : Les fonctions prennent en entrée des pointeurs vers des structures `People` (pour créer, supprimer, lier et comparer).
- **Sortie** : 
    - `createPeople` : Retourne un pointeur vers un `People` alloué dynamiquement.
    - `removePeople` : Supprime une structure `People` allouée dynamiquement.
    - `bindPeoples` : Crée une relation de "soulmate" entre deux personnes.
    - `comparePeoplesByAge` et `comparePeoplesByName` : Comparent deux structures `People` et retournent un entier pour déterminer l'ordre.