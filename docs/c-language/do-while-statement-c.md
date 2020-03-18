---
title: do-while, instruction (C)
ms.date: 11/04/2016
f1_keywords:
- do
helpviewer_keywords:
- do-while keyword [C]
ms.assetid: f2ac20a6-10c7-4a08-b5e3-c3b3639dbeaf
ms.openlocfilehash: 3658fe7635ad77db6d6e08ff9d7c30e29d665721
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438590"
---
# <a name="do-while-statement-c"></a>do-while, instruction (C)

L'instruction *do-while* vous permet de répéter une instruction ou une instruction composée jusqu'à ce qu'une expression spécifiée devienne false.

## <a name="syntax"></a>Syntaxe

*Iteration-Statement*: &nbsp;&nbsp;&nbsp;&nbsp;instruction **do***statement***while (** *expression* **);**

L'élément *expression* dans une instruction *do-while* est évalué après l'exécution du corps de la boucle. Par conséquent, le corps de la boucle est toujours exécuté au moins une fois.

L'élément *expression* doit être de type arithmétique ou pointeur. L'exécution se déroule comme suit :

1. Le corps de l'instruction est exécuté.

1. Ensuite, l'élément *expression* est évalué. Si l'élément *expression* est false, l'instruction *do-while* se termine et le contrôle passe à l'instruction suivante du programme. Si l'élément *expression* est true (différent de zéro), le processus se répète, en commençant à l'étape 1.

L'instruction *do-while* peut également se terminer lorsqu'une instruction **break**, **goto** ou **return** est exécutée dans le corps de l'instruction.

Voici un exemple d'instruction *do-while* :

```C
do
{
    y = f( x );
    x--;
} while ( x > 0 );
```

Dans cette instruction *do-while*, les deux instructions `y = f( x );` et `x--;` sont exécutées, quelle que soit la valeur initiale de `x`. Ensuite, `x > 0` est évalué. Si `x` est supérieur à 0, le corps de l'instruction est réexécuté et `x > 0` est réévalué. Le corps de l'instruction est exécuté à plusieurs reprises tant que `x` reste supérieur à 0. L'exécution de l'instruction *do-while* se termine lorsque `x` devient 0 ou négatif. Le corps de la boucle est exécuté au moins une fois.

## <a name="see-also"></a>Voir aussi

[do-while, instruction (C++)](../cpp/do-while-statement-cpp.md)
