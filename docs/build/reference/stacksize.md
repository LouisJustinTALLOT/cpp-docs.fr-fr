---
title: STACKSIZE
ms.date: 11/04/2016
f1_keywords:
- STACKSIZE
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
ms.openlocfilehash: de2aa99375f588d682b714632590ba8e0db8ddcb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597221"
---
# <a name="stacksize"></a>STACKSIZE

Définit la taille de la pile, en octets.

```
STACKSIZE reserve[,commit]
```

## <a name="remarks"></a>Notes

Pour définir la pile d’une manière équivalente est avec la [Allocations de la pile](../../build/reference/stack-stack-allocations.md) (/Stack) option. Consultez la documentation sur cette option pour plus d’informations la *réserver* et `commit` arguments.

Cette option n’a aucun effet sur les DLL.

## <a name="see-also"></a>Voir aussi

[Règles s’appliquant aux instructions de définition de module](../../build/reference/rules-for-module-definition-statements.md)