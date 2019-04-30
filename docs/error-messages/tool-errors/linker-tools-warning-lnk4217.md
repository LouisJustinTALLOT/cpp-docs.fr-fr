---
title: Avertissement des outils Éditeur de liens LNK4217
ms.date: 04/15/2019
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: f1ea3cd0a8770571ae5c55d29a901c134311550f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410224"
---
# <a name="linker-tools-warning-lnk4217"></a>Avertissement des outils Éditeur de liens LNK4217

> symbole '*symbole*'définie dans'*filename_1.obj*'est importé par'*filename_2.obj*« dans la fonction'*fonction*'

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) a été spécifié pour un symbole, même si le symbole est défini dans un fichier objet dans la même image. Supprimer le `__declspec(dllimport)` modificateur pour résoudre cet avertissement.

## <a name="remarks"></a>Notes

*symbole* est le nom du symbole qui est défini dans l’image. *fonction* est la fonction qui importe le symbole.

Cet avertissement n’apparaît pas quand vous compilez à l’aide de la [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) option.

LNK4217 peut également se produire si vous tentez de relier deux modules, quand au lieu de cela, vous devez compiler le deuxième module avec la bibliothèque d’importation du premier module.

```cpp
// LNK4217.cpp
// compile with: /LD
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

Puis,

```cpp
// LNK4217b.cpp
// compile with: /c
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

Toute tentative lier ces deux modules entraîne de LNK4217. Compilez le deuxième exemple avec la bibliothèque d’importation du premier exemple à résoudre.

## <a name="see-also"></a>Voir aussi

[Outils de l’éditeur de liens LNK4049 d’avertissement](linker-tools-warning-lnk4049.md) \
[Avertissement LNK4286 des outils de l’éditeur de liens](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)