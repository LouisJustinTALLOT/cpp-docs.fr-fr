---
title: Erreur du compilateur C2583
ms.date: 11/04/2016
f1_keywords:
- C2583
helpviewer_keywords:
- C2583
ms.assetid: b1c952dc-872c-47e4-9fc8-4dd72bcee6f9
ms.openlocfilehash: b78b9dd69b701e1a66646234d4603973657e90c6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366392"
---
# <a name="compiler-error-c2583"></a>Erreur du compilateur C2583

'identificateur' : ' const/volatile' pointeur 'this' est non conforme pour les constructeurs/destructeurs

Un constructeur ou un destructeur est déclaré `const` ou `volatile`. Cette opération n’est pas autorisée.

L’exemple suivant génère l’erreur C2583 :

```
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