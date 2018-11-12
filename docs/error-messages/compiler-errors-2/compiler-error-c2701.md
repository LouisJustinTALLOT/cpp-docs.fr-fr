---
title: Erreur du compilateur C2701
ms.date: 11/04/2016
f1_keywords:
- C2701
helpviewer_keywords:
- C2701
ms.assetid: 31cf2ab7-ced9-4f75-aa51-e169e20407fb
ms.openlocfilehash: b16ddb16d98a81e53b29ff51e41d19073200a2e5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469444"
---
# <a name="compiler-error-c2701"></a>Erreur du compilateur C2701

'fonction' : un modèle de fonction ne peut pas être une fonction friend d’une classe locale

Une classe locale ne peut pas avoir une fonction de modèle comme une fonction friend.

L’exemple suivant génère l’erreur C2701 :

```
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