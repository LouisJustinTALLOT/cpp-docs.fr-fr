---
title: if, instruction (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- else
- if
dev_langs:
- C++
helpviewer_keywords:
- if keyword [C]
- else clauses
- else keyword [C]
- if keyword [C], if statement syntax
- nested statements
ms.assetid: d7fc16a0-fdbc-4f39-b596-76e1ca4ad4a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98b01db4d842775dcb239aef9d40c661328d1544
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107876"
---
# <a name="if-statement-c"></a>if, instruction (C)

L’instruction **if** contrôle le branchement conditionnel. Le corps d'une instruction **if** est exécuté si la valeur de l'expression est différente de zéro. La syntaxe de l'instruction **if** a deux formes.

## <a name="syntax"></a>Syntaxe

*selection-statement*: **if (**  *expression*  **)**  *statement*

**if (**  *expression*  **)**  *statement*  **else**  *statement*

Dans les deux formes de l'instruction **if**, les expressions (qui peuvent avoir n'importe quelle valeur sauf une structure) sont évaluées, y compris tous les effets secondaires.

Dans la première forme de la syntaxe, si l'élément *expression* est true (différent de zéro), l'élément *statement* est exécuté. Si l'élément *expression* est false, l'élément *statement* est ignoré. Dans la deuxième forme de la syntaxe, qui utilise **else**, le deuxième élément *statement* est exécuté si l'élément *expression* est false. Avec les deux formes, le contrôle passe ensuite de l'instruction **if** à l'instruction suivante dans le programme à moins que l'une des instructions contienne **break**, **continue** ou `goto`.

Voici quelques exemples d'instruction **if** :

```
if ( i > 0 )
    y = x / i;
else
{
    x = i;
    y = f( x );
}
```

Dans cet exemple, l'instruction `y = x/i;` est exécutée si `i` est supérieur à 0. Si `i` est inférieur ou égal à 0, `i` est assigné à `x` et `f( x )` est assigné à `y`. Notez que l'instruction qui forme la clause **if** se termine par un point-virgule.

Lors de l'imbrication d'instructions **if** et de clauses **else**, utilisez des accolades pour grouper les instructions et les clauses dans des instructions composites qui clarifient votre intention. Si aucune accolade n'est présente, le compilateur résout les ambiguïtés en associant chaque **else** avec **l'if** le plus proche auquel il manque un **else**.

```
if ( i > 0 )           /* Without braces */
    if ( j > i )
        x = j;
    else
        x = i;
```

La clause **else** est associée à l'instruction**if** interne dans cet exemple. Si `i` est inférieur ou égal à 0, aucune valeur n'est assignée à `x`.

```
if ( i > 0 )
{                      /* With braces */
    if ( j > i )
        x = j;
}
else
    x = i;
```

Les accolades entourant les instructions **if** internes dans cet exemple composent la partie clause **else** de l'instruction **if** externe. Si `i` est inférieur ou égal à 0, `i` est assigné à `x`.

## <a name="see-also"></a>Voir aussi

[if-else, instruction (C++)](../cpp/if-else-statement-cpp.md)