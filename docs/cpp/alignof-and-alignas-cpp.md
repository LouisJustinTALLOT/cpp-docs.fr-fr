---
title: alignof et alignas (C++)
ms.date: 11/04/2016
ms.assetid: 1d18aa8a-9621-4fb5-86e5-4cc86d5187f4
ms.openlocfilehash: e5d023d7969764bdd36030a508abdd94068e48b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493650"
---
# <a name="alignof-and-alignas-c"></a>alignof et alignas (C++)

Le **alignas** spécificateur de type est un moyen de standard C++ portable, pour spécifier un alignement personnalisé des variables et les types définis par l’utilisateur. Le **alignof** opérateur est également un moyen standard et portable pour obtenir l’alignement d’une variable ou un type spécifié.

## <a name="example"></a>Exemple

Vous pouvez utiliser **alignas** sur une classe, struck ou une union, ou sur des membres individuels. Lorsque plusieurs **alignas** spécificateurs sont rencontrés, le compilateur choisit celui plus strict, (celui avec la plus grande valeur).

```cpp
// alignas_alignof.cpp
// compile with: cl /EHsc alignas_alignof.cpp
#include <iostream>

struct alignas(16) Bar
{
    int i;       // 4 bytes
    int n;      // 4 bytes
    alignas(4) char arr[3];
    short s;          // 2 bytes
};

int main()
{
    std::cout << alignof(Bar) << std::endl; // output: 16
}
```

## <a name="see-also"></a>Voir aussi

[Alignement](../cpp/alignment-cpp-declarations.md)