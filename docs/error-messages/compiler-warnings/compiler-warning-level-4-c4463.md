---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4463'
title: Avertissement du compilateur (niveau 4) C4463
ms.date: 11/04/2016
f1_keywords:
- C4463
helpviewer_keywords:
- C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
ms.openlocfilehash: fe4ea13c50e16bf5b72f5753fa989970db3cadde
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251321"
---
# <a name="compiler-warning-level-4-c4463"></a>Avertissement du compilateur (niveau 4) C4463

> surcharge affectation d’une *valeur* à un champ de bits qui ne peut contenir que des valeurs de *low_value* à *HIGH_VALUE*

La *valeur* assignée est en dehors de la plage de valeurs que le champ de bits peut contenir. Les types de champ de bits signés utilisent le bit de poids fort pour le signe, donc si *n* est la taille du champ de bits, la plage des champs de bits signés est-2 <sup>n-1</sup> à 2 <sup>n-1</sup>-1, tandis que les champs de bits non signés ont une plage comprise entre 0 et 2 <sup>n</sup>-1.

## <a name="example"></a>Exemple

Cet exemple génère C4463, car il tente d’affecter une valeur de 3 à un champ de bits de type **`int`** avec une taille de 2, qui a une plage comprise entre-2 et 1.

Pour résoudre ce problème, vous pouvez remplacer la valeur affectée par une valeur comprise dans la plage autorisée. Si le champ de bits est destiné à contenir des valeurs non signées dans la plage comprise entre 0 et 3, vous pouvez modifier le type de déclaration en **`unsigned`** . Si le champ est destiné à contenir des valeurs comprises dans la plage-4 à 3, vous pouvez modifier la taille du champ de bits sur 3.

```cpp
// C4463_overflow.cpp
// compile with: cl /W4 /EHsc C4463_overflow.cpp
struct S {
    int x : 2; // int type treats high-order bit as sign
};

int main() {
    S s;
    s.x = 3; // warning C4463: overflow; assigning 3
    // to bit-field that can only hold values from -2 to 1
    // To fix, change assigned value to fit in range,
    // increase size of bitfield, and/or change base type
    // to unsigned.
}
```
