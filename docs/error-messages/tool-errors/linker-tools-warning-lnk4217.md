---
title: Avertissement des outils Éditeur de liens LNK4217
ms.date: 07/23/2019
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: 1301dd53f71c616d7b7af346923a54c42903c9fd
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450861"
---
# <a name="linker-tools-warning-lnk4217"></a>Avertissement des outils Éditeur de liens LNK4217

> le symbole «*symbol*» défini dans «*filename_1. obj*» est importé par «*filename_2. obj*» dans la fonction «*Function*»

[_ _ declspec (dllimport)](../../cpp/dllexport-dllimport.md) a été spécifié pour un symbole même si le symbole est défini dans un fichier objet dans la même image. Supprimez `__declspec(dllimport)` le modificateur pour résoudre cet avertissement.

## <a name="remarks"></a>Notes

*symbol* est le nom du symbole qui est défini dans l’image. la *fonction est la* fonction qui importe le symbole.

Cet avertissement n’apparaît pas quand vous compilez à l’aide de l’option [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) .

LNK4217 peut également se produire si vous tentez de lier deux modules ensemble. au lieu de cela, vous devez compiler le deuxième module avec la bibliothèque d’importation du premier module.

```cpp
// main.cpp
__declspec(dllimport) void func();

int main()
{
    func();
    return 0;
}

```

Puis,

```cpp
// tt.cpp
// compile with: /c
void func() {}
```

Si vous tentez de compiler ces deux modules comme indiqué ci-dessous, LNK4217:

```cmd
cl.exe /c main.cpp tt.cpp
link.exe main.obj tt.obj
```

Pour corriger l’erreur, après avoir compilé les deux fichiers, transmettez TT. obj à lib. exe pour créer un fichier. lib, puis liez main. obj à TT. lib comme indiqué ici:

```cmd
cl.exe /c main.cpp tt.cpp
lib.exe tt.obj /export:func /def
link.exe main.obj tt.lib
```

## <a name="see-also"></a>Voir aussi

[Avertissement des outils Éditeur de liens LNK4049](linker-tools-warning-lnk4049.md) \
[Avertissement des outils Éditeur de liens LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)