---
title: Outils de génération MSVC supplémentaires
ms.date: 08/28/2019
f1_keywords:
- c.build
helpviewer_keywords:
- builds [C++], C/C++ tools
- tools [C++], build
ms.assetid: 48d9daf4-6bbf-473a-8ce2-bf2923b69f80
ms.openlocfilehash: 53c7c2f8c162cd851b4612e75ba14b019d9cbd63
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177296"
---
# <a name="additional-msvc-build-tools"></a>Outils de génération MSVC supplémentaires

Visual Studio fournit les utilitaires de ligne de commande suivants pour afficher ou manipuler la sortie de la génération:

- [Lib. EXE](lib-reference.md) est utilisé pour créer et gérer une bibliothèque de fichiers objets COFF (Common Object File Format). Il peut également être utilisé pour créer des fichiers d’exportation et des bibliothèques d’importation pour référencer des définitions exportées.

- [EDITBIN. EXE](editbin-reference.md) est utilisé pour modifier les fichiers binaires COFF.

- [DUMPBIN. EXE](dumpbin-reference.md) affiche des informations (par exemple, une table de symboles) sur les fichiers binaires COFF.

- [NMAKE](nmake-reference.md) lit et exécute les Makefiles.

- [ERRLOOK](value-edit-control.md), l’utilitaire de recherche d’erreurs, récupère un message d’erreur système ou un message d’erreur de module en fonction de la valeur entrée.

- [XDCMake](xdcmake-reference.md). Outil pour le traitement des fichiers de code source qui contiennent des commentaires de documentation marqués avec des balises XML.

- [BSCMAKE. EXE](bscmake-reference.md) (fourni à des fins de compatibilité descendante uniquement) crée un fichier d’informations de consultation (. bsc) qui contient des informations sur les symboles (classes, fonctions, données, macros et types) de votre programme. Vous pouvez afficher ces informations dans les fenêtres de navigation au sein de l’environnement de développement. (Un fichier. bsc peut également être généré dans l’environnement de développement.)

Le SDK Windows possède également plusieurs outils de génération, y compris [RC. EXE](/windows/win32/menurc/resource-compiler), que le C++ compilateur appelle pour compiler des ressources Windows natives, telles que des boîtes de dialogue, des pages de propriétés, des bitmaps, des tables de chaînes, etc.

## <a name="see-also"></a>Voir aussi

[Référence de la génération C/C++](c-cpp-building-reference.md)<br/>
[Noms décorés](decorated-names.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
