---
title: Opérateurs de bits signés
ms.date: 11/04/2016
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
ms.openlocfilehash: 43f65fd5d1ea14ef5e15f18d9c8516ccf5fb1e08
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158317"
---
# <a name="signed-bitwise-operations"></a>Opérateurs de bits signés

**ANSI 3.3** Résultats des opérations au niveau du bit sur les entiers signés

Les opérations au niveau du bit sur les entiers signés fonctionnent de la même façon que les opérations au niveau du bit sur les entiers non signés. Par exemple, les valeurs `-16 & 99` peuvent être exprimées au format binaire sous la forme

```
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

Le résultat de l'opération de bits AND est 96.

## <a name="see-also"></a>Voir aussi

[Entiers](../c-language/integers.md)
