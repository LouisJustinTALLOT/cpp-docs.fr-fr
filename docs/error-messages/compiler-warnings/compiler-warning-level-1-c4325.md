---
title: Avertissement du compilateur (niveau 1) C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: 293cbbcfe134f6cb4f5e1bf924be7c03fa278833
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408535"
---
# <a name="compiler-warning-level-1-c4325"></a>Avertissement du compilateur (niveau 1) C4325

> attributs pour la section «*section*' ignoré

## <a name="remarks"></a>Notes

Impossible de modifier les attributs d’une section standard. Exemple :

```cpp
#pragma section(".sdata", long)
```

Cela remplacerait la `.sdata` section standard qui utilise le **court** type de données avec le **long** type de données.

Sections standards dont vous ne pouvez pas modifier les attributs incluent,

- .data

- .sdata

- .bss

- .sbss

- .text

- .const

- .sconst

- .rdata

- .srdata

Les sections supplémentaires peuvent être ajoutées plus tard.

## <a name="see-also"></a>Voir aussi

[section](../../preprocessor/section.md)