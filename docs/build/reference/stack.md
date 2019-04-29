---
title: /STACK
ms.date: 11/04/2016
f1_keywords:
- /stack
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
ms.openlocfilehash: 6f30877800d4597054601f7459df88c78193fd3c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318496"
---
# <a name="stack"></a>/STACK

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>Notes

Cette option définit la taille de la pile en octets et accepte des arguments en notation décimale ou en langage C. L’option /STACK s’applique uniquement à un fichier exécutable.

Le *réserver* argument spécifie l’allocation de pile total dans la mémoire virtuelle. EDITBIN arrondit la valeur spécifiée aux 4 octets plus proches.

Le paramètre facultatif `commit` argument est soumis à l’interprétation par le système d’exploitation. Dans Windows NT, Windows 95 et Windows 98, `commit` spécifie la quantité de mémoire physique à allouer à la fois. Mémoire virtuelle dédiée, espace à réserver dans le fichier d’échange. Un degré plus élevé `commit` valeur fait gagner du temps lorsque l’application a besoin de davantage d’espace pile, mais augmente les besoins en mémoire et éventuellement les temps de démarrage.

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](editbin-options.md)
