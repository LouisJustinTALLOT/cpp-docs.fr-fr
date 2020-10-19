---
title: Avertissement du compilateur (niveau 4) C4389
description: Avertissement du compilateur Microsoft C/C++ C4389, ses causes et sa résolution.
ms.date: 10/16/2020
f1_keywords:
- c4389
helpviewer_keywords:
- C4389
ms.openlocfilehash: b06b013151ed12b4f66bb23a7e862992d05e6b30
ms.sourcegitcommit: f19f02f217b80804ab321d463c76ce6f681abcc6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92176270"
---
# <a name="compiler-warning-level-4-c4389"></a>Avertissement du compilateur (niveau 4) C4389

> '*égalité-opérateur*' : incompatibilité signed/unsigned

Une **`==`** **`!=`** opération ou impliquée **`signed`** et des **`unsigned`** variables. Cela peut entraîner une perte de données.

## <a name="remarks"></a>Notes

Une façon de résoudre cet avertissement est si vous effectuez un cast de l’un des deux types lorsque vous comparez **`signed`** des **`unsigned`** types et.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4389 :

```cpp
// C4389.cpp
// compile with: cl /EHsc /W4 C4389.cpp

int main()
{
   int a = 9;
   unsigned int b = 10;
   int result = 0;

   if (a == b)   // C4389
      result = 1;
   else
      result = 2;

   if (unsigned(a) == b) // OK
      result = 3;
   else
      result = 4;

   return result;
}
```

## <a name="see-also"></a>Voir aussi

[Avertissement du compilateur C4018](compiler-warning-level-3-c4018.md)\
[Avertissement du compilateur (niveau 4) C4388](c4388.md)
