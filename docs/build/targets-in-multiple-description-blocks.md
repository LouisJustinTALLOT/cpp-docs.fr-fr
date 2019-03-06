---
title: Cibles dans des blocs de description multiples
ms.date: 11/04/2016
helpviewer_keywords:
- description blocks
- blocks, multiple description
- multiple description blocks
ms.assetid: 8618dcd9-c11d-4562-91a7-0c904ed438a8
ms.openlocfilehash: df5ebba67b3fd041cbf28c90ec25f5a415c0669d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414042"
---
# <a name="targets-in-multiple-description-blocks"></a>Cibles dans des blocs de description multiples

Pour mettre à jour une cible dans plusieurs blocs de description à l’aide des commandes différentes, spécifiez deux signes deux-points consécutifs ( :) entre les cibles des dépendants.

```
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

## <a name="see-also"></a>Voir aussi

[Cibles](../build/targets.md)
