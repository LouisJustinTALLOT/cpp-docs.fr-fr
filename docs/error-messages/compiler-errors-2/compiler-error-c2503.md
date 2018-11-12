---
title: Erreur du compilateur C2503
ms.date: 11/04/2016
f1_keywords:
- C2503
helpviewer_keywords:
- C2503
ms.assetid: da86cc89-fd04-400b-aa8d-a5ffaf7e3918
ms.openlocfilehash: c481a27f19a92f47a19f0cfaa7b59cd509bb3c15
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660809"
---
# <a name="compiler-error-c2503"></a>Erreur du compilateur C2503

'class' : les classes de base ne peut pas contenir de tableaux de taille zéro

Une classe de base ou une structure contient un tableau de taille zéro. Un tableau dans une classe doit avoir au moins un élément.

L’exemple suivant génère l’erreur C2503 :

```
// C2503.cpp
// compile with: /c
class A {
   public:
   int array [];
};

class B : A {};    // C2503

class C {
public:
   int array [10];
};

class D : C {};
```