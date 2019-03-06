---
title: Fichiers de définition de module (.Def)
ms.date: 11/04/2016
helpviewer_keywords:
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
ms.openlocfilehash: 041894fa88527061d90399540bc29762bff66f81
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424533"
---
# <a name="module-definition-def-files"></a>Fichiers de définition de module (.Def)

Les fichiers de définition de module (.def) fournissent à l’éditeur de liens avec des informations sur les exportations, attributs et d’autres informations sur le programme à lier. Un fichier .def est particulièrement utile lors de la création d’une DLL. Étant donné la [les options de l’éditeur de liens](../../build/reference/linker-options.md) qui peut être utilisé au lieu des instructions de définition de module, fichiers .def ne sont généralement pas nécessaires. Vous pouvez également utiliser [__declspec (dllexport)](../../build/exporting-from-a-dll-using-declspec-dllexport.md) comme un moyen de spécifier des fonctions exportées.

Vous pouvez appeler un fichier .def pendant la phase de l’éditeur de liens avec la [/DEF (spécifier un fichier de définition de Module)](../../build/reference/def-specify-module-definition-file.md) option de l’éditeur de liens.

Si vous générez un fichier .exe qui ne possède aucune exportation, à l’aide d’un fichier .def rendra votre sortie plus lent et plus volumineux du chargement de fichiers.

Pour obtenir un exemple, consultez [exportation à partir d’une DLL à l’aide de fichiers DEF](../../build/exporting-from-a-dll-using-def-files.md).

Consultez les sections suivantes pour plus d’informations :

- [Règles s’appliquant aux instructions de définition de module](../../build/reference/rules-for-module-definition-statements.md)

- [EXPORTS](../../build/reference/exports.md)

- [HEAPSIZE](../../build/reference/heapsize.md)

- [LIBRARY](../../build/reference/library.md)

- [NOM](../../build/reference/name-c-cpp.md)

- [SECTIONS](../../build/reference/sections-c-cpp.md)

- [STACKSIZE](../../build/reference/stacksize.md)

- [STUB](../../build/reference/stub.md)

- [VERSION](../../build/reference/version-c-cpp.md)

- [Mots réservés](../../build/reference/reserved-words.md)

## <a name="see-also"></a>Voir aussi

[Référence de la génération C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)
