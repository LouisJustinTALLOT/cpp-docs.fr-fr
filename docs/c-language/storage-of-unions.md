---
title: Stockage des unions
ms.date: 11/04/2016
helpviewer_keywords:
- storage, union
- union keyword [C], storage
- union keyword [C]
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
ms.openlocfilehash: 06444151a453017055667885304ecb59534f5774
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602226"
---
# <a name="storage-of-unions"></a>Stockage des unions

Le stockage associé à une variable d'union est le stockage requis pour le plus grand membre de l'union. Lorsqu'un membre plus petit est stocké, la variable d'union peut contenir l'espace mémoire non utilisé. Tous les membres sont stockés dans le même espace mémoire et démarrent à la même adresse. La valeur stockée est remplacée chaque fois qu'une valeur est assignée à un autre membre. Exemple :

```
union         /* Defines a union named x */
{
    char *a, b;
    float f[20];
} x;
```

Les membres de l'union `x` sont, dans l'ordre de leur déclaration, un pointeur vers une valeur `char`, une valeur `char` et un tableau de valeurs **float**. Le stockage alloué pour `x` est le stockage requis pour le tableau `f`de 20 éléments, car `f` est le membre le plus long de l'union. Étant donné qu’aucune étiquette n’est associée à l’union, son type est sans nom ou « anonyme ».

## <a name="see-also"></a>Voir aussi

[Déclarations d’union](../c-language/union-declarations.md)