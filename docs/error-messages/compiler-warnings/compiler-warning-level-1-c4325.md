---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4325'
title: Avertissement du compilateur (niveau 1) C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: 17e14d4909e4b76d6a0a71d6e77fad1d01e3f41b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311589"
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
