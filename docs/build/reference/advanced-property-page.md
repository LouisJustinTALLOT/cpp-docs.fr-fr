---
title: Page de propriétés avancé (projet)
ms.date: 08/10/2020
f1_keywords:
- VC.Project.VCConfiguration.VCToolsVersion
ms.description: Use the Advanced property page in Visual Studio 2019 to set various properties for C++ projects.
ms.openlocfilehash: 3b1e45f984cd40d6ea42ead25b045fc8688ad0a7
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924042"
---
# <a name="advanced-property-page"></a>Page de propriétés avancé

::: moniker range="<=msvc-150"

La page de propriétés avancé est disponible dans Visual Studio 2019 et versions ultérieures. Pour afficher la documentation de cette version, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end

::: moniker range="msvc-160"

La page de propriétés avancé est disponible dans Visual Studio 2019 et versions ultérieures.

## <a name="advanced-properties"></a>Propriétés avancées

- **Extension de fichier cible**

   Spécifie l’extension de fichier à utiliser pour la sortie de la génération. La valeur par défaut est pour *`.exe`* les applications, *`.lib`* pour les bibliothèques statiques et *`.dll`* pour les dll.

- **Extensions à supprimer lors du nettoyage**

   L’option **Nettoyer** (menu **Générer** ) supprime les fichiers du répertoire intermédiaire où la configuration d’un projet est générée. Les fichiers dont les extensions sont spécifiées dans cette propriété sont supprimés lorsque le **nettoyage** est exécuté ou lorsque vous régénérez. Le système de génération supprime tous les fichiers qui ont ces extensions dans le répertoire intermédiaire. Elle supprime également toute sortie connue de la génération, quel que soit l’emplacement où elle se trouve. (Qui comprend les sorties intermédiaires telles que les *`.obj`* fichiers.) Vous pouvez spécifier des caractères génériques dans cette propriété.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>.

- **Fichier journal de génération**

   Vous permet de spécifier un emplacement autre que celui par défaut pour le fichier journal créé chaque fois que vous générez un projet. L’emplacement par défaut est spécifié par les macros `$(IntDir)$(MSBuildProjectName).log` .

   Vous pouvez utiliser des macros de projet pour modifier l'emplacement du répertoire. Consultez [les macros courantes pour les propriétés et les commandes de génération](common-macros-for-build-commands-and-properties.md).

- **Architecture de l’outil de génération par défaut**

   Spécifie s’il faut utiliser les outils de génération x86 ou x64.

- **Utiliser les bibliothèques de débogage**

   Spécifie s’il faut créer une version Debug ou Release.

- **Activer la build Unity (JUMBO)**

   Active un processus de génération plus rapide qui combine de nombreux fichiers sources C++ dans un ou plusieurs fichiers avant la compilation. Ces fichiers combinés sont appelés fichiers *Unity* . Ils ne sont pas liés au moteur de jeu Unity.

- **Copier le contenu dans OutDir**

   Copiez les éléments marqués en tant que *contenu* dans le projet dans le répertoire de sortie du projet ( `$(OutDir)` ). Ce paramètre peut simplifier le déploiement. Cette propriété est disponible à partir de Visual Studio 2019 version 16,7.

- **Copier les références de projet dans OutDir**

   Copiez les éléments de référence du projet exécutable (fichier DLL et EXE) dans le répertoire de sortie du projet ( `$(OutDir)` ). Dans les projets C++/CLI ( [`/clr`](clr-common-language-runtime-compilation.md) ), cette propriété est ignorée. Au lieu de cela, la propriété **copie locale** de chaque référence de projet contrôle si elle est copiée dans le répertoire de sortie. Ce paramètre peut simplifier le déploiement local. Il est disponible à partir de Visual Studio 2019 version 16,7.

- **Copier les symboles des références de projet dans OutDir**

   Copiez les fichiers PDB pour les éléments de référence de projet avec les éléments exécutables de référence du projet dans le répertoire de sortie du projet ( `$(OutDir)` ). Cette propriété est toujours activée pour les projets C++/CLI. Ce paramètre peut simplifier le déploiement du débogage. Il est disponible à partir de Visual Studio 2019 version 16,7.

- **Copier le runtime C++ dans OutDir**

   Copiez les dll du runtime dans le répertoire de sortie du projet ( `$(OutDir)` ). Ce paramètre peut simplifier le déploiement local. Il est disponible à partir de Visual Studio 2019 version 16,7.

- **Utilisation des MFC**

   Spécifie si le projet MFC est lié de manière statique ou dynamique à la DLL MFC. Dans les projets non-MFC, sélectionnez **utiliser les bibliothèques Windows standard** pour lier les bibliothèques Win32 incluses par MFC.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>.

- **Jeu de caractères**

   Définit si `_UNICODE` ou `_MBCS` doit être défini. Affecte également le point d'entrée de l'éditeur de liens le cas échéant.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>.

- **Optimisation de l’ensemble du programme**

   Spécifie l’option [`/GL`](gl-whole-program-optimization.md) de compilateur et l’option de l' [`/LTCG`](ltcg-link-time-code-generation.md) éditeur de liens. Par défaut, l’optimisation de l’ensemble du programme est désactivée pour les configurations de débogage et activée pour les configurations Release.

- **Version de l’ensemble d’outils MSVC**

   Spécifie la version complète de l’ensemble d’outils MSVC utilisé pour générer le projet. Plusieurs versions de mise à jour et d’aperçu d’un ensemble d’outils sont peut-être installées. Vous pouvez spécifier celui à utiliser ici.

## <a name="ccli-properties"></a>Propriétés C++/CLI

- **Prise en charge du Common Language Runtime**

   Provoque l' [`/clr`](clr-common-language-runtime-compilation.md) utilisation de l’option du compilateur.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>.

- **Version du .NET Framework cible**

   Dans les projets managés, spécifie la version du .NET Framework à cibler.

- **Activer la build incrémentielle managée**

   Pour les projets managés, cette option active la détection de la visibilité externe lorsque vous générez des assemblys. Si une modification apportée à un projet managé n’est pas visible pour les autres projets, les projets dépendants ne sont pas reconstruits. Les builds incrémentielles managées peuvent améliorer considérablement les temps de génération dans les solutions qui incluent des projets managés.

::: moniker-end
