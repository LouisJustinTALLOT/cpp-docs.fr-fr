---
title: Erreur du compilateur C2042
ms.date: 11/04/2016
f1_keywords:
- C2042
helpviewer_keywords:
- C2042
ms.assetid: e111788f-41ce-405a-9824-a4c1c26059e6
ms.openlocfilehash: 3302b3a529ad8af054bb29bced66bc939abcc060
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643862"
---
# <a name="compiler-error-c2042"></a>Erreur du compilateur C2042

les mots clés signed/unsigned s'excluent mutuellement

Les mots clés `signed` et `unsigned` sont utilisés dans une même déclaration.

L’exemple suivant génère l’erreur C2042 :

```
// C2042.cpp
unsigned signed int i;   // C2042
```

Solution possible :

```
// C2042b.cpp
// compile with: /c
unsigned int i;
signed int ii;
```