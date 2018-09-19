---
title: Spécificateurs de classe de stockage pour les déclarations de niveau externe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e4f2e80c22d7a341f5b44b77fc14ada8eb2f0098
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066609"
---
# <a name="storage-class-specifiers-for-external-level-declarations"></a>Spécificateurs de classe de stockage pour les déclarations de niveau externe

Les variables externes sont des variables au niveau de la portée du fichier. Elles sont définies en dehors de toute fonction et sont potentiellement disponibles pour de nombreuses fonctions. Les fonctions ne peuvent être définies qu'au niveau externe, par conséquent elles ne peuvent pas être imbriquées. Par défaut, toutes les références aux variables externes et aux fonctions du même nom sont des références au même objet, ce qui signifie qu'elles possèdent une « liaison externe. » (Vous pouvez utiliser le mot clé **static** pour modifier ce comportement. Pour plus d'informations sur le mot clé **static**, consultez les informations plus loin dans cette section.)

Les déclarations de variables au niveau externe sont des définitions de variables (« déclarations de définition ») ou des références aux variables définies ailleurs (« déclarations de référencement »).

Une déclaration de variable externe qui initialise aussi la variable (implicitement ou explicitement) est une déclaration de définition de la variable. Une définition au niveau externe peut prendre plusieurs formes :

- Une variable que vous déclarez avec le spécificateur de classe de stockage **static**. Vous pouvez initialiser explicitement la variable **static** avec une expression constante, comme indiqué dans la section [Initialisation](../c-language/initialization.md). Si vous omettez l'initialiseur, la variable est initialisée à 0 par défaut. Par exemple, les deux instructions suivantes sont les deux définitions reconnues de la variable `k`.

    ```
    static int k = 16;
    static int k;
    ```

- Une variable que vous initialisez explicitement au niveau externe. Par exemple, `int j = 3;` est une définition de la variable `j`.

Dans les déclarations de variables au niveau externe (c'est-à-dire en dehors de toutes les fonctions), vous pouvez utiliser le spécificateur de classe de stockage **static** ou `extern`, ou omettre le spécificateur de classe de stockage entièrement. Vous ne pouvez pas utiliser les éléments terminaux *storage-class-specifier* **auto** et **register** au niveau externe.

Une fois qu'une variable est définie au niveau externe, elle est visible dans le reste de l'unité de traduction. La variable n'est pas visible avant sa déclaration dans le même fichier source. En outre, elle n'est pas visible dans les autres fichiers sources du programme, à moins qu'une déclaration de référencement la rende visible, comme expliqué ci-dessous.

Les règles relatives à **static** sont les suivantes :

- Les variables déclarées à l'extérieur de tous les blocs sans le mot clé **static** conservent toujours leur valeur dans le programme. Pour limiter leur accès à une unité de traduction spécifique, vous devez utiliser le mot clé **static**. Cela leur confère une « liaison interne ». Pour les rendre globales dans un programme entier, omettez la classe de stockage explicite ou utilisez le mot clé `extern` (consultez les règles dans la liste suivante). Cela leur confère une « liaison externe ». Les liaisons interne et externe sont également abordées dans la rubrique [Liaison](../c-language/linkage.md).

- Vous pouvez définir une variable au niveau externe une seule fois à l'intérieur d'un programme. Vous pouvez définir une autre variable avec le même nom et le spécificateur de classe de stockage **static** dans une autre unité de traduction. Étant donné que chaque définition **static** est visible uniquement dans sa propre unité de traduction, aucun conflit ne se produit. Cela permet de masquer les noms d'identificateur qui doivent être partagés entre les fonctions d'une même unité de traduction mais rester invisibles pour les autres unités de traduction.

- Le spécificateur de classe de stockage **static** peut s'appliquer également aux fonctions. Si vous déclarez une fonction **static**, son nom est invisible en dehors du fichier dans lequel elle est déclarée.

Les règles relatives à l'utilisation d'`extern` sont les suivantes :

- Le spécificateur de classe de stockage `extern` déclare une référence à une variable définie ailleurs. Vous pouvez utiliser une déclaration `extern` pour rendre une définition dans un autre fichier source visible, ou pour rendre une variable visible avant sa définition dans le même fichier source. Une fois que vous avez déclaré une référence à la variable au niveau externe, la variable est visible dans le reste de l'unité de traduction dans laquelle la référence déclarée apparaît.

- Pour qu'une référence à `extern` soit valide, il faut que la variable à laquelle elle fait référence soit définie une seule fois au niveau externe. Cette définition (sans la classe de stockage `extern`) peut se trouver dans n'importe laquelle des unités de traduction qui composent le programme.

## <a name="example"></a>Exemple

L'exemple ci-dessous illustre les déclarations externes :

```
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

```
int i = 3;
```

définit la variable globale `i` et l'initialise avec la valeur initiale 3. La déclaration de « référencement » de `i` en haut du premier fichier source via le mot clé `extern` rend la variable globale visible avant sa déclaration de définition dans le fichier. La déclaration de référencement de `i` dans le deuxième fichier source rend également visible la variable dans ce fichier. Si une instance de définition n'est pas indiquée pour une variable dans l'unité de traduction, le compilateur suppose qu'il existe

```
extern int x;
```

une déclaration de référencement et qu'une référence de définition

```
int x = 0;
```

figure dans une autre unité de traduction du programme.

Les trois fonctions, `main`, `next` et `other`, exécutent la même tâche : elles augmentent `i` et l'impriment. Les valeurs 4, 5 et 6 sont imprimées.

Si la variable `i` n'avait pas été initialisée, elle aurait été définie à 0 automatiquement. Dans ce cas, les valeurs 1, 2 et 3 auraient été imprimées. Pour plus d'informations sur l'initialisation des variables, consultez [Initialisation](../c-language/initialization.md).

## <a name="see-also"></a>Voir aussi

[Classes de stockage C](../c-language/c-storage-classes.md)