---
title: Avertissement des outils Éditeur de liens LNK4217
ms.date: 11/04/2016
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: 12766241832d39f0b47ed85036c0ebeb0447fc75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448046"
---
# <a name="linker-tools-warning-lnk4217"></a>Avertissement des outils Éditeur de liens LNK4217

symbole 'symbole' importé dans la fonction 'fonction' défini localement

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) a été spécifié pour un symbole, même si le symbole est défini localement. Supprimer le `__declspec` modificateur pour résoudre cet avertissement.

`symbol` est le nom du symbole qui est défini dans l’image. `function` est la fonction qui importe le symbole.

Cet avertissement n’apparaît pas lorsque vous compilez en utilisant l’option [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

LNK4217 peut également se produire si vous tentez de relier deux modules, quand au lieu de cela, vous devez compiler le deuxième module avec la bibliothèque d’importation du premier module.

```
// LNK4217.cpp
// compile with: /LD
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

Puis,

```
// LNK4217b.cpp
// compile with: /c
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

Tentative de liaison de ces deux modules donnera LNK4217, compilez le deuxième exemple avec la bibliothèque d’importation du premier exemple à résoudre.