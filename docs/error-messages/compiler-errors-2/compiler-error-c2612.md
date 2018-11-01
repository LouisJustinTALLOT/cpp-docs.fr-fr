---
title: Erreur du compilateur C2612
ms.date: 11/04/2016
f1_keywords:
- C2612
helpviewer_keywords:
- C2612
ms.assetid: 6faacfd6-4455-41a2-808e-0f6799f84d6d
ms.openlocfilehash: b2d4888c1be39c4f48f0ca674426c7af612b9bb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612158"
---
# <a name="compiler-error-c2612"></a>Erreur du compilateur C2612

'char' non conforme dans une liste d’initialiseurs de base/membre de fin

Un caractère apparaît après la dernière base ou membres dans une liste d’initialiseurs.

L’exemple suivant génère l’erreur C2612 :

```
// C2612.cpp
class A {
public:
   int i;
   A( int ia ) : i( ia ) + {};   // C2612
};
```