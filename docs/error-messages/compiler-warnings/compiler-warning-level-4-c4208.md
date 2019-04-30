---
title: Avertissement du compilateur (niveau 4) C4208
ms.date: 11/04/2016
f1_keywords:
- C4208
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
ms.openlocfilehash: 11c6b1ad50c44ac4ad2a9d014e57efef097d9d8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401174"
---
# <a name="compiler-warning-level-4-c4208"></a>Avertissement du compilateur (niveau 4) C4208

extension non standard utilisée : delete [exp] - exp analysée mais ignorée

Avec les extensions Microsoft (/Ze), vous pouvez supprimer un tableau en utilisant une valeur entre accolades avec le [opérateur delete](../../cpp/delete-operator-cpp.md). La valeur est ignorée.

```
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

Ces valeurs ne sont pas valides sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).