---
title: Erreur du compilateur C2701
ms.date: 11/04/2016
f1_keywords:
- C2701
helpviewer_keywords:
- C2701
ms.assetid: 31cf2ab7-ced9-4f75-aa51-e169e20407fb
ms.openlocfilehash: aabb47d3e0e2f494b19205626861dea43ca87033
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758331"
---
# <a name="compiler-error-c2701"></a>Erreur du compilateur C2701

'fonction' : un modèle de fonction ne peut pas être friend d’une classe locale

Une classe locale ne peut pas avoir une fonction de modèle comme fonction friend.

L’exemple suivant génère l’C2701 :

```cpp
// C2701.cpp
// compile with: /c
template<typename T>   // OK
void f1(const T &);

void MyFunction() {
   class MyClass {
      template<typename T> friend void f2(const T &);   // C2701
   };
}
```
