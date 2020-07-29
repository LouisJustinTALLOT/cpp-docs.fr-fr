---
title: Erreur du compilateur C2583
ms.date: 11/04/2016
f1_keywords:
- C2583
helpviewer_keywords:
- C2583
ms.assetid: b1c952dc-872c-47e4-9fc8-4dd72bcee6f9
ms.openlocfilehash: 0cb021dcba4d050afb943c03ba6b4dca053bcbb8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206846"
---
# <a name="compiler-error-c2583"></a>Erreur du compilateur C2583

'identificateur' : le pointeur’const/volatile' 'This’est illégal pour les constructeurs/destructeurs

Un constructeur ou un destructeur est déclaré **`const`** ou **`volatile`** . Cette opération n’est pas autorisée.

L’exemple suivant génère l’C2583 :

```cpp
// C2583.cpp
// compile with: /c
class A {
public:
   int i;
   A() const;   // C2583

   // try the following line instead
   // A();
};
```
