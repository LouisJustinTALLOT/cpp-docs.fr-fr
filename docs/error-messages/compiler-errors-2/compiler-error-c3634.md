---
description: 'En savoir plus sur : erreur du compilateur C3634'
title: Erreur du compilateur C3634
ms.date: 11/04/2016
f1_keywords:
- C3634
helpviewer_keywords:
- C3634
ms.assetid: fd09f10c-f863-483b-9756-71c16b760b02
ms.openlocfilehash: 21407af8a86a3f82331d0f2a1d424457d8bee833
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239244"
---
# <a name="compiler-error-c3634"></a>Erreur du compilateur C3634

'fonction' : impossible de définir une méthode abstraite d’un managé ou d’un WinRTclass

Une méthode abstraite peut être déclarée dans une classe managée ou WinRT, mais elle ne peut pas être définie.

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C3634 :

```cpp
// C3634.cpp
// compile with: /clr
ref class C {
   virtual void f() = 0;
};

void C::f() {   // C3634 - don't define managed class' pure virtual method
}
```
