## Bases du Langage C

Cette section présente des exercices simples pour réviser les bases de la programmation en langage C. Chaque exemple de code est expliqué en détail, accompagné de son but, de ses entrées et sorties, ainsi que de son fonctionnement.

---

### 1. Conversion Horaire
```c
int time = seconds + (minutes * 60) + (hours * 3600);
```
- **But de l'algorithme** : Convertir un temps en secondes à partir d'heures, minutes et secondes.
- **Entrée** : 
  - `seconds` : Nombre de secondes.
  - `minutes` : Nombre de minutes.
  - `hours` : Nombre d'heures.
- **Sortie** : `time` : Le temps total en secondes.
- **Description** : Cette ligne de code convertit le temps exprimé en heures, minutes et secondes en un total de secondes.

---

### 2. Conversion Horaire 2
```c
int seconds;
int minutes;
int hours;

hours = time / 3600;
minutes = (time % 3600) / 60;
seconds = time % 60;
```
- **But de l'algorithme** : Convertir un temps en secondes en heures, minutes et secondes.
- **Entrée** : 
  - `time` : Temps total en secondes.
- **Sortie** : 
  - `hours` : Nombre d'heures.
  - `minutes` : Nombre de minutes.
  - `seconds` : Nombre de secondes.
- **Description** : Cette portion de code convertit un nombre total de secondes en heures, minutes et secondes.

---

### 3. Valeur ASCII
```c
if (a > b){
    printf("WRONG INPUT");
    return 0;
}

for(char c = a; c <= b; c++)
{
    printf("'%c' : %d \n", c, c);
}
```
- **But de l'algorithme** : Afficher les caractères et leurs valeurs ASCII dans un intervalle donné.
- **Entrée** : 
  - `a` et `b` : Valeurs représentant les bornes du caractère à afficher.
- **Sortie** : Affiche chaque caractère entre `a` et `b` avec sa valeur ASCII.
- **Description** : Ce code parcourt un intervalle de caractères (de `a` à `b`) et affiche pour chaque caractère sa représentation ASCII.

---

### 4. Affichage d'un Rectangle
```c
#include <stdio.h>

int main(){
    int w, h;
    scanf("%d %d",&w,&h);
    if(w<1 || h<1){
        printf("WRONG INPUT\n");
        return 0;
    }
    if(w>1)printf("+");
    for(int i = 1; i < w-1; i++)printf("-");
    printf("+\n");
    for(int j = 1; j < h-1; j++){
        if(w>1)printf("|");
        for(int i = 1; i < w-1; i++)printf("#");
        printf("|\n");
    }
    if(h>1){
        if(w>1)printf("+");
        for(int i = 1; i < w-1; i++)printf("-");
        printf("+\n");
    }

    return 0;
}
```
- **But de l'algorithme** : Afficher un rectangle constitué de "+" pour les coins, de "-" pour les bords supérieurs et inférieurs, et de "#" pour le remplissage intérieur.
- **Entrée** : 
  - `w` : Largeur du rectangle.
  - `h` : Hauteur du rectangle.
- **Sortie** : Affiche un rectangle formé par des caractères ASCII dans la console.
- **Description** : Ce programme prend la largeur et la hauteur d'un rectangle en entrée et affiche un rectangle à l'écran.

---

### 5. Table de Multiplication
```c
#include <stdio.h>

int main (){
    int n;
    
    scanf("%d", &n);
    
    for (int i = 1; i <= 10; i++){
        
        printf("%5d x %5d = %5d\n", i, n, (i*n));
    }
    
    return 0;
}
```
- **But de l'algorithme** : Afficher la table de multiplication d'un nombre `n` de 1 à 10.
- **Entrée** : 
  - `n` : Le nombre pour lequel afficher la table de multiplication.
- **Sortie** : Affiche la table de multiplication du nombre `n` jusqu'à 10.
- **Description** : Ce programme prend un nombre `n` et affiche sa table de multiplication de 1 à 10.

---

### 6. Table de Multiplication (Alignement à Gauche)
```c
int main (){
    int n;
    
    scanf("%d", &n);
    
    for (int i = 1; i <= 10; i++){
        
        printf("%-5d x %-5d = %-5d\n", i, n, (i*n));
    }
    
    return 0;
}
```
- **But de l'algorithme** : Afficher la table de multiplication d'un nombre `n` avec un alignement à gauche.
- **Entrée** : 
  - `n` : Le nombre pour lequel afficher la table de multiplication.
- **Sortie** : Affiche la table de multiplication du nombre `n` de manière alignée à gauche.
- **Description** : Ce programme fonctionne de manière similaire au précédent, mais cette fois, il aligne les résultats à gauche.

---

### 7. Calculette
```c
#include <stdio.h>

int main()
{
    int a, b;
    char s;
    
    scanf("%d %c %d", &a, &s, &b);
    
    switch(s) 
    {
        case '+':
            printf("%d", a + b);
            break;
        case '-':
            printf("%d", a - b);
            break;
        case 'x':
            printf("%d", a * b);
            break;
        case '/':
            if(b == 0)
            {
                printf("DIV BY 0 NOT ALLOWED");
            }
            else
            {
                printf("%.2f", (float)a / b);
            }
            break;
        default:
            printf("RTFM");
            break;
    }
    
    return 0;
}
```
- **But de l'algorithme** : Réaliser une opération arithmétique de base entre deux nombres.
- **Entrée** : 
  - `a` et `b` : Les deux nombres à manipuler.
  - `s` : L'opérateur arithmétique ( +, -, x, / ).
- **Sortie** : Le résultat de l'opération ou un message d'erreur.
- **Description** : Ce programme demande deux nombres et un opérateur, puis effectue l'opération correspondante. Il gère également l'erreur de division par zéro.

---