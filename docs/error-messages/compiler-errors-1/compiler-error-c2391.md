---
title: Erreur du compilateur C2391
ms.date: 11/04/2016
f1_keywords:
- C2391
helpviewer_keywords:
- C2391
ms.assetid: 63a9c6b9-03cc-4517-885c-bdcd048643b3
ms.openlocfilehash: 7683ad1580454bd7edb1fc08e5bd110a3e5c36c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491486"
---
# <a name="compiler-error-c2391"></a>Erreur du compilateur C2391

'identificateur' : 'friend' ne peut pas être utilisé lors de la définition de type

Le `friend` déclaration inclut une déclaration de classe complète. Un `friend` déclaration peut spécifier une fonction membre ou un spécificateur de type élaboré, mais pas une déclaration de classe complète.

L’exemple suivant génère l’erreur C2326 :

```
// C2391.cpp
// compile with: /c
class D {
   void func( int );
};

class A {
   friend class B { int i; };   // C2391

   // OK
   friend class C;
   friend void D::func(int);
};
```