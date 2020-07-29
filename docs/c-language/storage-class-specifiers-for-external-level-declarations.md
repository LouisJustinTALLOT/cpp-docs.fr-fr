---
title: Spécificateurs de classe de stockage pour les déclarations de niveau externe
ms.date: 11/04/2016
helpviewer_keywords:
- external definitions
- linkage [C++], external
- external linkage, variable declarations
- declaring variables, external variables
- declarations [C++], external
- declarations [C++], specifiers
- external declarations
- static variables, external declarations
- variables, visibility
- external linkage, storage-class specifiers
- referencing declarations
- visibility, variables
- static storage class specifiers
ms.assetid: b76b623a-80ec-4d5d-859b-6cef422657ee
ms.openlocfilehash: 6c30b8a12c0bf26bc35905872fb6fa527b367ef4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229465"
---
# <a name="storage-class-specifiers-for-external-level-declarations"></a>Spécificateurs de classe de stockage pour les déclarations de niveau externe

Les variables externes sont des variables au niveau de la portée du fichier. Elles sont définies en dehors de toute fonction et sont potentiellement disponibles pour de nombreuses fonctions. Les fonctions ne peuvent être définies qu'au niveau externe, par conséquent elles ne peuvent pas être imbriquées. Par défaut, toutes les références aux variables externes et aux fonctions du même nom sont des références au même objet, ce qui signifie qu’elles ont une *liaison externe*. (Vous pouvez utiliser le **`static`** mot clé pour remplacer ce comportement.)

Les déclarations de variables au niveau externe sont des définitions de variables (*définition de déclarations*) ou des références aux variables définies ailleurs (déclarations de*référence*).

Une déclaration de variable externe qui initialise aussi la variable (implicitement ou explicitement) est une déclaration de définition de la variable. Une définition au niveau externe peut prendre plusieurs formes :

- Variable que vous déclarez avec le **`static`** spécificateur de classe de stockage. Vous pouvez initialiser explicitement la **`static`** variable avec une expression constante, comme décrit dans [initialisation](../c-language/initialization.md). Si vous omettez l'initialiseur, la variable est initialisée à 0 par défaut. Par exemple, les deux instructions suivantes sont les deux définitions reconnues de la variable `k`.

    ```C
    static int k = 16;
    static int k;
    ```

- Une variable que vous initialisez explicitement au niveau externe. Par exemple, `int j = 3;` est une définition de la variable `j`.

Dans les déclarations de variables au niveau externe (autrement dit, en dehors de toutes les fonctions), vous pouvez utiliser le **`static`** **`extern`** spécificateur de classe de stockage ou ou omettre le spécificateur de classe de stockage entièrement. Vous ne pouvez pas utiliser les **`auto`** **`register`** *`storage-class-specifier`* terminaux et au niveau externe.

Une fois qu'une variable est définie au niveau externe, elle est visible dans le reste de l'unité de traduction. La variable n'est pas visible avant sa déclaration dans le même fichier source. En outre, elle n'est pas visible dans les autres fichiers sources du programme, à moins qu'une déclaration de référencement la rende visible, comme expliqué ci-dessous.

Les règles relatives aux **`static`** sont les suivantes :

- Les variables déclarées en dehors de tous les blocs sans le **`static`** mot clé conservent toujours leurs valeurs dans l’ensemble du programme. Pour limiter leur accès à une unité de traduction particulière, vous devez utiliser le **`static`** mot clé. Cela leur donne une *liaison interne*. Pour les rendre globaux à un programme entier, omettez la classe de stockage explicite ou utilisez le mot clé **`extern`** (consultez les règles dans la liste suivante). Cela leur donne une *liaison externe*. Les liaisons interne et externe sont également abordées dans la rubrique [Liaison](../c-language/linkage.md).

- Vous pouvez définir une variable au niveau externe une seule fois à l'intérieur d'un programme. Vous pouvez définir une autre variable avec le même nom et le **`static`** spécificateur de classe de stockage dans une unité de traduction différente. Étant donné que chaque **`static`** définition est visible uniquement dans sa propre unité de traduction, aucun conflit ne se produit. Il offre un moyen utile de masquer les noms d’identificateur qui doivent être partagés entre les fonctions d’une seule unité de traduction, mais qui ne sont pas visibles par les autres unités de traduction.

- Le **`static`** spécificateur de classe de stockage peut également s’appliquer aux fonctions. Si vous déclarez une fonction **`static`** , son nom est invisible en dehors du fichier dans lequel elle est déclarée.

Les règles d’utilisation de **`extern`** sont les suivantes :

- Le **`extern`** spécificateur de classe de stockage déclare une référence à une variable définie ailleurs. Vous pouvez utiliser une **`extern`** déclaration pour rendre une définition dans un autre fichier source visible, ou pour rendre une variable visible avant sa définition dans le même fichier source. Une fois que vous avez déclaré une référence à la variable au niveau externe, la variable est visible dans le reste de l’unité de traduction dans laquelle la référence déclarée se produit.

- Pour qu’une **`extern`** référence soit valide, la variable à laquelle elle fait référence doit être définie une fois, et une seule fois, au niveau externe. Cette définition (sans la **`extern`** classe de stockage) peut se trouver dans l’une des unités de traduction qui composent le programme.

## <a name="example"></a>Exemple

L'exemple ci-dessous illustre les déclarations externes :

```C
/******************************************************************
                      SOURCE FILE ONE
*******************************************************************/
#include <stdio.h>

extern int i;                // Reference to i, defined below
void next( void );           // Function prototype

int main()
{
    i++;
    printf_s( "%d\n", i );   // i equals 4
    next();
}

int i = 3;                  // Definition of i

void next( void )
{
    i++;
    printf_s( "%d\n", i );  // i equals 5
    other();
}

/******************************************************************
                      SOURCE FILE TWO
*******************************************************************/
#include <stdio.h>

extern int i;              // Reference to i in
                           // first source file
void other( void )
{
    i++;
    printf_s( "%d\n", i ); // i equals 6
}
```

Les deux fichiers sources dans cet exemple contiennent au total trois déclarations externes de `i`. Seule une d'elle est une « déclaration de définition. » Celle-ci,

```C
int i = 3;
```

définit la variable globale `i` et l'initialise avec la valeur initiale 3. La déclaration de « référencement » de `i` en haut du premier fichier source qui utilise **`extern`** rend la variable globale visible avant sa déclaration de définition dans le fichier. La déclaration de référencement de `i` dans le deuxième fichier source rend également visible la variable dans ce fichier. Si une instance de définition n'est pas indiquée pour une variable dans l'unité de traduction, le compilateur suppose qu'il existe

```C
extern int x;
```

une déclaration de référencement et qu'une référence de définition

```C
int x = 0;
```

figure dans une autre unité de traduction du programme.

Les trois fonctions, `main`, `next` et `other`, exécutent la même tâche : elles augmentent `i` et l'impriment. Les valeurs 4, 5 et 6 sont imprimées.

Si la variable n' `i` avait pas été initialisée, elle aurait été définie à 0 automatiquement. Dans ce cas, les valeurs 1, 2 et 3 auraient été imprimées. Pour plus d'informations sur l'initialisation des variables, consultez [Initialisation](../c-language/initialization.md).

## <a name="see-also"></a>Voir aussi

[Classes de stockage C](../c-language/c-storage-classes.md)
