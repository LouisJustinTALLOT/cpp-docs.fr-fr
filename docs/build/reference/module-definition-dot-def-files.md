---
description: 'En savoir plus sur les éléments suivants : Module-Definition (. Fichiers def)'
title: Fichiers de définition de module (.Def)
ms.date: 11/04/2016
helpviewer_keywords:
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
ms.openlocfilehash: d52141a2917b2c82616597b2d070a84b96d1a653
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137811"
---
# <a name="module-definition-def-files"></a>Fichiers de définition de module (.Def)

Les fichiers de définition de module (. def) fournissent à l’éditeur de liens des informations sur les exportations, les attributs et d’autres informations sur le programme à lier. Un fichier. def est très utile lors de la génération d’une DLL. Comme il existe des options de l' [éditeur de liens MSVC](linker-options.md) qui peuvent être utilisées à la place des instructions de définition de module, les fichiers. def ne sont généralement pas nécessaires. Vous pouvez également utiliser [__declspec (dllexport)](../exporting-from-a-dll-using-declspec-dllexport.md) comme méthode pour spécifier des fonctions exportées.

Vous pouvez appeler un fichier. def pendant la phase de l’éditeur de liens avec l’option de l’éditeur de liens [/def (spécifier le fichier Module-Definition)](def-specify-module-definition-file.md) .

Si vous générez un fichier. exe qui n’a pas d’exportation, l’utilisation d’un fichier. def rendra votre fichier de sortie plus volumineux et plus lent.

Pour obtenir un exemple, consultez [exportation à partir d’une dll à l’aide de fichiers def](../exporting-from-a-dll-using-def-files.md).

Pour plus d’informations, voir les sections suivantes :

- [Règles pour les instructions Module-Definition](rules-for-module-definition-statements.md)

- [VENTES](exports.md)

- [HEAPSIZE](heapsize.md)

- [Bibliothèque](library.md)

- [NAME](name-c-cpp.md)

- [SECTIONS](sections-c-cpp.md)

- [STACKSIZE](stacksize.md)

- [STUB](stub.md)

- [VERSION](version-c-cpp.md)

- [Mots réservés](reserved-words.md)

## <a name="see-also"></a>Voir aussi

[Référence à la génération C/C++](c-cpp-building-reference.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
