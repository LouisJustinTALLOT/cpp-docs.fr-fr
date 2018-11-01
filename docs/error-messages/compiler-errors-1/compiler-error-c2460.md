---
title: Erreur du compilateur C2460
ms.date: 11/04/2016
f1_keywords:
- C2460
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
ms.openlocfilehash: 414b6e53cf1610a55db984a1127bfc884102494f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589590"
---
# <a name="compiler-error-c2460"></a>Erreur du compilateur C2460

'identificateur1' : utilise 'identificateur2', qui est défini

Une classe ou structure (`identifier2`) est déclaré en tant que membre de lui-même (`identifier1`). Les définitions des classes et des structures récursives ne sont pas autorisées.

L’exemple suivant génère l’erreur C2460 :

```
// C2460.cpp
class C {
   C aC;    // C2460
};
```

Au lieu de cela, utilisez une référence de pointeur de la classe.

```
// C2460.cpp
class C {
   C * aC;    // OK
};
```