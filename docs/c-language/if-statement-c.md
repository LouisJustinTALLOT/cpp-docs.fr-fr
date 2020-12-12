---
description: 'En savoir plus sur : if, instruction (C)'
title: if, instruction (C)
ms.date: 11/04/2016
f1_keywords:
- else
- if
helpviewer_keywords:
- if keyword [C]
- else clauses
- else keyword [C]
- if keyword [C], if statement syntax
- nested statements
ms.assetid: d7fc16a0-fdbc-4f39-b596-76e1ca4ad4a5
ms.openlocfilehash: 07d350329d047e35948ed9819de640e98c5bc13b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182136"
---
# <a name="if-statement-c"></a>if, instruction (C)

L' **`if`** instruction contrôle la branche conditionnelle. Le corps d’une **`if`** instruction est exécuté si la valeur de l’expression est différente de zéro. La syntaxe de l' **`if`** instruction a deux formes.

## <a name="syntax"></a>Syntaxe

instruction *de sélection*:*instruction* **if (***expression***)**      

instruction **if (***expression***)***Statement* **`else`**           

Dans les deux formes de l' **`if`** instruction, les expressions, qui peuvent avoir n’importe quelle valeur, à l’exception d’une structure, sont évaluées, y compris tous les effets secondaires.

Dans la première forme de la syntaxe, si l'élément *expression* est true (différent de zéro), l'élément *statement* est exécuté. Si l'élément *expression* est false, l'élément *statement* est ignoré. Dans la deuxième forme de syntaxe, qui utilise **`else`** , la deuxième *instruction* est exécutée si *expression* a la valeur false. Avec les deux formes, le contrôle passe ensuite de l' **`if`** instruction à l’instruction suivante dans le programme à moins que l’une des instructions contienne un **`break`** , **`continue`** ou **`goto`** .

Voici quelques exemples de l' **`if`** instruction :

```C
if ( i > 0 )
    y = x / i;
else
{
    x = i;
    y = f( x );
}
```

Dans cet exemple, l'instruction `y = x/i;` est exécutée si `i` est supérieur à 0. Si `i` est inférieur ou égal à 0, `i` est assigné à `x` et `f( x )` est assigné à `y`. Notez que l’instruction formant la **`if`** clause se termine par un point-virgule.

Lorsque vous imbriquez **`if`** des instructions et des **`else`** clauses, utilisez des accolades pour regrouper les instructions et les clauses dans des instructions composées qui clarifient votre intention. Si aucune accolade n’est présente, le compilateur résout les ambiguïtés en associant chacune **`else`** à la plus proche **`if`** qui n’a pas de **`else`** .

```C
if ( i > 0 )           /* Without braces */
    if ( j > i )
        x = j;
    else
        x = i;
```

La **`else`** clause est associée à l' **`if`** instruction interne dans cet exemple. Si `i` est inférieur ou égal à 0, aucune valeur n'est assignée à `x`.

```C
if ( i > 0 )
{                      /* With braces */
    if ( j > i )
        x = j;
}
else
    x = i;
```

Les accolades entourant l' **`if`** instruction interne dans cet exemple rendent la **`else`** clause dans la clause de l' **`if`** instruction externe. Si `i` est inférieur ou égal à 0, `i` est assigné à `x`.

## <a name="see-also"></a>Voir aussi

[if-else, instruction (C++)](../cpp/if-else-statement-cpp.md)
