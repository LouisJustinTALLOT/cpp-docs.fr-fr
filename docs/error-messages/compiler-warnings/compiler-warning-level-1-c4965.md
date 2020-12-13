---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4965'
title: Avertissement du compilateur (niveau 1) C4965
ms.date: 11/04/2016
f1_keywords:
- C4965
helpviewer_keywords:
- C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
ms.openlocfilehash: a3e20fa7007daac6f9a1c6f4761e222d5ab1e86c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344274"
---
# <a name="compiler-warning-level-1-c4965"></a>Avertissement du compilateur (niveau 1) C4965

zone implicite de l’entier 0 ; utiliser nullptr ou cast explicite

Visual C++ intègre une conversion boxing implicite des types valeur. Une instruction qui a entraîné une assignation null à l’aide de Extensions managées pour C++ devient maintenant une assignation à un int boxed.

Pour plus d'informations, consultez [Boxing](../../extensions/boxing-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4965.

```cpp
// C4965.cpp
// compile with: /clr /W1
int main() {
   System::Object ^o = 0;   // C4965

   // the previous line is the same as the following line
   // using Managed Extensions for C++
   // System::Object *o = __box(0);

   // OK
   System::Object ^o2 = nullptr;
   System::Object ^o3 = safe_cast<System::Object^>(0);
}
```
