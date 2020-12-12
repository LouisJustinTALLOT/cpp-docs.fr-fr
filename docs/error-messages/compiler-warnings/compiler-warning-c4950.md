---
description: 'En savoir plus sur : avertissement du compilateur C4950'
title: Avertissement du compilateur C4950
ms.date: 11/04/2016
f1_keywords:
- C4950
helpviewer_keywords:
- C4950
ms.assetid: 50226a5c-c664-4d09-ac59-e9e874ca244f
ms.openlocfilehash: e1bb05501fcac6c836bfd4aa89f72807b625c292
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314878"
---
# <a name="compiler-warning-c4950"></a>Avertissement du compilateur C4950

'type_or_member' : marqué comme obsolète

Un membre ou un type a été marqué comme obsolète avec l' <xref:System.ObsoleteAttribute> attribut.

L’avertissement C4950 est toujours présenté comme une erreur. Vous pouvez désactiver cet avertissement à l’aide de la directive pragma [Warning](../../preprocessor/warning.md) ou de l’option du compilateur [/WD](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4950 :

```cpp
// C4950.cpp
// compile with: /clr
using namespace System;

// Any reference to Func3 should generate an error with message
[System::ObsoleteAttribute("Will be removed in next version", true)]
Int32 Func3(Int32 a, Int32 b) {
   return (a + b);
}

int main() {
   Int32 MyInt3 = ::Func3(2, 2);   // C4950
}
```
