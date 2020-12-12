---
description: 'En savoir plus sur : false (C++)'
title: false (C++)
ms.date: 11/04/2016
f1_keywords:
- false_cpp
helpviewer_keywords:
- false keyword [C++]
ms.assetid: cc13aec5-1f02-4d38-8dbf-5473ea2b354f
ms.openlocfilehash: 73f1f07c858f0a578cc2d3135e560cc8e0cb9d32
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319454"
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
