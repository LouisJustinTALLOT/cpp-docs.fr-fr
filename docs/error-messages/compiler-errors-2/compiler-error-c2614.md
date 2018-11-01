---
title: Erreur du compilateur C2614
ms.date: 11/04/2016
f1_keywords:
- C2614
helpviewer_keywords:
- C2614
ms.assetid: a550c1d5-8718-4e17-a888-b2619e00fe11
ms.openlocfilehash: 71f0fe3211ce253bcf30347658692651e84ab608
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463594"
---
# <a name="compiler-error-c2614"></a>Erreur du compilateur C2614

'classe1' : l’initialisation de membre non conforme : 'classe2' n’est pas une base ni un membre

Seuls les membres ou les classes de base peuvent apparaître dans la liste d’initialisation pour une classe ou structure.

## <a name="example"></a>Exemple

L’exemple suivant génère C2614.

```
// C2614.cpp
// compile with: /c
struct A {
   int i;
   A( int ia ) : B( i ) {};   // C2614 B is not a member of A
};

struct A2 {
   int B;
   int i;
   A2( int ia ) : B( i ) {};   // OK
};
```