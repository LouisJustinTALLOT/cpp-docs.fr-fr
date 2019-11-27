---
title: Avertissement du compilateur (niveau 3) C4823
ms.date: 11/04/2016
f1_keywords:
- C4823
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
ms.openlocfilehash: a96877252b0b7699f5e4033f8e695f4d9016a6c9
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541264"
---
# <a name="compiler-warning-level-3-c4823"></a>Avertissement du compilateur (niveau 3) C4823

'fonction' : utilise des pointeurs épingle mais les sémantiques de déroulement ne sont pas activées. Envisagez d’utiliser/EHa

Pour détacher un objet sur le tas managé pointé par un pointeur épingle déclaré dans une portée de bloc, le compilateur simule le comportement des destructeurs de classes locales, « prétendant » le pointeur épingle a un destructeur qui annule le pointeur. Pour activer un appel à un destructeur après la levée d’une exception, vous devez activer le déroulement de l’objet, ce que vous pouvez faire à l’aide de [/EHsc](../../build/reference/eh-exception-handling-model.md).

Vous pouvez également désépingler manuellement l’objet et ignorer l’avertissement.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4823.

```cpp
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
