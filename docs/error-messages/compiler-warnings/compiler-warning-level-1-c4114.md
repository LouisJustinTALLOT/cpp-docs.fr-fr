---
title: Compilateur avertissement (niveau 1) C4114
ms.date: 11/04/2016
f1_keywords:
- C4114
helpviewer_keywords:
- C4114
ms.assetid: 3983e1c6-e8bb-46dc-8894-e1827db48797
ms.openlocfilehash: 41e951e7c4a8b23ddbec14c5421f66702e70c937
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450971"
---
# <a name="compiler-warning-level-1-c4114"></a>Compilateur avertissement (niveau 1) C4114

même qualificateur de type utilisé plusieurs fois

Une définition ou déclaration de type utilise un qualificateur de type (**const**, **volatile**, **signé**, ou **non signé**) plusieurs fois. Cela provoque un avertissement avec les extensions Microsoft (/Ze) et une erreur sous compatibilité ANSI (/Za).

L’exemple suivant génère l’erreur C4114 :

```
// C4114.cpp
// compile with: /W1 /c
volatile volatile int i;   // C4114
```

L’exemple suivant génère l’erreur C4114 :

```
// C4114_b.cpp
// compile with: /W1 /c
static const int const * ii;   // C4114
static const int * const iii;   // OK
```
