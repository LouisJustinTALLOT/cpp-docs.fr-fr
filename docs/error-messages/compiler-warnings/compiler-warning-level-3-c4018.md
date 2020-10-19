---
title: Avertissement du compilateur (niveau 3) C4018
description: Avertissement du compilateur Microsoft C/C++ C4018, ses causes et sa résolution.
ms.date: 10/16/2020
f1_keywords:
- C4018
helpviewer_keywords:
- C4018
ms.openlocfilehash: b9d01f6b733c2ca18880aa6f4b6fca9771f8123f
ms.sourcegitcommit: f19f02f217b80804ab321d463c76ce6f681abcc6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92176178"
---
# <a name="compiler-warning-level-3-c4018"></a>Avertissement du compilateur (niveau 3) C4018

> '*Token*' : incompatibilité signed/unsigned

L’utilisation de l’opérateur de *jeton* pour comparer **`signed`** et des **`unsigned`** nombres nécessitait que le compilateur convertisse la **`signed`** valeur en **`unsigned`** .

## <a name="remarks"></a>Notes

Une façon de résoudre cet avertissement est si vous effectuez un cast de l’un des deux types lorsque vous comparez **`signed`** des **`unsigned`** types et.

## <a name="example"></a>Exemple

Cet exemple génère C4018 et montre comment le corriger :

```cpp
// C4018.cpp
// compile with: cl /EHsc /W4 C4018.cpp
int main() {
    unsigned int uc = 0;
    int c = 0;
    unsigned int c2 = c; // implicit conversion

    if (uc < c)           // C4018
        uc = 0;

    if (uc < unsigned(c)) // OK
        uc = 0;

    if (uc < c2)          // Also OK
       uc = 0;
}
```

## <a name="see-also"></a>Voir aussi

[Avertissement du compilateur (niveau 4) C4388](c4388.md)\
[Avertissement du compilateur (niveau 4) C4389](compiler-warning-level-4-c4389.md)
