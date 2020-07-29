---
title: Avertissement du compilateur (niveau 1) C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: 551680bc1d24097200a1e641bc4238f883ad94dd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230699"
---
# <a name="compiler-warning-level-1-c4325"></a>Avertissement du compilateur (niveau 1) C4325

> attributs pour la section standard'*section*'ignorés

## <a name="remarks"></a>Notes

Vous ne pouvez pas modifier les attributs d’une section standard. Par exemple :

```cpp
#pragma section(".sdata", long)
```

Cela remplacerait la `.sdata` section standard qui utilise le **`short`** type de données par le **`long`** type de données.

Les sections standard dont vous ne pouvez pas modifier les attributs sont les suivantes :

- . Data

- . sdata

- . BSS

- . sbss

- .text

- . const

- .sconst

- . rdata

- .srdata

Des sections supplémentaires peuvent être ajoutées ultérieurement.

## <a name="see-also"></a>Voir aussi

[section](../../preprocessor/section.md)
