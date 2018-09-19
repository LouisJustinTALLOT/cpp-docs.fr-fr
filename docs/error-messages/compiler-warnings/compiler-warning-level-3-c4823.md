---
title: Compilateur avertissement (niveau 3) C4823 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4823
dev_langs:
- C++
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c3a6f24a32267f221dbc37e242bae48c0056af5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044650"
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
