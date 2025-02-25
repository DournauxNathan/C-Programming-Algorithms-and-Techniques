# Chaînes de caractères

## Inversion de chaîne

```c
void reverse(char* str)
{
    int n = 0;
    
    for (int i = 0; str[i] != '\0'; i++)
    {
        n++;
    }
        
    for (int i = 0; i < n/2; i++)
    {
        char temp = str[i];
        str[i]= str[n - i - 1];
        str[n - i - 1] = temp;
    }
}
```

### **But de l'algorithme** :
Inverser une chaîne de caractères.

### **Entrée** :
- Une chaîne de caractères `str`.

### **Sortie** :
- La chaîne `str` est modifiée avec les caractères dans l'ordre inverse.

### **Description** :
Cette fonction calcule d'abord la longueur de la chaîne puis échange les caractères à partir des extrémités pour inverser l'ordre des caractères.

---

## Rotation alphabétique

```c
void alphaRotate(char* str, int n)
{
    if (n < 0)
    {
        n = 26 + (n % 26);
    }
    else
    {
        n = n % 26;
    }
    
    for(int i = 0; str[i] != '\0'; i++)
    {
        char c = str[i];
        
        if (c >= 'A' && c <= 'Z')
        {
            c = 'A' + (c - 'A' + n) % 26;
        }
        else if (c >= 'a' && c <= 'z')
        {
            c = 'a' + (c - 'a' + n) % 26;
        }
        
        str[i] = c;
    }
}
```

### **But de l'algorithme** :
Effectuer une rotation des lettres d'une chaîne de caractères de `n` positions dans l'alphabet.

### **Entrée** :
- Une chaîne de caractères `str` et un entier `n` représentant le nombre de positions de rotation.

### **Sortie** :
- La chaîne `str` est modifiée avec chaque lettre décalée de `n` positions dans l'alphabet.

### **Description** :
Cette fonction effectue une rotation alphabétique pour chaque caractère de la chaîne, en déplaçant les lettres de l'alphabet par un nombre `n` spécifié.

---

## Générer un nom d'utilisateur

```c
#include <stdio.h>

int isUsernameAlphabetic(char* str)
{
    for (int i = 0; str[i] != '\0'; i++)
    {
        if(isInRange(str[i]))
        {
            return 0;
        }
    }
    return 1;
}

int isInRange(char* c)
{
    if (!((c >= 'A' && c <= 'Z') || (c >= 'a' && c <= 'z')))
    {
        return 1;
    }
    return 0;
}

int toLowerCase(char* str)
{
    for(int i = 0; str[i] != '\0'; i++)
    {
        if (str[i] >= 'A' && str[i] <= 'Z')
        {
            str[i] = str[i] + ('a' - 'A');    
        }
    }
}

int main()
{
    char firstName[50];
    char lastName[50];
    
    scanf("%s", firstName);
    scanf("%s", lastName);
    
    if (!isUsernameAlphabetic(firstName)){
        printf("\"%s\" is not a valid firstname\n", firstName);
    }
    
    if (!isUsernameAlphabetic(lastName)){
        printf("\"%s\" is not a valid lastname\n", lastName);
    }

    char username[8];
    int i = 0;
    
    for (i = 0; i < 7 && lastName[i] != '\0'; i++)
    {
        username[i] = lastName[i];
    }
    
    username[i] = firstName[0];
    i++;
    
    username[i] = '\0';
    
    toLowerCase(username);
        
    if (isUsernameAlphabetic(firstName) && isUsernameAlphabetic(firstName))
    {
        printf("%s", username);
    }
    
    return 0;    
}
```

### **But de l'algorithme** :
Générer un nom d'utilisateur à partir du nom et prénom de l'utilisateur.

### **Entrée** :
- Un prénom `firstName` et un nom `lastName` sous forme de chaînes de caractères.

### **Sortie** :
- Un nom d'utilisateur généré en combinant les 7 premières lettres du nom de famille et la première lettre du prénom, en minuscules.

### **Description** :
Cette fonction génère un nom d'utilisateur en vérifiant que le prénom et le nom sont valides (constitués uniquement de lettres), puis en combinant le nom de famille et la première lettre du prénom pour créer un nom d'utilisateur unique.