---
title: Erreur du compilateur C2391
ms.date: 11/04/2016
f1_keywords:
- C2391
helpviewer_keywords:
- C2391
ms.assetid: 63a9c6b9-03cc-4517-885c-bdcd048643b3
ms.openlocfilehash: f000287c5934a39d56342bce0f6c9ca2c69e2297
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212733"
---
# <a name="compiler-error-c2391"></a>Erreur du compilateur C2391

'identifier' : 'Friend’ne peut pas être utilisé lors de la définition de type

La **`friend`** déclaration comprend une déclaration de classe complète. Une **`friend`** déclaration peut spécifier une fonction membre ou un spécificateur de type élaboré, mais pas une déclaration de classe complète.

L’exemple suivant génère l’erreur C2326 :

```cpp
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
