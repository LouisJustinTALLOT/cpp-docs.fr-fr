---
title: Avertissement du compilateur (niveau 3) C4823
ms.date: 11/04/2016
f1_keywords:
- C4823
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
ms.openlocfilehash: 28d490c341c4d14c2e6c03e13007b5a8be423622
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625905"
---
# <a name="compiler-warning-level-3-c4823"></a>Avertissement du compilateur (niveau 3) C4823

'fonction' : utilise des pointeurs épingle mais déroulement sémantique n’est pas activée. Utilisez /EHa

Pour supprimer un objet sur le tas managé vers lequel pointé un pointeur épingle déclaré dans une portée de bloc, le compilateur simule le comportement de destructeurs de classes locales, « prétendant » le pointeur épingle possède un destructeur qui annule le pointeur. Pour activer un appel à un destructeur après la levée d’une exception, vous devez activer le déroulement de l’objet, ce que vous pouvez faire à l’aide de [/EHsc](../../build/reference/eh-exception-handling-model.md).

Vous pouvez manuellement supprimer l’objet et ignorer l’avertissement.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4823.

```
// C4823.cpp
// compile with: /clr /W3 /EHa-
using namespace System;

ref struct G {
   int m;
};

void f(G ^ pG) {
   try {
      pin_ptr<int> p = &pG->m;
      // manually unpin, ignore warning
      // p = nullptr;
      throw gcnew Exception;
   }
   catch(Exception ^) {}
}   // C4823 warning

int main() {
   f( gcnew G );
}
```
