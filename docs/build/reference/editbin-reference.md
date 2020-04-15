---
title: Référence EDITBIN
ms.date: 11/04/2016
f1_keywords:
- editbin
helpviewer_keywords:
- binary data, editing
- object files, modifying
- EDITBIN program
- COFF files, editing
ms.assetid: efdda03b-3dfc-4d31-90e6-caf5b3977914
ms.openlocfilehash: 266347de063b4e050cb032aa2d8d74e7934b8081
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328349"
---
# <a name="editbin-reference"></a>Référence EDITBIN

L’éditeur de fichiers binaires Microsoft COFF (EDITBIN. EXE) modifie les fichiers binaires Common Object File Format (COFF). Vous pouvez utiliser EDITBIN pour modifier les fichiers d’objets, les fichiers exécutables et les bibliothèques à liens dynamiques (DLL).

> [!NOTE]
> Vous pouvez démarrer cet outil uniquement à partir de l’invite de commande Visual Studio. Vous ne pouvez pas le démarrer à partir d'une invite de commandes système ni de l'Explorateur de fichiers.

EDITBIN n’est pas disponible pour une utilisation sur les fichiers produits avec l’option [compilateur /GL.](gl-whole-program-optimization.md) Toute modification des fichiers binaires produits avec /GL devra être réalisée en recompilant et en reliant.

- [Ligne de commande EDITBIN](editbin-command-line.md)

- [Options EDITBIN](editbin-options.md)

## <a name="see-also"></a>Voir aussi

[Outils de construction MSVC supplémentaires](c-cpp-build-tools.md)
