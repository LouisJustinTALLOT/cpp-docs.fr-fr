---
title: Avertissement du compilateur (niveau 4) C4238
ms.date: 11/04/2016
f1_keywords:
- C4238
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
ms.openlocfilehash: c5ffa07b06f010d10edc14aa7576bb614aa9dd04
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471901"
---
# <a name="compiler-warning-level-4-c4238"></a>Avertissement du compilateur (niveau 4) C4238

extension non standard utilisée : classe rvalue utilisée comme lvalue

Pour assurer la compatibilité avec les versions précédentes de Visual C++, les extensions Microsoft (**/Ze**) vous permettent d’utiliser un type de classe comme rvalue dans un contexte qui implicitement ou explicitement prend son adresse. Dans certains cas, comme dans l’exemple ci-dessous, cela peut être dangereux.

## <a name="example"></a>Exemple

```
// C4238.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

C * pC = &C();   // C4238
```

Cette utilisation génère une erreur sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).