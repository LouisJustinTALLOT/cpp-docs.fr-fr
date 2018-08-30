---
title: Compilateur avertissement (niveau 1) C4325 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4325
dev_langs:
- C++
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd265938afb51cc402dc84f38b7e95188c6292a7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197483"
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

- .Data

- .sdata

- .BSS

- .sbss

- ".Text"

- .const

- .sconst

- .rdata

- .srdata

Les sections supplémentaires peuvent être ajoutées plus tard.

## <a name="see-also"></a>Voir aussi

[section](../../preprocessor/section.md)