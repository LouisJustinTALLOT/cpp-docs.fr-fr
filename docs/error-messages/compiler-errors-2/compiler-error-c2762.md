---
title: Erreur du compilateur C2762
ms.date: 11/04/2016
f1_keywords:
- C2762
helpviewer_keywords:
- C2762
ms.assetid: 8b81a801-fd48-40a1-8bee-0748795b12e4
ms.openlocfilehash: 0cb05d0e111319ff135bdb48d51af6eb4a2f2353
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574068"
---
# <a name="compiler-error-c2762"></a>Erreur du compilateur C2762

'classe' : expression non valide comme argument template pour 'argument'

Lorsque vous utilisez [/Za](../../build/reference/za-ze-disable-language-extensions.md), le compilateur ne convertira pas un type intégral vers un autre pointeur.

L’exemple suivant génère l’erreur C2762 :

```
// C2762.cpp
// compile with: /Za
template<typename T, T *pT>
class X2 {};

void f2() {
   X2<int, 0> x21;   // C2762
   // try the following line instead
   // X2<int, static_cast<int *>(0)> x22;
}
```