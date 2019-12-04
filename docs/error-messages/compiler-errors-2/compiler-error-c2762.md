---
title: Erreur du compilateur C2762
ms.date: 11/04/2016
f1_keywords:
- C2762
helpviewer_keywords:
- C2762
ms.assetid: 8b81a801-fd48-40a1-8bee-0748795b12e4
ms.openlocfilehash: c2f325fc9266321f224429afd3c295141627ecd6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759852"
---
# <a name="compiler-error-c2762"></a>Erreur du compilateur C2762

'class' : expression non valide comme argument template pour’argument'

Lors de l’utilisation de [/za](../../build/reference/za-ze-disable-language-extensions.md), le compilateur ne convertit pas un intégral en pointeur.

L’exemple suivant génère l’C2762 :

```cpp
// C2762.cpp
// compile with: /Za
template<typename T, T *pT>
class X2 {};

void f2() {
   X2<int, 0> x21;   // C2762
   // try the following line instead
   // X2<int, static_cast<int *>(0)> x22;
}
```
