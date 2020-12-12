---
description: 'En savoir plus sur : erreur du compilateur C3470'
title: Erreur du compilateur C3470
ms.date: 11/04/2016
f1_keywords:
- C3470
helpviewer_keywords:
- C3470
ms.assetid: 170c7a9d-214d-41b1-8f15-d4a4fc38aaa5
ms.openlocfilehash: 1b8310a8bf7f4d69590baeebfc9e49ec01ad9d05
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168434"
---
# <a name="compiler-error-c3470"></a>Erreur du compilateur C3470

'type' : une classe ne peut pas avoir à la fois un indexeur (propriété indexée par défaut) et operator[]

Un type ne peut pas définir à la fois un indexeur par défaut et un operator[].

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3470.

```cpp
// C3470.cpp
// compile with: /clr
using namespace System;

ref class R {
public:
   property int default[int] {
      int get(int i) {
         return i+1;
      }
   }

   int operator[](String^ s) { return Convert::ToInt32(s); }   // C3470
};

int main() {
   R ^ r = gcnew R;
   // return r[9] + r["32"] - 42;
}
```
