---
title: Erreur du compilateur C3638
ms.date: 11/04/2016
f1_keywords:
- C3638
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
ms.openlocfilehash: 8b1ef7f4cb38653f0ccdfae5684eb2907a735af7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486888"
---
# <a name="compiler-error-c3638"></a>Erreur du compilateur C3638

'opérateur' : Impossible de redéfinir le boxing standard et les opérateurs de conversion unboxing

Le compilateur définit un opérateur de conversion pour chaque classe managée pour prendre en charge la conversion boxing implicite. Cet opérateur ne peut pas être redéfini.

Pour plus d’informations, consultez [Boxing implicite](../../windows/boxing-cpp-component-extensions.md).

L’exemple suivant génère l’erreur C3638 :

```
// C3638.cpp
// compile with: /clr
value struct V {
   V(){}
   static operator V^(V);   // C3638
};

int main() {
   V myV;
   V ^ pmyV = myV;   // operator supports implicit boxing
}
```