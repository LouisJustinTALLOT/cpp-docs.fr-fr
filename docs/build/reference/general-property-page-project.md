---
title: Général, page de propriétés (Projet)
ms.date: 07/17/2019
f1_keywords:
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.ManagedExtensions
- VC.Project.VCConfiguration.BuildBrowserInformation
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.ATLMinimizesCRunTimeLibraryUsage
- VC.Project.VCConfiguration.ReferencesPath
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.useOfMfc
- VC.Project.VCConfiguration.CharacterSet
- VC.Project.VCGeneralMakefileSettings.ConfigurationType
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.AppSupport
- VC.Project.VCConfiguration.ToolFiles
- VC.Project.VCConfiguration.useOfATL
helpviewer_keywords:
- Clean Build option
- output files, setting directory
- Unicode, creating C++ build configuration
ms.openlocfilehash: eb172e7bd76816458a0efff7b053d136f52076ab
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78166756"
---
# <a name="general-property-page-project"></a>Général, page de propriétés (Projet)

::: moniker range=">=vs-2019"

Cette rubrique s’applique aux projets Visual Studio pour Windows. Pour les projets Linux, consultez les informations de référence sur les [pages de propriétés Linux C++ ](../../linux/prop-pages-linux.md). Pour les projets CMake, consultez [projets cmake dans Visual Studio](../cmake-projects-in-visual-studio.md). Pour les projets Android, consultez [Propriétés générales du projet C++(Android)](/cpp/cross-platform/general-android-prop-page). Pour les projets Makefile Android, consultez [Propriétés générales du projet C++ (Makefile Android)](/cpp/cross-platform/general-makefile-android-prop-page) .

Lorsque vous cliquez avec le bouton droit sur un nœud de projet dans Explorateur de solutions, puis sélectionnez **Propriétés**, la page de propriétés **général** sous le nœud **Propriétés de configuration** dans le volet gauche affiche les propriétés suivantes :

- **Répertoire de sortie**

   Spécifie le répertoire dans lequel des outils, tels que l'éditeur de liens, placent tous les fichiers de sortie finaux créés pendant le processus de génération. En règle générale, cela inclut la sortie d'outils comme l'éditeur de liens, le Générateur de bibliothèques ou BSCMake. Par défaut, cette propriété est le répertoire spécifié par les macros $(SolutionDir)$(Configuration)\.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>.

- **Répertoire intermédiaire**

   Spécifie le répertoire dans lequel des outils, tels que le compilateur, placent tous les fichiers intermédiaires créés pendant le processus de génération. En règle générale, cela inclut la sortie d'outils tels que le compilateur C/C++, MIDL et le compilateur de ressources. Par défaut, cette propriété est le répertoire spécifié par la macro $(Configuration)\.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>.

- **Nom de la cible**

   Spécifie le nom de fichier généré par ce projet. Par défaut, cette propriété est le nom de fichier spécifié par la macro $(ProjectName).

- **Type de configuration**

  Vous pouvez choisir parmi plusieurs types de configuration :

  - **Application (.exe)**

     Affiche l’ensemble d’outils de l’éditeur de liens (compilateur C/C++, MIDL, compilateur de ressources, éditeur de liens, BSCMake, Générateur proxy du service web XML, événements de build/prebuild/préliaison/postbuild personnalisés).

  - **Bibliothèque dynamique (.dll)**

     Affiche l’ensemble d’outils de l’éditeur de liens, spécifie l’option /DLL de l’éditeur de liens et ajoute la définition _WINDLL à CL.

  - **Makefile**

     Affiche l’ensemble d’outils makefile (NMake).

  - **Bibliothèque statique (.lib)**

     Affiche l’ensemble d’outils du Générateur de bibliothèques (identique à celui de l’éditeur de liens, sauf qu’il contient le Générateur de bibliothèques au lieu de l’éditeur de liens et qu’il ne contient pas le Générateur proxy du service web XML).

  - **Utilitaire**

     Affiche l’ensemble d’outils d’utilitaires (MIDL, événements de build/prebuild/postbuild personnalisés).

  Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>.

- **Version du SDK Windows**

   Pour la plateforme cible Windows, spécifie la version du SDK Windows qu’exige votre projet. Quand vous installez une charge de travail C++ à l’aide du programme d’installation de Visual Studio, les parties obligatoires du SDK Windows sont également installées. Si vous avez d’autres versions du SDK Windows sur votre ordinateur, chaque version de SDK Tools que vous avez installée est répertoriée dans la liste déroulante.

   Pour cibler Windows 7 ou Windows Vista, utilisez la valeur **8.1** puisque le SDK Windows 8.1 offre une compatibilité descendante avec ces plateformes. En outre, vous devez définir la valeur appropriée pour **_WIN32_WINNT** dans targetver.h. Pour Windows 7, il s'agit de 0x0601. Consultez [Modification de WINVER et _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md).

   Vous pouvez installer l’ensemble d’outils de plateforme Windows XP inclus dans Visual Studio pour utiliser la version actuelle des bibliothèques afin de générer des projets Windows XP et Windows 2003 Server. Pour plus d’informations sur l’obtention et l’utilisation de cet ensemble d’outils de plateforme, consultez [Configuration des programmes pour Windows XP](../configuring-programs-for-windows-xp.md). Pour plus d’informations sur la modification de l’ensemble d’outils de plateforme, consultez [Guide pratique pour modifier le framework cible et l’ensemble d’outils de la plateforme](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **Ensemble d’outils de plateforme**

   Permet au projet de cibler une version différente des bibliothèques Visual C++ et du compilateur. Les projets C++ Visual Studio peuvent cibler l’ensemble d’outils par défaut installé par Visual Studio, ou l’un des ensembles d’outils installés par plusieurs versions précédentes de Visual Studio, y compris les ensembles d’outils qui créent des exécutables pouvant s’exécuter sous Windows XP. Pour obtenir des informations sur le changement de l’ensemble d’outils de plateforme, consultez [Guide pratique pour modifier le framework cible et l’ensemble d’outils de la plateforme](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **C++Norme du langage**

   Spécifie la norme de langue à utiliser. La valeur par défaut est/std : c++ 14. Spécifiez/std : c++ 17 pour utiliser les fonctionnalités C++ 17 ou/std : c++ + latest pour utiliser C++ 20 ou d’autres fonctionnalités expérimentales. Pour plus d’informations, consultez [/STD (spécifier la version du langage standard)](std-specify-language-standard-version.md) .

::: moniker-end

::: moniker range="<=vs-2017"

Dans Visual Studio 2015 et Visual Studio 2017, lorsque vous cliquez avec le bouton droit sur un nœud de projet dans **Explorateur de solutions**, et que vous sélectionnez **Propriétés**, la page de propriétés **général** sous le nœud **Propriétés de configuration** dans le volet gauche affiche deux sections de propriétés :

- Général

- Paramètres par défaut du projet

## <a name="general"></a>Général

- **Plateforme cible**

   Spécifie la plateforme sur laquelle le projet s'exécutera. Par exemple Windows, Android ou iOS. La valeur **Windows 10** signifie que le projet cible la plateforme Windows universelle. Si vous ciblez des versions antérieures de Windows, la version n’est pas répertoriée et la valeur de ce champ est simplement **Windows**. Il s'agit d'un champ en lecture seule qui est défini quand vous créez un projet.

- **Version de la plateforme cible (Visual Studio 2015)**

   Spécifie la version la plus basse de la plateforme sur laquelle le projet peut s'exécuter. Cette propriété s’affiche uniquement si le type de projet le prend en charge. Si votre application peut tirer parti des fonctionnalités offertes par une nouvelle version du Kit SDK Windows tout en pouvant s'exécuter sur des versions antérieures sans ces fonctionnalités (éventuellement avec une perte de fonctionnalité), la valeur de ces deux propriétés peut être différente. Dans ce cas, votre code doit vérifier au moment de l'exécution la version de la plateforme sur laquelle il s'exécute et ne pas essayer d'utiliser des fonctionnalités qui ne sont pas disponibles dans les versions antérieures de la plateforme.

   Le C++ système de projet n’applique pas cette option. Elle est fournie par souci de cohérence avec d'autres langages, tels que C# et JavaScript, et comme guide pour toute personne qui utilise votre projet. Visual C++ ne génère pas d'erreur si vous utilisez une fonctionnalité qui n'est pas disponible dans la version minimale.

- **Version de SDK Windows (Visual Studio 2017)**

   Pour la plateforme cible Windows, spécifie la version du SDK Windows qu’exige votre projet. Quand vous installez une charge de travail C++ à l’aide du programme d’installation de Visual Studio, les parties obligatoires du SDK Windows sont également installées. Si vous avez d’autres versions du SDK Windows sur votre ordinateur, chaque version de SDK Tools que vous avez installée est répertoriée dans la liste déroulante.

   Pour cibler Windows 7 ou Windows Vista, utilisez la valeur **8.1** puisque le SDK Windows 8.1 offre une compatibilité descendante avec ces plateformes. En outre, vous devez définir la valeur appropriée pour **_WIN32_WINNT** dans targetver.h. Pour Windows 7, il s'agit de 0x0601. Consultez [Modification de WINVER et _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md).

   Vous pouvez installer l’ensemble d’outils de plateforme Windows XP inclus dans Visual Studio pour utiliser la version actuelle des bibliothèques afin de générer des projets Windows XP et Windows 2003 Server. Pour plus d’informations sur l’obtention et l’utilisation de cet ensemble d’outils de plateforme, consultez [Configuration des programmes pour Windows XP](../configuring-programs-for-windows-xp.md). Pour plus d’informations sur la modification de l’ensemble d’outils de plateforme, consultez [Guide pratique pour modifier le framework cible et l’ensemble d’outils de la plateforme](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **Répertoire de sortie**

   Spécifie le répertoire dans lequel des outils, tels que l'éditeur de liens, placent tous les fichiers de sortie finaux créés pendant le processus de génération. En règle générale, cela inclut la sortie d'outils comme l'éditeur de liens, le Générateur de bibliothèques ou BSCMake. Par défaut, cette propriété est le répertoire spécifié par les macros $(SolutionDir)$(Configuration)\.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>.

- **Répertoire intermédiaire**

   Spécifie le répertoire dans lequel des outils, tels que le compilateur, placent tous les fichiers intermédiaires créés pendant le processus de génération. En règle générale, cela inclut la sortie d'outils tels que le compilateur C/C++, MIDL et le compilateur de ressources. Par défaut, cette propriété est le répertoire spécifié par la macro $(Configuration)\.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>.

- **Nom de la cible**

   Spécifie le nom de fichier généré par ce projet. Par défaut, cette propriété est le nom de fichier spécifié par la macro $(ProjectName).

- **Extension de la cible**

   Spécifie l'extension de nom de fichier générée par ce projet, par exemple .exe ou .dll.

- **Extensions à supprimer lors du nettoyage**

   L’option **Nettoyer** (menu **Générer**) supprime les fichiers du répertoire intermédiaire où la configuration d’un projet est générée. Les fichiers portant les extensions spécifiées avec cette propriété sont supprimés quand vous exécutez la commande **Nettoyer** ou quand vous effectuez une regénération. Outre les fichiers qui figurent dans le répertoire intermédiaire avec ces extensions, le système de génération supprime également toute sortie connue de la génération, quel que soit l’emplacement où elle se trouve (y compris les sorties intermédiaires telles que les fichiers .obj). Notez que vous pouvez spécifier des caractères génériques.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>.

- **Fichier journal de génération**

   Vous permet de spécifier un emplacement autre que l'emplacement par défaut pour le fichier journal créé chaque fois que vous générez un projet. L’emplacement par défaut est spécifié par les macros $(IntDir)$(MSBuildProjectName).log.

   Vous pouvez utiliser des macros de projet pour modifier l'emplacement du répertoire. Consultez [les macros courantes pour les propriétés et les commandes de génération](common-macros-for-build-commands-and-properties.md).

- **Ensemble d’outils de plateforme**

   Permet au projet de cibler une version différente des bibliothèques Visual C++ et du compilateur. Les projets C++ Visual Studio peuvent cibler l’ensemble d’outils par défaut installé par Visual Studio, ou l’un des ensembles d’outils installés par plusieurs versions précédentes de Visual Studio, y compris les ensembles d’outils qui créent des exécutables pouvant s’exécuter sous Windows XP. Pour obtenir des informations sur le changement de l’ensemble d’outils de plateforme, consultez [Guide pratique pour modifier le framework cible et l’ensemble d’outils de la plateforme](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **Activer la build incrémentielle managée**

   Pour les projets managés, active la détection de la visibilité externe quand vous générez des assemblys. Si un changement apporté à un projet managé n’est pas visible par d’autres projets, les projets dépendants ne sont pas regénérés. Il peut en résulter une réduction considérable des durées de génération dans les solutions qui incluent des projets managés.

## <a name="project-defaults"></a>Paramètres par défaut du projet

Les propriétés de la section Paramètres par défaut du projet représentent les propriétés par défaut que vous pouvez modifier. La définition de ces propriétés est accessible dans les fichiers .props dans *Installation Directory*\VC\VCProjectDefaults.

- **Type de configuration**

  Vous pouvez choisir parmi plusieurs types de configuration :

  - **Application (.exe)**

     Affiche l’ensemble d’outils de l’éditeur de liens (compilateur C/C++, MIDL, compilateur de ressources, éditeur de liens, BSCMake, Générateur proxy du service web XML, événements de build/prebuild/préliaison/postbuild personnalisés).

  - **Bibliothèque dynamique (.dll)**

     Affiche l’ensemble d’outils de l’éditeur de liens, spécifie l’option /DLL de l’éditeur de liens et ajoute la définition _WINDLL à CL.

  - **Makefile**

     Affiche l’ensemble d’outils makefile (NMake).

  - **Bibliothèque statique (.lib)**

     Affiche l’ensemble d’outils du Générateur de bibliothèques (identique à celui de l’éditeur de liens, sauf qu’il contient le Générateur de bibliothèques au lieu de l’éditeur de liens et qu’il ne contient pas le Générateur proxy du service web XML).

  - **Utilitaire**

     Affiche l’ensemble d’outils d’utilitaires (MIDL, événements de build/prebuild/postbuild personnalisés).

  Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>.

- **Utilisation des MFC**

   Spécifie si le projet MFC sera lié de manière statique ou dynamique à la DLL MFC. Les projets non-MFC peuvent sélectionner **Utiliser les bibliothèques Windows standard** pour établir des liaisons à différentes bibliothèques Win32 qui sont incluses quand vous utilisez MFC.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>.

- **Jeu de caractères**

   Définit si _UNICODE ou _MBCS doit être défini. Affecte également le point d'entrée de l'éditeur de liens le cas échéant.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>.

- **Prise en charge du Common Language Runtime**

   Entraîne l’utilisation de l’option du compilateur [/clr](clr-common-language-runtime-compilation.md).

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>.

- **Version du .NET Framework cible**

   Dans les projets managés, spécifie la version du .NET Framework à cibler.

- **Optimisation de l’ensemble du programme**

   Spécifie l’option du compilateur [/GL](gl-whole-program-optimization.md) et l’option de l’éditeur de liens [/LTCG](ltcg-link-time-code-generation.md). Par défaut, cette option est désactivée pour les configurations Debug, et activée pour les configurations Retail.

- **Prise en charge d’applications du Windows Store**

   Spécifie si ce projet prend en charge les applications Windows Runtime (plateforme Windows universelle). Pour plus d’informations, consultez [/ZW (compilation Windows Runtime)](zw-windows-runtime-compilation.md) et le Centre de développement Windows.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[C++Référence de la page de propriétés du projet](property-pages-visual-cpp.md)
