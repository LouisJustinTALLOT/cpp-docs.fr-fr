---
description: 'En savoir plus sur : erreur du compilateur C2583'
title: Erreur du compilateur C2583
ms.date: 11/04/2016
f1_keywords:
- C2583
helpviewer_keywords:
- C2583
ms.assetid: b1c952dc-872c-47e4-9fc8-4dd72bcee6f9
ms.openlocfilehash: 067e65f6085d033ca8d7372ee5e4d169e1b411dd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177690"
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
