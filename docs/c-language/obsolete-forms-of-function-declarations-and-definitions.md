---
description: 'En savoir plus sur : formes obsolètes des déclarations et définitions de fonctions'
title: Formes obsolètes des déclarations et définitions de fonctions
ms.date: 11/04/2016
helpviewer_keywords:
- old style function declarations
ms.assetid: 67c5038f-0529-4f29-9d0f-c27580977b50
ms.openlocfilehash: 7cd66ba1600d4a5fd381819f4b1d3f0beeb30f0a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256911"
---
# <a name="obsolete-forms-of-function-declarations-and-definitions"></a>Formes obsolètes des déclarations et définitions de fonctions

En comparaison à la syntaxe recommandée par la norme C ANSI, les anciennes définitions et déclarations de fonction utilisent des règles légèrement différentes pour déclarer des paramètres. Premièrement, les anciennes déclarations n'ont pas de liste de paramètres. Ensuite, dans la définition de fonction, les paramètres sont répertoriés, mais leurs types ne sont pas déclarés dans la liste de paramètres. Les déclarations de type précèdent l'instruction composée constituant le corps de la fonction. L'ancienne syntaxe est obsolète et ne doit pas être utilisée dans le nouveau code. Le code utilisant l'ancienne syntaxe est cependant toujours pris en charge. Cet exemple montre les formes obsolètes des déclarations et des définitions :

```
double old_style();           /* Obsolete function declaration */

double alt_style( a , real )  /* Obsolete function definition */
    double *real;
    int a;
{
    return ( *real + a ) ;
}
```

Les fonctions qui retournent un entier ou un pointeur de même taille qu’un **`int`** ne doivent pas obligatoirement avoir une déclaration, bien que la déclaration soit recommandée.

En conformité avec la norme C ANSI, les anciennes déclarations de fonction utilisant des points de suspension génèrent désormais une erreur lors de la compilation avec l'option /Za et un avertissement de niveau 4 lors de la compilation avec /Ze. Par exemple :

```cpp
void funct1( a, ... )  /* Generates a warning under /Ze or */
int a;                 /* an error when compiling with /Za */
{
}
```

Vous devez réécrire cette déclaration en tant que prototype :

```cpp
void funct1( int a, ... )
{
}
```

Les anciennes déclarations de fonction génèrent également des avertissements si vous déclarez ou définissez ensuite la même fonction avec des points de suspension ou avec un paramètre d'un type qui n'est pas identiques au type promu.

La section suivante, [Définitions de fonctions C](../c-language/c-function-definitions.md), explique la syntaxe des définitions de fonctions, y compris l'ancienne syntaxe. L'élément non terminal pour la liste de paramètres dans l'ancienne syntaxe est *identifier-list*.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble des fonctions](../c-language/overview-of-functions.md)
