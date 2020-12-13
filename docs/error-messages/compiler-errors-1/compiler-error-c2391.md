---
description: 'En savoir plus sur : erreur du compilateur C2391'
title: Erreur du compilateur C2391
ms.date: 11/04/2016
f1_keywords:
- C2391
helpviewer_keywords:
- C2391
ms.assetid: 63a9c6b9-03cc-4517-885c-bdcd048643b3
ms.openlocfilehash: 3161cd6ade15817142cc24f38c61fd3e09eb8857
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337571"
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
