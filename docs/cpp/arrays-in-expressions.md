---
title: Tableaux dans les Expressions | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34f8a45dfa9de9a5a48e13cb6a38f667e5963f2d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068544"
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