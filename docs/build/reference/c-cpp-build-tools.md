---
title: Outils de génération C/C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- c.build
dev_langs:
- C++
helpviewer_keywords:
- builds [C++], C/C++ tools
- tools [C++], build
ms.assetid: 48d9daf4-6bbf-473a-8ce2-bf2923b69f80
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a6a223e092e7ad31dd263142d2a87712eaf556b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726035"
---
# <a name="cc-build-tools"></a>Outils de génération C/C++

Visual C++ fournit les outils de ligne de commande suivants pour l’affichage ou la manipulation de sortie de génération :

- [BSCMAKE. EXE](../../build/reference/bscmake-reference.md) génère un fichier d’informations de consultation (.bsc) qui contient des informations sur les symboles (classes, fonctions, données, macros et types) dans votre programme. Vous permet d’afficher ces informations dans les fenêtres de navigation au sein de l’environnement de développement. (Un fichier .bsc peut également être généré dans l’environnement de développement.)

- [LIB. EXE](../../build/reference/lib-reference.md) est utilisé pour créer et gérer une bibliothèque de fichiers d’objets fichier Format COFF (Common Object). Il peut également être utilisé pour créer des fichiers d’exportation et de bibliothèques d’importation pour référencer des définitions exportées.

- [EDITBIN. EXE](../../build/reference/editbin-reference.md) est utilisé pour modifier les fichiers binaires COFF.

- [DUMPBIN. EXE](../../build/reference/dumpbin-reference.md) affiche des informations (par exemple, une table de symboles) sur les fichiers binaires COFF.

- [NMAKE](../../build/nmake-reference.md) lit et exécute des makefiles.

- [ERRLOOK](../../build/reference/value-edit-control.md), l’utilitaire de recherche d’erreurs, récupère un message d’erreur système ou d’un message d’erreur de module selon la valeur entrée.

## <a name="see-also"></a>Voir aussi

[Référence de la génération C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Noms décorés](../../build/reference/decorated-names.md)<br/>
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)