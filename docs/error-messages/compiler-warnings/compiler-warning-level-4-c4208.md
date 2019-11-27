---
title: Avertissement du compilateur (niveau 4) C4208
ms.date: 11/04/2016
f1_keywords:
- C4208
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
ms.openlocfilehash: e15140bd2f0983bde64c89a054fd733d1ab902ac
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541865"
---
# <a name="compiler-warning-level-4-c4208"></a>Avertissement du compilateur (niveau 4) C4208

extension non standard utilisée : delete [exp]-exp évaluée mais ignorée

Avec les extensions Microsoft (/Ze), vous pouvez supprimer un tableau à l’aide d’une valeur entre crochets avec l' [opérateur delete](../../cpp/delete-operator-cpp.md). La valeur est ignorée.

```cpp
// C4208.cpp
// compile with: /W4
int main()
{
   int * MyArray = new int[18];
   delete [18] MyArray;      // C4208
   MyArray = new int[18];
   delete [] MyArray;        // ok
}
```

Ces valeurs ne sont pas valides sous compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).