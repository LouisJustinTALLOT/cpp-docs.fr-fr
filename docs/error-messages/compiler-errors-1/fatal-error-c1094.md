---
description: 'En savoir plus sur : erreur irrécupérable C1094'
title: Erreur irrécupérable C1094
ms.date: 11/04/2016
f1_keywords:
- C1094
helpviewer_keywords:
- C1094
ms.assetid: 9e1193b2-cb95-44f9-bf6f-019e0d41dd97
ms.openlocfilehash: af83c6fa80a6e1b115146ad05513539fea7d348c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145091"
---
# <a name="fatal-error-c1094"></a>Erreur irrécupérable C1094

'-Zmval1 ' : l’option de ligne de commande n’est pas cohérente avec la valeur utilisée pour générer l’en-tête précompilé ('-Zmval2 ')

La valeur passée à [/Yc](../../build/reference/yc-create-precompiled-header-file.md) doit être la même que celle passée à [/Yu](../../build/reference/yu-use-precompiled-header-file.md) (les valeurs **/ZM** doivent être identiques dans toutes les compilations qui utilisent ou créent le même fichier d’en-tête précompilé).

L’exemple suivant génère l’C1094 :

```
// C1094.h
int func1();
```

Puis,

```cpp
// C1094.cpp
// compile with: /Yc"C1094.h" /Zm200
int u;
int main() {
   int sd = 32;
}
#include "C1094.h"
```

Puis,

```cpp
// C1094b.cpp
// compile with: /Yu"C1094.h" /Zm300 /c
#include "C1094.h"   // C1094 compile with /Zm200
void Test() {}
```
