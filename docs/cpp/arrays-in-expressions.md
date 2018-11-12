---
title: Tableaux dans les expressions
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
ms.openlocfilehash: 0f2ef43c2a5bc4f8a44378c21d6d53b14f07ea07
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478167"
---
# <a name="arrays-in-expressions"></a>Tableaux dans les expressions

Quand un identificateur d’un type tableau apparaît dans une expression autre que `sizeof`, de l’adresse (**&**), ou l’initialisation d’une référence, il est converti en un pointeur vers le premier élément du tableau. Exemple :

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

Le pointeur `psz` pointe vers le premier élément du tableau `szError1`. Notez que les tableaux, contrairement aux pointeurs, ne sont pas des valeurs lvalues modifiables. Par conséquent, l'assignation suivante n'est pas conforme :

```cpp
szError1 = psz;
```

## <a name="see-also"></a>Voir aussi

[Tableaux](../cpp/arrays-cpp.md)