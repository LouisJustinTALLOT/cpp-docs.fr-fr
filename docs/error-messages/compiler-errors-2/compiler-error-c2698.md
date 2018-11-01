---
title: Erreur du compilateur C2698
ms.date: 11/04/2016
f1_keywords:
- C2698
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
ms.openlocfilehash: f643b7d8c035b4d1d7d8806feb5b121cf76d7796
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651906"
---
# <a name="compiler-error-c2698"></a>Erreur du compilateur C2698

la déclaration using pour ' déclaration 1' ne peuvent pas coexister avec la déclaration using existante pour ' déclaration 2'

Une fois que vous avez un [à l’aide de la déclaration](../../cpp/using-declaration.md) pour un membre de données, à l’aide de n’importe quel déclaration dans la même portée qui utilise le même nom n’est pas autorisée, car seules les fonctions peuvent être surchargées.

L’exemple suivant génère C2698 :

```
// C2698.cpp
struct A {
   int x;
};

struct B {
   int x;
};

struct C : A, B {
   using A::x;
   using B::x;   // C2698
}
```