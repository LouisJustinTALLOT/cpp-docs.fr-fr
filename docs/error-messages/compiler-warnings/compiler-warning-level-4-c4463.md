---
title: Compilateur avertissement (niveau 4) C4463
ms.date: 11/04/2016
f1_keywords:
- C4463
helpviewer_keywords:
- C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
ms.openlocfilehash: e125a532f87533958ec43ed5580665ad4108856b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474820"
---
# <a name="compiler-warning-level-4-c4463"></a>Compilateur avertissement (niveau 4) C4463

> dépassement de capacité ; affectation *valeur* au champ de bits qui peut contenir uniquement des valeurs à partir de *low_value* à *high_value*

Assigné *valeur* est en dehors de la plage de valeurs que le champ de bits peut contenir. Les types de champ de bits signés utilisent le poids de bits pour le signe, par conséquent, si *n* est la taille de champ de bits, la plage de champs de bits signés est -2<sup>n-1</sup> 2<sup>n-1</sup>-1, tandis que non signé champs de bits ont une plage de 0 à 2<sup>n</sup>-1.

## <a name="example"></a>Exemple

Cet exemple génère C4463, car elle tente d’assigner une valeur de 3 à un champ de bits de type `int` avec une taille de 2, qui a une plage comprise entre -2 à 1.

Pour résoudre ce problème, vous pouvez modifier la valeur assignée à un élément dans la plage autorisée. Si le champ de bits est destiné à contenir des valeurs non signées dans la plage de 0 à 3, vous pouvez modifier le type de déclaration pour `unsigned`. Si le champ est destiné à contenir des valeurs dans le -4 à 3 de plage, vous pouvez modifier la taille de champ de bits à 3.

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
