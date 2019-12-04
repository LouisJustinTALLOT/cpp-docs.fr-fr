---
title: Erreur du compilateur C2784
ms.date: 11/04/2016
f1_keywords:
- C2784
helpviewer_keywords:
- C2784
ms.assetid: 3d761fe2-881c-48bd-afae-e2e714e20473
ms.openlocfilehash: 1ff91135f6a6207921aa1f83d42ebd1689e711a1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739634"
---
# <a name="compiler-error-c2784"></a>Erreur du compilateur C2784

’déclaration’ : impossible de déduire l’argument template pour ’type’ à partir de ’type’

Le compilateur ne peut pas déterminer un argument template à partir des arguments de fonction fournis.

L'exemple suivant génère l'erreur C2784 et montre comment la corriger :

```cpp
// C2784.cpp
template<class T> class X {};
template<class T> void f(X<T>) {}

int main() {
   X<int> x;
   f(1);   // C2784

   // To fix it, try the following line instead
   f(x);
}
```
