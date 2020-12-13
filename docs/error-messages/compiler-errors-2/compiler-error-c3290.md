---
description: 'En savoir plus sur : erreur du compilateur C3290'
title: Erreur du compilateur C3290
ms.date: 11/04/2016
f1_keywords:
- C3290
helpviewer_keywords:
- C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
ms.openlocfilehash: 68c0e79c233f7fbd416f6bdbe42cc555c04731fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337425"
---
# <a name="compiler-error-c3290"></a>Erreur du compilateur C3290

'type' : une propriété triviale ne peut pas avoir de type référence

Une propriété n’a pas été correctement déclarée. Quand vous déclarez une propriété triviale, le compilateur crée une variable que la propriété va mettre à jour et il n’est pas possible d’avoir une variable de référence de suivi dans une classe.

Pour plus d’informations, consultez [opérateur de référence](../../extensions/tracking-reference-operator-cpp-component-extensions.md) de [propriété](../../extensions/property-cpp-component-extensions.md) et de suivi.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3290.

```cpp
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
