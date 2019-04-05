---
title: Erreur du compilateur C3290
ms.date: 11/04/2016
f1_keywords:
- C3290
helpviewer_keywords:
- C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
ms.openlocfilehash: f2a346354d8da7d78c5517b01b4438bfb8af50ad
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58774839"
---
# <a name="compiler-error-c3290"></a>Erreur du compilateur C3290

'type' : une propriété triviale ne peut pas avoir de type référence

Une propriété n’a pas été correctement déclarée. Quand vous déclarez une propriété triviale, le compilateur crée une variable que la propriété va mettre à jour et il n’est pas possible d’avoir une variable de référence de suivi dans une classe.

Consultez [propriété](../../extensions/property-cpp-component-extensions.md) et [opérateur de référence de suivi](../../extensions/tracking-reference-operator-cpp-component-extensions.md) pour plus d’informations.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3290.

```
// C3290.cpp
// compile with: /clr /c
ref struct R {};

ref struct X {
   R^ mr;

   property R % y;   // C3290
   property R ^ x;   // OK

   // OK
   property R% prop {
      R% get() {
         return *mr;
      }

      void set(R%) {}
   }
};

int main() {
   X x;
   R% xp = x.prop;
}
```