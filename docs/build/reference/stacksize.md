---
title: STACKSIZE
ms.date: 11/04/2016
f1_keywords:
- STACKSIZE
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
ms.openlocfilehash: 2d27b4fd596098f4abc5bb0d804d87bd08f70a60
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318353"
---
# <a name="stacksize"></a>STACKSIZE

Définit la taille de la pile, en octets.

```
STACKSIZE reserve[,commit]
```

## <a name="remarks"></a>Notes

Pour définir la pile d’une manière équivalente est avec la [Allocations de la pile](stack-stack-allocations.md) (/Stack) option. Consultez la documentation sur cette option pour plus d’informations la *réserver* et `commit` arguments.

Cette option n’a aucun effet sur les DLL.

## <a name="see-also"></a>Voir aussi

[Règles s’appliquant aux instructions de définition de module](rules-for-module-definition-statements.md)
