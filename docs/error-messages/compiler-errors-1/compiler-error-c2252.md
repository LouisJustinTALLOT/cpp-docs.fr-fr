---
title: Erreur du compilateur C2252
ms.date: 11/04/2016
f1_keywords:
- C2252
helpviewer_keywords:
- C2252
ms.assetid: fee74ab9-1997-4615-82fe-e6d1fe3aacd9
ms.openlocfilehash: 1fe64292ce6463b3b628367ef0052208e74b24d3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758877"
---
# <a name="compiler-error-c2252"></a>Erreur du compilateur C2252

Impossible d’instancier explicitement le modèle dans la portée actuelle

Le compilateur a détecté un problème avec une instanciation explicite d’un modèle.  Par exemple, vous ne pouvez pas instancier explicitement un modèle dans une fonction.

L’exemple suivant génère l’C2252 :

```cpp
// C2252.cpp
class A {
public:
   template <class T>
   int getit(int i , T * it ) {
      return i;
   }
   template int A::getit<double>(int i, double * it);   // C2252
   // try the following line instead
   // template <> int A::getit<double>(int i, double * it);

};

int main() {
   // cannot explicitly instantiate in function
   template int A::getit<long>(int i, long * it);   // C2252
}
```
