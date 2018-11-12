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
ms.openlocfilehash: c2c0ee66ed1811755edc33b24737e057554fd01f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542903"
---
# <a name="editbin-reference"></a>Référence EDITBIN

L’éditeur de fichiers binaires Microsoft COFF (EDITBIN. (EXE) modifie les fichiers binaires du fichier Format COFF (Common Object). Vous pouvez y recourir pour modifier des fichiers objets, les fichiers exécutables et les bibliothèques de liens dynamiques (DLL).

> [!NOTE]
>  Vous pouvez démarrer cet outil uniquement à partir de l’invite de commandes de Visual Studio. Vous ne pouvez pas le démarrer à partir d'une invite de commandes système ni de l'Explorateur de fichiers.

EDITBIN n’est pas disponible pour les fichiers générés avec le [/GL](../../build/reference/gl-whole-program-optimization.md) option du compilateur. Toutes les modifications dans des fichiers binaires produits avec /GL aura être atteint par la recompilation et la liaison.

- [Ligne de commande EDITBIN](../../build/reference/editbin-command-line.md)

- [Options EDITBIN](../../build/reference/editbin-options.md)

## <a name="see-also"></a>Voir aussi

[Outils de génération C/C++](../../build/reference/c-cpp-build-tools.md)