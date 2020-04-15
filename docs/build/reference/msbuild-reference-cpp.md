---
title: Référence MSBuild pour les projets de CMD dans Visual Studio
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: 96987a252d12f718025dd55deecad5c6bac26872
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336211"
---
# <a name="msbuild-reference-for-c-projects"></a>Informations de référence sur MSBuild pour les projets C++

MSBuild est le système de construction natif pour tous les projets de Visual Studio, y compris les projets C. Lorsque vous construisez un projet dans l’environnement de développement intégré Visual Studio (IDE), il invoque l’outil msbuild.exe, qui consomme à son tour le fichier de projet .vcxproj, et divers fichiers .targets et .props. En général, nous vous recommandons fortement d’utiliser le Visual Studio IDE pour définir les propriétés du projet et invoquer MSBuild. L’édition manuelle des fichiers de projet peut entraîner de graves problèmes s’il n’est pas fait correctement.

Si pour une raison quelconque vous souhaitez utiliser MSBuild directement à partir de la ligne de commande, voir [Utilisez MSBuild de la ligne de commande](../msbuild-visual-cpp.md). Pour plus d’informations sur MSBuild en général, voir [MSBuild](/visualstudio/msbuild/msbuild) dans la documentation Visual Studio.

## <a name="in-this-section"></a>Contenu de cette section

[Composants internes MSBuild pour les projets C++](msbuild-visual-cpp-overview.md)<br/>
Informations sur la façon dont les propriétés et les cibles sont stockées et consommées.

[Macros courantes pour les propriétés et les commandes de build](common-macros-for-build-commands-and-properties.md)<br/>
Décrit les macros (compiler les constantes) qui peuvent être utilisés pour définir des propriétés telles que les chemins et les versions de produits.

[Types de fichiers créés pour les projets C](file-types-created-for-visual-cpp-projects.md)<br/>
Décrit les différents types de fichiers que Visual Studio crée pour différents types de projets.

[Modèles de projets Visual Studio CMD](visual-cpp-project-types.md)<br>
Décrit les types de projets basés sur msBuild qui sont disponibles pour le C.

[Modèle de nouvel élément C++](using-visual-cpp-add-new-item-templates.md)<br>
Décrit les fichiers sources et autres éléments que vous pouvez ajouter à un projet Visual Studio.

[Fichiers d’en-tête précompilés](../creating-precompiled-header-files.md) Comment utiliser les fichiers d’en-tête précompilés et comment créer votre propre code précompilé personnalisé pour accélérer les temps de construction.

[Référence de propriété de projet de studio visuel](property-pages-visual-cpp.md)<br/>
Documentation de référence pour les propriétés du projet qui sont définies dans le Visual Studio IDE.

## <a name="see-also"></a>Voir aussi

[Référence à la génération C/C++](c-cpp-building-reference.md)
