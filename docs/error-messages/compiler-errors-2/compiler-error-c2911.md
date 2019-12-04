---
title: Erreur du compilateur C2911
ms.date: 11/04/2016
f1_keywords:
- C2911
helpviewer_keywords:
- C2911
ms.assetid: 83c7c01a-ab6a-4179-9fb0-289a9ec8d44e
ms.openlocfilehash: 59061ab8126e3ba45c0b456bb4428652cab8a7e9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761099"
---
# <a name="compiler-error-c2911"></a>Erreur du compilateur C2911

'member' : ne peut pas être déclaré ou défini dans la portée actuelle

Dans un espace de noms, une classe ou une fonction, vous ne pouvez définir qu’un membre du même espace de noms, de la même classe ou de la même fonction, ou encore un membre compris dans le même espace de noms, la même classe ou la même fonction.

L’exemple suivant génère l’erreur C2911 :

```cpp
// C2911.cpp
struct A;

namespace M {
   struct D;
}

namespace N {
   struct C;

   namespace O {
      struct B;
   }

   // in N
   struct ::A {};   // C2911  A is member of global NS
   struct O::B{};   // OK B is in O, O is inside of N
   struct C {};     // OK C is member of N
   struct M::D {};  // C2911 D is member of M, M not enclosed by N
}
```
