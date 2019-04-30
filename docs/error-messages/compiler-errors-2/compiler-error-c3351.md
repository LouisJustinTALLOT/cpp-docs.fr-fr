---
title: Erreur du compilateur C3351
ms.date: 11/04/2016
f1_keywords:
- C3351
helpviewer_keywords:
- C3351
ms.assetid: c021bbbe-1067-4f51-af4f-940d2b792eb5
ms.openlocfilehash: 3935acc645403efcd579a80340ebb9794bc1052a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402656"
---
# <a name="compiler-error-c3351"></a>Erreur du compilateur C3351

'object' : constructeur délégué : le second argument doit être l’adresse d’une fonction globale ou d’une fonction membre statique

Le compilateur attend l’adresse d’une fonction déclarée `static`.

L’exemple suivant génère l’erreur C3351 :

```
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
