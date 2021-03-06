---
description: 'En savoir plus sur : référence MSBuild pour les projets C++'
title: Référence MSBuild pour les projets C++ dans Visual Studio
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: 898757c8b7f1427c36e68a7227ec145abab8d078
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190612"
---
# <a name="msbuild-reference-for-c-projects"></a>Informations de référence sur MSBuild pour les projets C++

MSBuild est le système de génération natif pour tous les projets dans Visual Studio, y compris les projets C++. Quand vous générez un projet dans l’environnement de développement intégré (IDE) de Visual Studio, il appelle l’outil msbuild.exe, qui à son tour consomme le fichier projet. vcxproj et divers fichiers. targets et. props. En général, nous vous recommandons fortement d’utiliser l’IDE de Visual Studio pour définir les propriétés du projet et appeler MSBuild. La modification manuelle des fichiers projet peut entraîner des problèmes sérieux si elle n’est pas effectuée correctement.

Si, pour une raison quelconque, vous souhaitez utiliser MSBuild directement à partir de la ligne de commande, consultez [Utiliser MSBuild à partir de la ligne de commande](../msbuild-visual-cpp.md). Pour plus d’informations sur MSBuild en général, consultez [MSBuild](/visualstudio/msbuild/msbuild) dans la documentation de Visual Studio.

## <a name="in-this-section"></a>Dans cette section

[Composants internes MSBuild pour les projets C++](msbuild-visual-cpp-overview.md)<br/>
Informations sur la façon dont les propriétés et les cibles sont stockées et consommées.

[Macros courantes pour les propriétés et les commandes de build](common-macros-for-build-commands-and-properties.md)<br/>
Décrit les macros (constantes au moment de la compilation) qui peuvent être utilisées pour définir des propriétés telles que les chemins d’accès et les versions de produit.

[Types de fichiers créés pour les projets C++](file-types-created-for-visual-cpp-projects.md)<br/>
Décrit les différents types de fichiers créés par Visual Studio pour différents types de projets.

[Modèles de projet Visual Studio C++](visual-cpp-project-types.md)<br>
Décrit les types de projets basés sur MSBuild qui sont disponibles pour C++.

[Modèles de nouvel élément C++](using-visual-cpp-add-new-item-templates.md)<br>
Décrit les fichiers sources et d’autres éléments que vous pouvez ajouter à un projet Visual Studio.

[Fichiers d’en-tête précompilés](../creating-precompiled-header-files.md) Comment utiliser des fichiers d’en-tête précompilés et comment créer votre propre code précompilé personnalisé pour accélérer les temps de génération.

[Référence des propriétés de projet Visual Studio](property-pages-visual-cpp.md)<br/>
Documentation de référence pour les propriétés de projet qui sont définies dans l’IDE de Visual Studio.

## <a name="see-also"></a>Voir aussi

[Référence à la génération C/C++](c-cpp-building-reference.md)
