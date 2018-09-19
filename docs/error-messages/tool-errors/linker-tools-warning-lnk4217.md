---
title: Avertissement LNK4217 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4217
dev_langs:
- C++
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c650eddd8078419f63df48cc91705d2e86eb5c8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067975"
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