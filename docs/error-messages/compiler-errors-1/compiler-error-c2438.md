---
title: Erreur du compilateur C2438
ms.date: 11/04/2016
f1_keywords:
- C2438
helpviewer_keywords:
- C2438
ms.assetid: 3a0ab3ba-d0e4-4d8f-971d-e503397cc827
ms.openlocfilehash: b2861090b5f7629c7f0cd94ea38a99e888909258
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630501"
---
# <a name="compiler-error-c2438"></a>Erreur du compilateur C2438

'identificateur' : Impossible d’initialiser les données de classes static via un constructeur

Un constructeur est utilisé pour initialiser un membre statique d’une classe. Les membres statiques doivent être initialisés dans une définition en dehors de la déclaration de classe.

L’exemple suivant génère l’erreur C2438 :

```
// C2438.cpp
struct X {
   X(int i) : j(i) {}   // C2438
   static int j;
};

int X::j;

int main() {
   X::j = 1;
}
```