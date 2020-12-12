---
description: En savoir plus sur:/STACK
title: /STACK
ms.date: 11/04/2016
f1_keywords:
- /stack_editbin
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
ms.openlocfilehash: 253aec1d760a85f1ebe5dbf7596353b46744cd57
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224450"
---
# <a name="stack"></a>/STACK

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>Notes

Cette option définit la taille de la pile en octets et prend des arguments en notation décimale ou de langage C. L’option/STACK s’applique uniquement à un fichier exécutable.

L’argument *Reserve* spécifie le nombre total d’allocations de piles dans la mémoire virtuelle. EDITBIN arrondit la valeur spécifiée aux 4 octets les plus proches.

L' `commit` argument facultatif est soumis à une interprétation par le système d’exploitation. Dans Windows NT, Windows 95 et Windows 98, `commit` spécifie la quantité de mémoire physique à allouer à la fois. La mémoire virtuelle validée entraîne la réservation de l’espace dans le fichier d’échange. Une valeur plus élevée permet de `commit` gagner du temps lorsque l’application a besoin de davantage d’espace de pile, mais augmente les besoins en mémoire et éventuellement le temps de démarrage.

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](editbin-options.md)
