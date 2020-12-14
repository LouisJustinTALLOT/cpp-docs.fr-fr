---
description: 'En savoir plus sur les éléments suivants : STACKSIZE'
title: STACKSIZE
ms.date: 11/04/2016
f1_keywords:
- STACKSIZE
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
ms.openlocfilehash: b5d52bccc09979084b9023d380e86fe90e4def32
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230339"
---
# <a name="stacksize"></a>STACKSIZE

Définit la taille de la pile, en octets.

```
STACKSIZE reserve[,commit]
```

## <a name="remarks"></a>Notes

Une méthode équivalente pour définir la pile est avec l’option [allocations](stack-stack-allocations.md) de la pile (/Stack). Pour plus d’informations sur la *réserve* et les arguments, consultez la documentation relative à cette option `commit` .

Cette option n’a aucun effet sur les dll.

## <a name="see-also"></a>Voir aussi

[Règles pour les instructions Module-Definition](rules-for-module-definition-statements.md)
