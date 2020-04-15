---
title: Page de propriété avancée (Projet)
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCConfiguration.VCToolsVersion
ms.description: Use the Advanced property page in Visual Studio 2019 to set various properties for C++ projects.
ms.openlocfilehash: 8ce62b768f5cda30501e791bcd040a40b18bfb23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328428"
---
# <a name="advanced-property-page"></a>Page de propriété avancée

La page de propriété Advanced est disponible en Visual Studio 2019 et plus tard.

::: moniker range="vs-2019"

## <a name="advanced-properties"></a>Propriétés avancées

- **Extension du fichier cible**

   Spécifie l’extension de fichier à utiliser pour la sortie de construction. Par défaut de **.exe** pour les applications, **.lib** pour les bibliothèques statiques et **.dll** pour DLLs.

- **Extensions à supprimer lors du nettoyage**

   L’option **Nettoyer** (menu **Générer**) supprime les fichiers du répertoire intermédiaire où la configuration d’un projet est générée. Les fichiers portant les extensions spécifiées avec cette propriété sont supprimés quand vous exécutez la commande **Nettoyer** ou quand vous effectuez une regénération. Outre les fichiers qui figurent dans le répertoire intermédiaire avec ces extensions, le système de génération supprime également toute sortie connue de la génération, quel que soit l’emplacement où elle se trouve (y compris les sorties intermédiaires telles que les fichiers .obj). Notez que vous pouvez spécifier des caractères génériques.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>.

- **Fichier journal de génération**

   Vous permet de spécifier un emplacement autre que l'emplacement par défaut pour le fichier journal créé chaque fois que vous générez un projet. L’emplacement par défaut est spécifié par les macros $(IntDir)$(MSBuildProjectName).log.

   Vous pouvez utiliser des macros de projet pour modifier l'emplacement du répertoire. Voir [macros communes pour les commandes de construction et les propriétés](common-macros-for-build-commands-and-properties.md).

- **Architecture d’outil de construction préférée**

   Précise s’il faut utiliser les outils de construction x86 ou x64.

- **Utiliser les bibliothèques Debug**

   Précise s’il faut créer une construction DEBUG ou RELEASE.

- **Activer la construction d’Unité (JUMBO)**

   Permet un processus de construction où de nombreux fichiers source CMD sont combinés dans un ou plusieurs fichiers « unité » avant compilation pour améliorer les performances de construction. Sans rapport avec le moteur de jeu Unity.

- **Utilisation des MFC**

   Spécifie si le projet MFC sera lié de manière statique ou dynamique à la DLL MFC. Les projets non-MFC peuvent sélectionner **Utiliser les bibliothèques Windows standard** pour établir des liaisons à différentes bibliothèques Win32 qui sont incluses quand vous utilisez MFC.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>.

- **Ensemble de caractères**

   Définit si _UNICODE ou _MBCS doit être défini. Affecte également le point d'entrée de l'éditeur de liens le cas échéant.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>.

- **Optimisation de l'ensemble du programme**

   Spécifie l’option du compilateur [/GL](gl-whole-program-optimization.md) et l’option de l’éditeur de liens [/LTCG](ltcg-link-time-code-generation.md). Par défaut, cette option est désactivée pour les configurations Debug, et activée pour les configurations Retail.

- **MSVC Toolset Version**

   Spécifie la version complète de l’ensemble d’outils MSVC qui sera utilisé pour construire le projet. Si vous avez différentes versions de mise à jour et de prévisualisation d’un toolset installé, vous pouvez spécifier lequel utiliser ici.

## <a name="ccli-properties"></a>Propriétés CMD/CLI

- **Prise en charge du Common Language Runtime**

   Entraîne l’utilisation de l’option du compilateur [/clr](clr-common-language-runtime-compilation.md).

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>.

- **Version du .NET Framework cible**

   Dans les projets managés, spécifie la version du .NET Framework à cibler.

- **Activer la build incrémentielle managée**

   Pour les projets managés, active la détection de la visibilité externe quand vous générez des assemblys. Si un changement apporté à un projet managé n’est pas visible par d’autres projets, les projets dépendants ne sont pas regénérés. Il peut en résulter une réduction considérable des durées de génération dans les solutions qui incluent des projets managés.

::: moniker-end
