---
title: Page de propriétés avancé (projet)
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCConfiguration.VCToolsVersion
ms.description: Use the Advanced property page in Visual Studio 2019 to set various properties for C++ projects.
ms.openlocfilehash: fae3c76d4a62e3b0409664b3630ad76ab601c52b
ms.sourcegitcommit: 610751254a01cba6ad15fb1e1764ecb2e71f66bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2019
ms.locfileid: "68315528"
---
# <a name="advanced-property-page"></a>Page de propriétés avancé

La page de propriétés avancé est disponible dans Visual Studio 2019 et versions ultérieures.

::: moniker range="vs-2019"

## <a name="advanced-properties"></a>Propriétés avancées

- **Extension de fichier cible**

   Spécifie l’extension de fichier à utiliser pour la sortie de la génération. La valeur par défaut est **. exe** pour les applications, **. lib** pour les bibliothèques statiques et **. dll** pour les dll.

- **Extensions à supprimer lors du nettoyage**

   L’option **Nettoyer** (menu **Générer**) supprime les fichiers du répertoire intermédiaire où la configuration d’un projet est générée. Les fichiers portant les extensions spécifiées avec cette propriété sont supprimés quand vous exécutez la commande **Nettoyer** ou quand vous effectuez une regénération. Outre les fichiers qui figurent dans le répertoire intermédiaire avec ces extensions, le système de génération supprime également toute sortie connue de la génération, quel que soit l’emplacement où elle se trouve (y compris les sorties intermédiaires telles que les fichiers .obj). Notez que vous pouvez spécifier des caractères génériques.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>.

- **Fichier journal de génération**

   Vous permet de spécifier un emplacement autre que l'emplacement par défaut pour le fichier journal créé chaque fois que vous générez un projet. L’emplacement par défaut est spécifié par les macros $(IntDir)$(MSBuildProjectName).log.

   Vous pouvez utiliser des macros de projet pour modifier l'emplacement du répertoire. Consultez [les macros courantes pour les propriétés et les commandes de génération](common-macros-for-build-commands-and-properties.md).

- **Architecture de l’outil de génération par défaut**

   Spécifie s’il faut utiliser les outils de génération x86 ou x64.

- **Utiliser les bibliothèques de débogage**

   Spécifie s’il faut créer une version DEBUG ou RELEASE.

- **Activer la build Unity (JUMBO)**

   Active un processus de génération dans C++ lequel de nombreux fichiers sources sont combinés en un ou plusieurs fichiers «Unity» avant la compilation pour améliorer les performances de génération. Non lié au moteur de jeu Unity.

- **Utilisation des MFC**

   Spécifie si le projet MFC sera lié de manière statique ou dynamique à la DLL MFC. Les projets non-MFC peuvent sélectionner **Utiliser les bibliothèques Windows standard** pour établir des liaisons à différentes bibliothèques Win32 qui sont incluses quand vous utilisez MFC.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>.

- **Jeu de caractères**

   Définit si _UNICODE ou _MBCS doit être défini. Affecte également le point d'entrée de l'éditeur de liens le cas échéant.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>.

- **Optimisation de l’ensemble du programme**

   Spécifie l’option du compilateur [/GL](gl-whole-program-optimization.md) et l’option de l’éditeur de liens [/LTCG](ltcg-link-time-code-generation.md). Par défaut, cette option est désactivée pour les configurations Debug, et activée pour les configurations Retail.

- **Version de l’ensemble d’outils MSVC**

   Spécifie la version complète de l’ensemble d’outils MSVC qui sera utilisée pour générer le projet. Si vous avez installé plusieurs versions de mise à jour et de préversion d’un ensemble d’outils, vous pouvez spécifier celui à utiliser ici.

## <a name="ccli-properties"></a>C++Propriétés/CLI

- **Prise en charge du Common Language Runtime**

   Entraîne l’utilisation de l’option du compilateur [/clr](clr-common-language-runtime-compilation.md).

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>.

- **Version du .NET Framework cible**

   Dans les projets managés, spécifie la version du .NET Framework à cibler.

- **Activer la build incrémentielle managée**

   Pour les projets managés, active la détection de la visibilité externe quand vous générez des assemblys. Si un changement apporté à un projet managé n’est pas visible par d’autres projets, les projets dépendants ne sont pas regénérés. Il peut en résulter une réduction considérable des durées de génération dans les solutions qui incluent des projets managés.

::: moniker-end
