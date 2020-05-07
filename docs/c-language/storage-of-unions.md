---
title: Stockage des unions
ms.date: 11/04/2016
helpviewer_keywords:
- storage, union
- union keyword [C], storage
- union keyword [C]
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
ms.openlocfilehash: 49b99dc17fd7bdddd8a47e3bfd5913a70a7631a7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157921"
---
# <a name="storage-of-unions"></a>Stockage des unions

Le stockage associé à une variable d'union est le stockage requis pour le plus grand membre de l'union. Lorsqu'un membre plus petit est stocké, la variable d'union peut contenir l'espace mémoire non utilisé. Tous les membres sont stockés dans le même espace mémoire et démarrent à la même adresse. La valeur stockée est remplacée chaque fois qu'une valeur est assignée à un autre membre. Par exemple :

```
union         /* Defines a union named x */
{
    char *a, b;
    float f[20];
} x;
```

Les membres de l'union `x` sont, dans l'ordre de leur déclaration, un pointeur vers une valeur `char`, une valeur `char` et un tableau de valeurs **float**. Le stockage alloué pour `x` est le stockage requis pour le tableau `f`de 20 éléments, car `f` est le membre le plus long de l'union. Étant donné qu’aucune étiquette n’est associée à l’union, son type est sans nom ou « anonyme ».

## <a name="see-also"></a>Voir aussi

[Déclarations d'union](../c-language/union-declarations.md)
