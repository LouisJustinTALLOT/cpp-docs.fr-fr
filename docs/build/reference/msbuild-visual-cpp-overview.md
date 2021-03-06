---
title: Composants internes MSBuild pour les projets C++ dans Visual Studio
description: Fichiers de prise en charge, propriétés et cibles utilisés par MSBuild pour les projets Visual Studio C++.
ms.date: 10/14/2020
helpviewer_keywords:
- MSBuild overview
ms.openlocfilehash: e99b9a428d9c6149debc06e1dfab7a69c3590196
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924394"
---
# <a name="msbuild-internals-for-c-projects"></a>Composants internes MSBuild pour les projets C++

Quand vous définissez des propriétés de projet dans l’IDE et enregistrez le projet, Visual Studio écrit les paramètres du projet dans votre fichier projet. Le fichier projet contient des paramètres qui sont uniques à votre projet. Toutefois, il ne contient pas tous les paramètres requis pour générer votre projet. Le fichier projet contient des éléments `Import` qui incluent un réseau d’autres *fichiers de support* . Les fichiers de support contiennent les propriétés, cibles et paramètres restants nécessaires pour générer le projet.

La plupart des cibles et propriétés dans les fichiers de support ont pour seul but d’implémenter le système de build. Cet article présente les cibles et les propriétés utiles que vous pouvez spécifier sur la ligne de commande MSBuild. Pour découvrir d’autres cibles et propriétés, explorez les fichiers dans les répertoires des fichiers de support.

## <a name="support-file-directories"></a>Répertoires des fichiers de support

Par défaut, les principaux fichiers de support Visual Studio sont situés dans les répertoires suivants. Ces informations sont spécifiques à la version.

::: moniker range=">=msvc-160"

### <a name="visual-studio-2019"></a>Visual Studio 2019

- *`%VSINSTALLDIR%MSBuild\Microsoft\VC\<version>\`*

  Contient les principaux fichiers cibles (.targets) et fichiers de propriétés (.props) qui sont utilisés par les cibles. Par défaut, la macro $(VCTargetsPath) référence ce répertoire. L' *`<version>`* espace réservé fait référence à la version de Visual Studio : V160 pour Visual studio 2019, V150 pour Visual studio 2017.

- *`%VSINSTALLDIR%MSBuild\Microsoft\VC\<version>\Platforms\<platform>\`*

  Contient les fichiers cibles et de propriétés spécifiques à la plateforme qui remplacent les cibles et propriétés dans le répertoire parent. Ce répertoire contient également une DLL qui définit les tâches qui sont utilisées par les cibles dans ce répertoire. L' *`<platform>`* espace réservé représente le sous-répertoire ARM, ARM64, Win32 ou x64.

- *`%VSINSTALLDIR%MSBuild\Microsoft\VC\<version>\Platforms\<platform>\PlatformToolsets\<toolset>\`*

  Contient les répertoires qui permettent à la build de générer des applications C++ à l’aide du spécifié *`<toolset>`* . L' *`<platform>`* espace réservé représente le sous-répertoire ARM, ARM64, Win32 ou x64. L' *`<toolset>`* espace réservé représente le sous-répertoire de l’ensemble d’outils.

::: moniker-end

::: moniker range=">=msvc-150"

### <a name="visual-studio-2017"></a>Visual Studio 2017

- *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\`*

  Contient les fichiers cibles principaux ( *`.targets`* ) et les fichiers de propriétés ( *`.props`* ) utilisés par les cibles. Par défaut, la `$(VCTargetsPath)` macro fait référence à ce répertoire.

- *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\Platforms\<platform>\`*

  Contient les fichiers cibles et de propriétés spécifiques à la plateforme qui remplacent les cibles et propriétés dans le répertoire parent. Ce répertoire contient également une DLL qui définit les tâches qui sont utilisées par les cibles dans ce répertoire. L' *`<platform>`* espace réservé représente le sous-répertoire ARM, ARM64, Win32 ou x64.

- *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\Platforms\<platform>\PlatformToolsets\<toolset>\`*

  Contient les répertoires qui permettent à la build de générer des applications C++ à l’aide du spécifié *`<toolset>`* . L' *`<platform>`* espace réservé représente le sous-répertoire ARM, Win32 ou x64. L' *`<toolset>`* espace réservé représente le sous-répertoire de l’ensemble d’outils.

::: moniker-end

### <a name="visual-studio-2015-and-earlier"></a>Visual Studio 2015 et versions antérieures

- *`<drive>:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\<version>\`*

  Contient les principaux fichiers cibles (.targets) et fichiers de propriétés (.props) qui sont utilisés par les cibles. Par défaut, la macro $(VCTargetsPath) référence ce répertoire.

- *`<drive>:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\<version>\Platforms\<platform>\`*

  Contient les fichiers cibles et de propriétés spécifiques à la plateforme qui remplacent les cibles et propriétés dans le répertoire parent. Ce répertoire contient également une DLL qui définit les tâches qui sont utilisées par les cibles dans ce répertoire. L' *`<platform>`* espace réservé représente le sous-répertoire ARM, Win32 ou x64.

- *`<drive>:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\<version>\Platforms\<platform>\PlatformToolsets\<toolset>\`*

  Contient les répertoires qui permettent à la build de générer des applications C++ à l’aide du spécifié *`<toolset>`* . L' *`<version>`* espace réservé est V110 pour Visual studio 2012, V120 pour Visual Studio 2013 et V140 pour Visual studio 2015. L' *`<platform>`* espace réservé représente le sous-répertoire ARM, Win32 ou x64. L' *`<toolset>`* espace réservé représente le sous-répertoire de l’ensemble d’outils. Par exemple, il s’agit de V140 pour la création d’applications Windows à l’aide de l’ensemble d’outils Visual Studio 2015. Ou v120_xp pour générer Windows XP à l’aide de l’ensemble d’outils Visual Studio 2013.

- *`<drive>:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\Platforms\<platform>\PlatformToolsets\<toolset>\`*

  Les chemins d’accès qui permettent à la build de générer des applications Visual Studio 2008 ou Visual Studio 2010 n’incluent pas *`<version>`* . Dans ces versions, l' *`<platform>`* espace réservé représente le sous-répertoire Itanium, Win32 ou x64. L' *`<toolset>`* espace réservé représente le sous-répertoire de l’ensemble d’outils V90 ou V100.

## <a name="support-files"></a>Fichiers de support

Les répertoires des fichiers de support contiennent des fichiers avec les extensions suivantes :

| Extension | Description |
| --------- | ----------- |
| *`.targets`* | Contient des éléments XML `Target` qui spécifient les tâches qui sont exécutées par la cible. Peut également contenir des éléments `PropertyGroup`, `ItemGroup`, `ItemDefinitionGroup` et `Item` définis par l’utilisateur qui sont utilisés pour assigner des fichiers et des options de ligne de commande aux paramètres de tâche.<br /><br /> Pour plus d’informations, consultez [Target, élément (MSBuild)](/visualstudio/msbuild/target-element-msbuild). |
| *`.props`* | Contient des éléments XML `Property` définis par l’utilisateur et `Property Group` qui spécifient des paramètres de fichier et des paramètres qui sont utilisés pendant une génération.<br /><br /> Peut également contenir des éléments XML `Item` définis par l’utilisateur et `ItemDefinitionGroup` qui spécifient des paramètres supplémentaires. Les éléments définis dans un groupe de définitions d’éléments sont similaires aux propriétés, mais ils ne sont pas accessibles à partir de la ligne de commande. Les fichiers projet Visual Studio utilisent fréquemment des éléments au lieu de propriétés pour représenter les paramètres.<br /><br /> Pour plus d’informations, consultez [ItemGroup, élément (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild), [ItemDefinitionGroup, élément (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild)et [Item, élément (MSBuild)](/visualstudio/msbuild/item-element-msbuild). |
| *`.xml`* | Contient des éléments XML qui déclarent et initialisent des éléments de l’interface utilisateur IDE. Par exemple, les feuilles de propriétés, les pages de propriétés, les contrôles TextBox et les contrôles ListBox.<br /><br /> Les *`.xml`* fichiers prennent directement en charge l’IDE, et non MSBuild. Toutefois, les valeurs des propriétés IDE sont assignées pour générer des propriétés et des éléments.<br /><br /> La plupart des *`.xml`* fichiers se trouvent dans un sous-répertoire spécifique aux paramètres régionaux. Par exemple, les fichiers de la région anglais (États-Unis) se trouvent dans `$(VCTargetsPath)\1033\` . |

## <a name="user-targets-and-properties"></a>Cibles et propriétés utilisateur

Pour utiliser MSBuild efficacement, il est utile de connaître les propriétés et les cibles qui sont utiles et pertinentes. La plupart des propriétés et des cibles permettent d’implémenter le système de génération Visual Studio et ne sont donc pas pertinentes pour l’utilisateur. Cette section décrit les propriétés et les cibles orientées utilisateur qui méritent de connaître.

### <a name="platformtoolset-property"></a>Propriété`PlatformToolset`

La propriété `PlatformToolset` identifie l’ensemble d’outils MSVC utilisé dans la génération. Par défaut, l’ensemble d’outils actuel est utilisé. Quand cette propriété est définie, sa valeur est concaténée avec des chaînes littérales pour former le chemin d’accès. Il s’agit du répertoire qui contient la propriété et les fichiers cibles requis pour générer un projet pour une plateforme particulière. L’ensemble d’outils de plateforme doit être installé pour générer à l’aide de cette version d’ensemble d’outils de plateforme.

Par exemple, affectez à la propriété `PlatformToolset` la valeur `v140` afin d’utiliser les bibliothèques et les outils Visual Studio 2015 pour générer votre application :

`msbuild myProject.vcxproj /p:PlatformToolset=v140`

### <a name="preferredtoolarchitecture-property"></a>Propriété`PreferredToolArchitecture`

La propriété `PreferredToolArchitecture` détermine si les outils et le compilateur 32 bits ou 64 bits sont utilisés dans la génération. Cette propriété n’affecte pas l’architecture ou la configuration de la plateforme de sortie. Par défaut, MSBuild utilise la version x86 du compilateur et des outils si cette propriété n’est pas définie.

Par exemple, affectez à la propriété `PreferredToolArchitecture` la valeur `x64` afin d’utiliser les outils et le compilateur 64 bits pour générer votre application :

`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="useenv-property"></a>Propriété`UseEnv`

Par défaut, les paramètres spécifiques à la plateforme pour le projet actuel substituent les variables d’environnement PATH, INCLUDE, LIB, LIBPATH, CONFIGURATION et PLATFORM. Affectez à la propriété la valeur `UseEnv` **`true`** pour garantir que les variables d’environnement ne sont pas remplacées.

> `msbuild myProject.vcxproj /p:UseEnv=true`

### <a name="targets"></a>Cibles

Il existe des centaines de cibles dans les fichiers de support Visual Studio. Toutefois, la plupart sont des cibles orientées système que l’utilisateur peut ignorer. La plupart des cibles système sont précédées d’un trait de soulignement ( `_` ), ou portent un nom qui commence par `PrepareFor` , `Compute` , `Before` ,, `After` `Pre` ou `Post` .

Le tableau suivant liste plusieurs cibles orientées utilisateur utiles.

| Cible | Description |
| ------ | ----------- |
| BscMake | Exécute l’outil Microsoft Browse Information Maintenance Utility, bscmake.exe. |
| Build | Génère le projet.<br /><br /> Cette cible est la valeur par défaut pour un projet. |
| ClCompile | Exécute l’outil Compilateur MSVC, cl.exe. |
| Clean | Supprime les fichiers de génération temporaires et intermédiaires. |
| Lib | Exécute l’outil Gestionnaire de bibliothèques 32 bits de Microsoft, lib.exe. |
| Lien | Exécute l’outil Éditeur de liens MSVC, link.exe. |
| ManifestResourceCompile | Extrait une liste de ressources à partir d’un manifeste, puis exécute l’outil Compilateur de ressources Microsoft Windows, rc.exe. |
| Midl | Exécute l’outil Compilateur MIDL (Microsoft Interface Definition Language), midl.exe. |
| Reconstruire | Nettoie, puis génère votre projet. |
| ResourceCompile | Exécute l’outil Compilateur de ressources Microsoft Windows, rc.exe. |
| XdcMake | Exécute l’outil Documentation XML, xdcmake.exe. |
| Xsd | Exécute l’outil XML Schema Definition, xsd.exe. *Consultez la remarque.* |

> [!NOTE]
> Dans Visual Studio 2017 et ultérieur, les fichiers **xsd** ne sont plus pris en charge par les projets C++. Vous pouvez toujours utiliser **Microsoft.VisualC.CppCodeProvider** en ajoutant **CppCodeProvider.dll** manuellement au GAC.

## <a name="see-also"></a>Voir aussi

[Référence des tâches MSBuild](/visualstudio/msbuild/msbuild-task-reference)\
[BscMake, tâche](/visualstudio/msbuild/bscmake-task)\
[CL (tâche)](/visualstudio/msbuild/cl-task)\
[Tâche CPPClean,](/visualstudio/msbuild/cppclean-task)\
[LIB, tâche](/visualstudio/msbuild/lib-task)\
[Lier la tâche](/visualstudio/msbuild/link-task)\
[MIDL, tâche](/visualstudio/msbuild/midl-task)\
[MT, tâche](/visualstudio/msbuild/mt-task)\
[RC, tâche](/visualstudio/msbuild/rc-task)\
[SetEnv, tâche](/visualstudio/msbuild/setenv-task)\
[Tâche VCMessage,](/visualstudio/msbuild/vcmessage-task)\
[XDCMake, tâche](/visualstudio/msbuild/xdcmake-task)
