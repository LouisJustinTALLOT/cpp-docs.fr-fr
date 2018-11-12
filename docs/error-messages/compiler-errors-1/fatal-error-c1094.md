---
title: Erreur irrécupérable C1094
ms.date: 11/04/2016
f1_keywords:
- C1094
helpviewer_keywords:
- C1094
ms.assetid: 9e1193b2-cb95-44f9-bf6f-019e0d41dd97
ms.openlocfilehash: 23891a783a018f6d84ea820af98992f61632984c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469652"
---
# <a name="fatal-error-c1094"></a>Erreur irrécupérable C1094

'-Zmval1' : option de ligne de commande est cohérente avec la valeur utilisée pour générer l’en-tête précompilé ('-Zmval2')

La valeur est passée à [/Yc](../../build/reference/yc-create-precompiled-header-file.md) doit être la même valeur que celle qui est passée à [/Yu](../../build/reference/yu-use-precompiled-header-file.md) (**/Zm** valeurs doivent être identiques dans toutes les compilations qui utilisent ou créer les mêmes précompilé fichier d’en-tête).

L’exemple suivant génère l’erreur C1094 :

```
// C1094.h
int func1();
```

Puis,

```
// C1094.cpp
// compile with: /Yc"C1094.h" /Zm200
int u;
int main() {
   int sd = 32;
}
#include "C1094.h"
```

Puis,

```
// C1094b.cpp
// compile with: /Yu"C1094.h" /Zm300 /c
#include "C1094.h"   // C1094 compile with /Zm200
void Test() {}
```