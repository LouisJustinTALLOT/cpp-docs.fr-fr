---
description: 'En savoir plus sur : référence EDITBIN'
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
ms.openlocfilehash: ad211ab85ac00cd716b7c3b8e381a9a448ea04ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201025"
---
# <a name="editbin-reference"></a>Référence EDITBIN

L’éditeur de fichiers binaires COFF Microsoft (EDITBIN.EXE) modifie les fichiers binaires COFF (Common Object File Format). Vous pouvez utiliser EDITBIN pour modifier des fichiers objets, des fichiers exécutables et des bibliothèques de liens dynamiques (DLL).

> [!NOTE]
> Vous pouvez démarrer cet outil uniquement à partir de l’invite de commandes de Visual Studio. Vous ne pouvez pas le démarrer à partir d'une invite de commandes système ni de l'Explorateur de fichiers.

EDITBIN ne peut pas être utilisé sur les fichiers produits avec l’option du compilateur [/GL](gl-whole-program-optimization.md) . Toutes les modifications apportées aux fichiers binaires générés avec/GL devront être réalisées par recompilation et liaison.

- [Ligne de commande EDITBIN](editbin-command-line.md)

- [Options EDITBIN](editbin-options.md)

## <a name="see-also"></a>Voir aussi

[Outils de génération MSVC supplémentaires](c-cpp-build-tools.md)
