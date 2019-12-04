---
title: Erreur du compilateur C3351
ms.date: 11/04/2016
f1_keywords:
- C3351
helpviewer_keywords:
- C3351
ms.assetid: c021bbbe-1067-4f51-af4f-940d2b792eb5
ms.openlocfilehash: d93d6b08268aa8d6a7a7ad2e2086f4799417bbb4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737463"
---
# <a name="compiler-error-c3351"></a>Erreur du compilateur C3351

'object' : constructeur délégué : le second argument doit être l’adresse d’une fonction globale ou d’une fonction membre statique

Le compilateur attend l’adresse d’une fonction déclarée `static`.

L’exemple suivant génère l’erreur C3351 :

```cpp
// C3351a.cpp
// compile with: /clr
delegate int D(int, int);

ref class C {
public:
   int mf(int, int) {
      return 1;
   }

   static int mf2(int, int) {
      return 1;
   }
};

int main() {
   System::Delegate ^pD = gcnew D(nullptr, &C::mf);   // C3351
   System::Delegate ^pD2 = gcnew D(&C::mf2);
}
```
