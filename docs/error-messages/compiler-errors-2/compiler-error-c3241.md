---
title: Erreur du compilateur C3241
ms.date: 11/04/2016
f1_keywords:
- C3241
helpviewer_keywords:
- C3241
ms.assetid: 2ca14879-bba0-4a23-b22a-72cfff92d6a4
ms.openlocfilehash: 6eab22a8627b817b7a31e4bd34aad86d1f274615
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533430"
---
# <a name="compiler-error-c3241"></a>Erreur du compilateur C3241

'méthode' : cette méthode n’a pas été introduite par 'interface'

Lorsque vous substituez explicitement une fonction, la signature de fonction doit correspondre exactement à la déclaration de la fonction que vous substituez.

L’exemple suivant génère l’erreur C3241 :

```
// C3241.cpp
#pragma warning(disable:4199)

__interface IX12A {
   void mf();
};

__interface IX12B {
   void mf(int);
};

class CX12 : public IX12A, public IX12B { // C3241
   void IX12A::mf(int);
};
```