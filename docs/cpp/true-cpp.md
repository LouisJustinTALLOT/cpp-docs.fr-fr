---
title: true (C++)
ms.date: 11/04/2016
f1_keywords:
- true_cpp
helpviewer_keywords:
- true keyword [C++]
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
ms.openlocfilehash: f6420d0abea8bac1d385c1cfdfd58a5500cf5bd3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87185838"
---
# <a name="true-c"></a>true (C++)

## <a name="syntax"></a>Syntaxe

```
bool-identifier = true ;
bool-expression logical-operator true ;
```

## <a name="remarks"></a>Notes

Ce mot clé est l’une des deux valeurs d’une variable de type [bool](../cpp/bool-cpp.md) ou d’une expression conditionnelle (une expression conditionnelle est maintenant une véritable expression booléenne). Si `i` est de type **`bool`** , l’instruction `i = true;` assigne **`true`** à `i` .

## <a name="example"></a>Exemple

```cpp
// bool_true.cpp
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
