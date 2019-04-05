---
title: Référence MSBuild pour les projets C++ dans Visual Studio
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: b6ec6b5d276cb7104cf61c229476596d2a2a7684
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024697"
---
# <a name="msbuild-reference-for-c-projects"></a>Référence MSBuild pour les projets C++

MSBuild est le système de génération natifs pour tous les projets dans Visual Studio, y compris les projets C++. Lorsque vous générez un projet dans l’environnement de développement intégré (IDE) Visual Studio, elle appelle l’outil msbuild.exe, qui à son tour utilise le fichier de projet .vcxproj et divers fichiers .targets et .props. En règle générale, nous vous recommandons vivement d’à l’aide de l’IDE Visual Studio pour définir les propriétés du projet et appelez MSBuild. Modification manuelle des fichiers de projet peut entraîner des problèmes graves si ne pas effectuée correctement.

Si pour une raison quelconque, vous souhaitez utiliser MSBuild directement à partir de la ligne de commande, consultez [utilisation de MSBuild à partir de la ligne de commande](../msbuild-visual-cpp.md). Pour plus d’informations sur MSBuild, en général, consultez [MSBuild](/visualstudio/msbuild/msbuild) dans la documentation de Visual Studio.

## <a name="in-this-section"></a>Dans cette section

[Éléments internes de MSBuild pour les projets C++](msbuild-visual-cpp-overview.md)<br/>
Informations sur la façon dont les propriétés et cibles sont stockées et consommées.

[Macros courantes pour les propriétés et les commandes de build](common-macros-for-build-commands-and-properties.md)<br/>
Décrit les macros (constantes de compilation) qui peuvent être utilisées pour définir des propriétés telles que les chemins d’accès et les versions du produit.

[Types de fichiers créés pour les projets C++](file-types-created-for-visual-cpp-projects.md)<br/>
Décrit les différents types de fichiers créé par Visual Studio pour différents types de projets.

[Modèles de projet Visual Studio C++](visual-cpp-project-types.md)<br>
Décrit les types de projet MSBuild qui sont disponibles pour C++.

[Modèles d’élément nouveau C++](using-visual-cpp-add-new-item-templates.md)<br>
Décrit les fichiers sources et autres éléments que vous pouvez ajouter à un projet Visual Studio.

[Fichiers d’en-tête précompilés](../creating-precompiled-header-files.md) comment utiliser les fichiers d’en-tête précompilé et comment créer vos propres précompilé accélérer les temps de génération de code.

[Référence des propriétés de projet Visual Studio](property-pages-visual-cpp.md)<br/>
Documentation de référence pour les propriétés de projet qui sont définies dans l’IDE Visual Studio.

## <a name="see-also"></a>Voir aussi

[Référence à la génération C/C++](c-cpp-building-reference.md)