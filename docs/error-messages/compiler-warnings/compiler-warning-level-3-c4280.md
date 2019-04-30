---
title: Avertissement du compilateur (niveau 3) C4280
ms.date: 11/04/2016
f1_keywords:
- C4280
helpviewer_keywords:
- C4280
ms.assetid: 153fb639-3ee1-4fee-baf9-71420abcf3f6
ms.openlocfilehash: 6a3daa9903cbf983ddc19538a154d9717a2f9f0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402136"
---
# <a name="compiler-warning-level-3-c4280"></a>Avertissement du compilateur (niveau 3) C4280

'operator ->' était auto-récurrent à travers le type 'type'

Votre code autorise de façon incorrecte **operator ->** s’appeler elle-même.

L’exemple suivant génère l’erreur C4280 :

```
// C4280.cpp
// compile with: /W3 /WX
struct A
{
   int z;
   A& operator ->();
};

void f(A y)
{
   int i = y->z; // C4280
}
```