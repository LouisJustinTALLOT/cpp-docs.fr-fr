---
title: Erreur du compilateur C2550
ms.date: 11/04/2016
f1_keywords:
- C2550
helpviewer_keywords:
- C2550
ms.assetid: 3293f53e-ee66-4035-920d-34e115c3a24c
ms.openlocfilehash: 29e907e682e0caae86569fe8bd7c101b3e0b14a3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740817"
---
# <a name="compiler-error-c2550"></a>Erreur du compilateur C2550

'identificateur' : les listes d’initialiseurs de constructeur ne sont autorisées que sur les définitions de constructeur

Une liste d’initialiseurs de classe de base est utilisée sur la définition d’une fonction qui n’est pas un constructeur.

L’exemple suivant génère l’C2550 :

```cpp
// C2550.cpp
// compile with: /c
class C {
public:
   C();
};

class D : public C {
public:
   D();
   void func();
};

void D::func() : C() {}  // C2550
D::D() : C() {}   // OK
```
