---
title: false (C++)
ms.date: 11/04/2016
f1_keywords:
- false_cpp
helpviewer_keywords:
- false keyword [C++]
ms.assetid: cc13aec5-1f02-4d38-8dbf-5473ea2b354f
ms.openlocfilehash: d6162bdde3dea0d245a0c83c1d52b06003fee16c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227489"
---
# <a name="false-c"></a>false (C++)

Le mot clé est l’une des deux valeurs d’une variable de type [bool](../cpp/bool-cpp.md) ou d’une expression conditionnelle (une expression conditionnelle est maintenant une **`true`** expression booléenne). Par exemple, si `i` est une variable de type **`bool`** , l' `i = false;` instruction assigne **`false`** à `i` .

## <a name="example"></a>Exemple

```cpp
// bool_false.cpp
#include <stdio.h>

int main()
{
    bool bb = true;
    printf_s("%d\n", bb);
    bb = false;
    printf_s("%d\n", bb);
}
```

```Output
1
0
```

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)
