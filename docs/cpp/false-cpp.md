---
title: false (C++)
ms.date: 11/04/2016
f1_keywords:
- false_cpp
helpviewer_keywords:
- false keyword [C++]
ms.assetid: cc13aec5-1f02-4d38-8dbf-5473ea2b354f
ms.openlocfilehash: f363e309b91e44472447d040aa36752750afec6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188933"
---
# <a name="false-c"></a>false (C++)

Le mot clé est l’une des deux valeurs d’une variable de type [bool](../cpp/bool-cpp.md) ou d’une expression conditionnelle (une expression conditionnelle est maintenant une **véritable** expression booléenne). Par exemple, si `i` est une variable de type **bool**, l’instruction `i = false;` affecte la **valeur false** à `i`.

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
