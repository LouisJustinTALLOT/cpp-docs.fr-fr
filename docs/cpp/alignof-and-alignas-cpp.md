---
title: alignof et alignas (C++)
ms.date: 11/04/2016
ms.assetid: 1d18aa8a-9621-4fb5-86e5-4cc86d5187f4
ms.openlocfilehash: 825df25494497e13d29212f7f951be8247b6f136
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155249"
---
# <a name="alignof-and-alignas-c"></a>alignof et alignas (C++)

Le **alignas** spécificateur de type est un moyen de standard C++ portable, pour spécifier un alignement personnalisé des variables et les types définis par l’utilisateur. Le **alignof** opérateur est également un moyen standard et portable pour obtenir l’alignement d’une variable ou un type spécifié.

## <a name="example"></a>Exemple

Vous pouvez utiliser **alignas** sur une classe, struct ou une union, ou sur des membres individuels. Lorsque plusieurs **alignas** spécificateurs sont rencontrés, le compilateur choisit celui plus strict, (celui avec la plus grande valeur).

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
