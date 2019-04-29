---
title: Erreur du compilateur C2534
ms.date: 11/04/2016
f1_keywords:
- C2534
helpviewer_keywords:
- C2534
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
ms.openlocfilehash: e684804ea31b16f31c82e244cb4f9a6aaf2d08c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386965"
---
# <a name="compiler-error-c2534"></a>Erreur du compilateur C2534

'identificateur' : constructeur ne peut pas retourner une valeur

Un constructeur ne peut pas retourner une valeur ou avoir un type de retour (pas même un `void` type de retour).

Cette erreur peut être résolue en supprimant la `return` instruction à partir de la définition du constructeur.

L’exemple suivant génère l’erreur C2534 :

```
// C2534.cpp
class A {
public:
   int i;
   A() { return i; }   // C2534
};
```