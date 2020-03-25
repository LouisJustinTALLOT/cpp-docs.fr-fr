---
title: Avertissement du compilateur (niveau 1) C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: e0a13761b0657d054065358994638779817dad6a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163022"
---
# <a name="compiler-warning-level-1-c4325"></a>Avertissement du compilateur (niveau 1) C4325

> attributs pour la section standard'*section*'ignorés

## <a name="remarks"></a>Notes

Vous ne pouvez pas modifier les attributs d’une section standard. Par exemple :

```cpp
#pragma section(".sdata", long)
```

Cela remplacerait la section `.sdata` standard qui utilise le type de données **short** avec le type de données **long** .

Les sections standard dont vous ne pouvez pas modifier les attributs sont les suivantes :

- .data

- .sdata

- . BSS

- . sbss

- .text

- .const

- .sconst

- .rdata

- .srdata

Des sections supplémentaires peuvent être ajoutées ultérieurement.

## <a name="see-also"></a>Voir aussi

[section](../../preprocessor/section.md)
