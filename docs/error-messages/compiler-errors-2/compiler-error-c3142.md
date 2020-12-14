---
description: 'En savoir plus sur : erreur du compilateur C3142'
title: Erreur du compilateur C3142
ms.date: 11/04/2016
f1_keywords:
- C3142
helpviewer_keywords:
- C3142
ms.assetid: 795137ad-d00a-4a9c-9665-0cd8bfb5da8b
ms.openlocfilehash: b03f6efbbf473493354742ef7654e5629b5e5fba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204041"
---
# <a name="compiler-error-c3142"></a>Erreur du compilateur C3142

'property_name' : vous ne pouvez pas prendre l’adresse d’une propriété

L’adresse d’une propriété n’est pas disponible pour le développeur.

L’exemple suivant génère l’C3142 :

```cpp
// C3142_2.cpp
// compile with: /clr
using namespace System;
ref class CSize {
private:
   property int Size {
      int get();
   }
};

int main() {
    &CSize::Size; // C3142
}
```
