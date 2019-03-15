---
title: Fichiers de définition de module (.Def)
ms.date: 11/04/2016
helpviewer_keywords:
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
ms.openlocfilehash: 0047f24722644cd9a68bbbf827ced26ad085d4c1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812237"
---
# <a name="module-definition-def-files"></a>Fichiers de définition de module (.Def)

Les fichiers de définition de module (.def) fournissent à l’éditeur de liens avec des informations sur les exportations, attributs et d’autres informations sur le programme à lier. Un fichier .def est particulièrement utile lors de la création d’une DLL. Étant donné la [Options de l’éditeur de liens MSVC](linker-options.md) qui peut être utilisé au lieu des instructions de définition de module, fichiers .def ne sont généralement pas nécessaires. Vous pouvez également utiliser [__declspec (dllexport)](../exporting-from-a-dll-using-declspec-dllexport.md) comme un moyen de spécifier des fonctions exportées.

Vous pouvez appeler un fichier .def pendant la phase de l’éditeur de liens avec la [/DEF (spécifier un fichier de définition de Module)](def-specify-module-definition-file.md) option de l’éditeur de liens.

Si vous générez un fichier .exe qui ne possède aucune exportation, à l’aide d’un fichier .def rendra votre sortie plus lent et plus volumineux du chargement de fichiers.

Pour obtenir un exemple, consultez [exportation à partir d’une DLL à l’aide de fichiers DEF](../exporting-from-a-dll-using-def-files.md).

Consultez les sections suivantes pour plus d’informations :

- [Règles s’appliquant aux instructions de définition de module](rules-for-module-definition-statements.md)

- [EXPORTS](exports.md)

- [HEAPSIZE](heapsize.md)

- [LIBRARY](library.md)

- [NOM](name-c-cpp.md)

- [SECTIONS](sections-c-cpp.md)

- [STACKSIZE](stacksize.md)

- [STUB](stub.md)

- [VERSION](version-c-cpp.md)

- [Mots réservés](reserved-words.md)

## <a name="see-also"></a>Voir aussi

[Référence de la génération C/C++](c-cpp-building-reference.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
