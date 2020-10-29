---
title: 'Procédure pas à pas : utilisation de MSBuild pour créer un projet Visual Studio C++'
description: Procédure pas à pas qui montre comment créer un projet MSBuild C++. vcxproj en ligne de commande à partir de zéro.
ms.date: 10/08/2020
helpviewer_keywords:
- 'MSBuild (C++), walkthrough: create a project'
ms.openlocfilehash: b3d4e8881f926e80e95832a27f7a5106ce876265
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924331"
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>Procédure pas à pas : utilisation de MSBuild pour créer un projet Visual C++

Cette procédure pas à pas montre comment utiliser MSBuild dans une invite de commandes pour générer un projet Visual Studio C++. Vous allez apprendre à créer un *`.vcxproj`* fichier projet XML pour une application console Visual C++. Après avoir généré le projet, vous allez découvrir comment personnaliser le processus de build.

> [!IMPORTANT]
> N’utilisez pas cette approche si vous envisagez de modifier le fichier projet ultérieurement à l’aide de l’IDE de Visual Studio. Si vous créez un *`.vcxproj`* fichier manuellement, l’IDE de Visual Studio peut ne pas être en mesure de le modifier ou de le charger, en particulier si le projet utilise des caractères génériques dans les éléments de projet. Pour plus d’informations, consultez [ `.vcxproj` et `.props` structure](./reference/vcxproj-file-structure.md) de fichiers et [ `.vcxproj` fichiers et caractères génériques](./reference/vcxproj-files-and-wildcards.md).

Cette procédure pas à pas décrit les tâches suivantes :

- Création des fichiers sources C++ de votre projet.

- Création du fichier projet XML MSBuild.

- Génération du projet à l’aide de MSBuild.

- Personnalisation du projet à l’aide de MSBuild.

## <a name="prerequisites"></a>Conditions préalables requises

Pour effectuer cette procédure pas à pas, vous avez besoin des conditions préalables suivantes :

- Une copie de Visual Studio 2019 avec la charge de travail **Développement Desktop en C++** installée.

- Une compréhension générale du système MSBuild.

::: moniker range="msvc-140"

> [!NOTE]
> La plupart des instructions de génération de bas niveau sont contenues dans les *`.targets`* *`.props`* fichiers et qui sont définis dans le dossier cibles par défaut, stocké dans la propriété `$(VCTargetsPath)` . C’est là que vous trouverez des fichiers tels que *`Microsoft.Cpp.Common.props`* . Le chemin d’accès par défaut de ces fichiers dans Visual Studio 2015 et versions antérieures est sous *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\`* .

::: moniker-end

::: moniker range="msvc-150"

> [!NOTE]
> La plupart des instructions de génération de bas niveau sont contenues dans les *`.targets`* *`.props`* fichiers et qui sont définis dans le dossier cibles par défaut, stocké dans la propriété `$(VCTargetsPath)` . C’est là que vous trouverez des fichiers tels que *`Microsoft.Cpp.Common.props`* . Le chemin d’accès par défaut de ces fichiers dans Visual Studio 2017 est sous *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\`* . Visual Studio 2015 et les versions antérieures les stockaient sous *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\`* .

::: moniker-end

::: moniker range=">=msvc-160"

> [!NOTE]
> La plupart des instructions de génération de bas niveau sont contenues dans les *`.targets`* *`.props`* fichiers et qui sont définis dans le dossier cibles par défaut, stocké dans la propriété `$(VCTargetsPath)` . C’est là que vous trouverez des fichiers tels que *`Microsoft.Cpp.Common.props`* . Le chemin d’accès par défaut de ces fichiers est sous *`%VSINSTALLDIR%MSBuild\Microsoft\VC\<version>\`* . L' `<version>` élément Path est spécifique à la version de Visual Studio. Il s’agit *`v160`* de Visual Studio 2019. Visual Studio 2017 stockait ces fichiers sous *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\`* . Visual Studio 2015 et les versions antérieures les stockaient sous *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\`* .

::: moniker-end

## <a name="create-the-c-source-files"></a>Créer les fichiers sources C++

Dans cette procédure pas à pas, vous allez créer un projet constitué d’un fichier source et d’un fichier d’en-tête. Le fichier source *`main.cpp`* contient la `main` fonction pour l’application console. Le fichier d’en-tête *`main.h`* contient du code pour inclure le *`<iostream>`* fichier d’en-tête. Vous pouvez créer ces fichiers C++ à l’aide de Visual Studio ou d’un éditeur de texte comme Visual Studio Code.

### <a name="to-create-the-c-source-files-for-your-project"></a>Pour créer les fichiers sources C++ de votre projet

1. Créez un dossier pour votre projet.

1. Créez un fichier nommé *`main.cpp`* et ajoutez le code suivant au fichier :

    ```cpp
    // main.cpp : the application source code.
    #include <iostream>
    #include "main.h"
    int main()
    {
       std::cout << "Hello, from MSBuild!\n";
       return 0;
    }
    ```

1. Créez un fichier nommé *`main.h`* et ajoutez le code suivant au fichier :

    ```cpp
    // main.h: the application header code.
    /* Additional source code to include. */
    ```

## <a name="creating-the-xml-msbuild-project-file"></a>Création du fichier projet XML MSBuild

Un fichier projet MSBuild est un fichier XML qui contient un élément racine de projet (`<Project>`). Dans l’exemple de projet que vous allez générer, l' `<Project>` élément contient sept éléments enfants :

- Trois balises de groupe d’éléments (`<ItemGroup>`) qui spécifient la configuration et la plateforme du projet, le nom du fichier source et le nom du fichier d’en-tête.

- Trois balises d’importation (`<Import>`) qui spécifient l’emplacement des paramètres de Microsoft Visual C++.

- Une balise de groupe de propriétés (`<PropertyGroup>`) qui spécifie les paramètres du projet.

### <a name="to-create-the-msbuild-project-file"></a>Pour créer le fichier projet MSBuild

1. Utilisez un éditeur de texte pour créer un fichier projet nommé *`myproject.vcxproj`* , puis ajoutez l' `<Project>` élément racine indiqué ici. (Utilisez `ToolsVersion="14.0"` si vous utilisez Visual studio 2015, `ToolsVersion="15.0"` si vous utilisez visual studio 2017 ou `ToolsVersion="16.0"` si vous utilisez Visual Studio 2019.)

    ```xml
    <Project DefaultTargets="Build" ToolsVersion="16.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

   Insérez les éléments dans les étapes de la procédure suivante entre les `<Project>` balises racine.

1. Ajoutez ces deux `<ProjectConfiguration>` éléments enfants dans un `<ItemGroup>` élément. L’élément enfant spécifie les configurations Debug et Release pour un système d’exploitation Windows 32 bits :

    ```xml
    <ItemGroup>
      <ProjectConfiguration Include="Debug|Win32">
        <Configuration>Debug</Configuration>
        <Platform>Win32</Platform>
      </ProjectConfiguration>
      <ProjectConfiguration Include="Release|Win32">
        <Configuration>Release</Configuration>
        <Platform>Win32</Platform>
      </ProjectConfiguration>
    </ItemGroup>
    ```

1. Ajoutez un `<Import>` élément qui spécifie le chemin d’accès des paramètres C++ par défaut pour ce projet :

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
    ```

1. Ajoutez un élément de groupe de propriétés ( `<PropertyGroup>` ) qui spécifie deux propriétés de projet, `<ConfigurationType>` et `<PlatformToolset>` . (Utilisez `v140` comme `<PlatformToolset>` valeur si vous utilisez visual studio 2015, `v141` si vous utilisez Visual Studio 2017 ou `v142` si vous utilisez Visual Studio 2019.)

    ```xml
    <PropertyGroup>
      <ConfigurationType>Application</ConfigurationType>
      <PlatformToolset>v142</PlatformToolset>
    </PropertyGroup>
    ```

1. Ajoutez un `<Import>` élément qui spécifie le chemin d’accès des paramètres C++ actuels pour ce projet :

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
    ```

1. Ajoutez un `<ClCompile>` élément enfant dans un `<ItemGroup>` élément. L’élément enfant spécifie le nom du fichier source C/C++ à compiler :

    ```xml
    <ItemGroup>
      <ClCompile Include="main.cpp" />
    </ItemGroup>
    ```

   > [!NOTE]
   > `<ClCompile>` est une *cible de génération* et est définie dans le dossier cibles par défaut.

1. Ajoutez un `<ClInclude>` élément enfant dans un `<ItemGroup>` élément. L’élément enfant spécifie le nom du fichier d’en-tête pour le fichier source C/C++ :

    ```xml
    <ItemGroup>
      <ClInclude Include="main.h" />
    </ItemGroup>
    ```

1. Ajoutez un `<Import>` élément qui spécifie le chemin d’accès du fichier qui définit la cible de ce projet :

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
    ```

### <a name="complete-project-file"></a>Fichier projet complet

Ce code montre le fichier de projet complet que vous avez créé dans la procédure précédente. (Utilisez `ToolsVersion="15.0"` pour Visual studio 2017 ou `ToolsVersion="14.0"` pour visual studio 2015.)

```xml
<Project DefaultTargets="Build" ToolsVersion="16.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <ProjectConfiguration Include="Debug|Win32">
      <Configuration>Debug</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
    <ProjectConfiguration Include="Release|Win32">
      <Configuration>Release</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
  </ItemGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
  <PropertyGroup>
    <ConfigurationType>Application</ConfigurationType>
    <PlatformToolset>v142</PlatformToolset>
  </PropertyGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
  <ItemGroup>
    <ClCompile Include="main.cpp" />
  </ItemGroup>
  <ItemGroup>
    <ClInclude Include="main.h" />
  </ItemGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
</Project>
```

## <a name="using-msbuild-to-build-your-project"></a>Générer votre projet à l’aide de MSBuild

Entrez cette commande à l’invite de commandes pour générer votre application console :

> `msbuild myproject.vcxproj /p:configuration=debug`

MSBuild crée un dossier pour les fichiers de sortie, puis compile et lie votre projet pour générer le *`Myproject.exe`* programme. Une fois le processus de génération terminé, utilisez cette commande pour exécuter l’application à partir du dossier de débogage :

> `myproject`

L’application doit afficher « Hello, from MSBuild! » dans la fenêtre de console.

## <a name="customizing-your-project"></a>Personnalisation de votre projet

MSBuild vous permet d’exécuter des cibles de build prédéfinies, d’appliquer des propriétés définies par l’utilisateur et d’utiliser des outils, des événements et des étapes de build personnalisés. Cette section présente les tâches suivantes :

- Utilisation de MSBuild avec des cibles de build.

- Utilisation de MSBuild avec des propriétés de build.

- Utilisation de MSBuild avec les outils et le compilateur 64 bits.

- Utilisation de MSBuild avec des ensembles d’outils différents.

- Ajout de personnalisations MSBuild.

### <a name="using-msbuild-with-build-targets"></a>Utilisation de MSBuild avec des cibles de build

Un *cible de build* est un jeu nommé de commandes prédéfinies ou définies par l’utilisateur qui peuvent être exécutées pendant la génération. Utilisez l’option de ligne de commande cible ( **`/t`** ) pour spécifier une cible de génération. Pour l' `myproject` exemple de projet, la cible prédéfinie **`clean`** supprime tous les fichiers dans le dossier de débogage et crée un nouveau fichier journal.

À l’invite de commandes, entrez cette commande pour nettoyer `myproject` :

> `msbuild myproject.vcxproj /t:clean`

### <a name="using-msbuild-with-build-properties"></a>Utilisation de MSBuild avec des propriétés de build

L’option de ligne de commande de propriété (`/p`) vous permet de remplacer une propriété dans votre fichier de build de projet. Dans l’exemple de projet `myproject`, la configuration de build Release ou Debug est spécifiée par la propriété `Configuration`. Le système d’exploitation que vous utiliserez pour exécuter l’application générée est spécifié par la `Platform` propriété.

À l’invite de commandes, entrez la commande suivante pour créer une version Debug de l' `myproject` application à exécuter sur Windows 32 bits :

> `msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`

Supposez que l’exemple de projet `myproject` définit aussi une configuration pour Windows 64 bits et une autre configuration pour un système d’exploitation personnalisé nommé `myplatform`.

À l’invite de commandes, entrez la commande suivante pour créer une version Release qui s’exécute sur Windows 64 bits :

> `msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`

À l’invite de commandes, entrez la commande suivante pour créer une version Release pour `myplatform` :

> `msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`

### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>Utilisation de MSBuild avec les outils et le compilateur 64 bits

Si vous avez installé Visual Studio sur Windows 64 bits, les outils natif et croisé de 64 bits sont installés par défaut. Vous pouvez configurer MSBuild pour générer votre application à l’aide des outils et du compilateur 64 bits en définissant la propriété `PreferredToolArchitecture`. Cette propriété n’affecte pas la configuration du projet ou les propriétés de la plateforme. Par défaut, la version 32 bits des outils est utilisée. Pour spécifier la version 64 bits du compilateur et des outils, ajoutez cet élément de groupe de propriétés au *`Myproject.vcxproj`* fichier projet après l' *`Microsoft.Cpp.default.props`* `<Import />` élément file :

```xml
<PropertyGroup>
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>
</PropertyGroup>
```

À l’invite de commandes, entrez la commande suivante pour utiliser les outils 64 bits pour générer votre application :

> `msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="using-msbuild-with-a-different-toolset"></a>Utilisation de MSBuild avec un ensemble d’outils différent

Si vous disposez des ensembles d’outils et de bibliothèques d’autres versions de Visual C++, MSBuild peut générer des applications pour la version actuelle de Visual C++ ou pour les autres versions installées. Par exemple, si vous avez installé Visual Studio 2012, pour spécifier l’ensemble d’outils Visual C++ 11,0 pour Windows XP, ajoutez cet élément de groupe de propriétés au *`Myproject.vcxproj`* fichier projet après l' *`Microsoft.Cpp.props`* `<Import />` élément file :

```xml
<PropertyGroup>
    <PlatformToolset>v110_xp</PlatformToolset>
</PropertyGroup>
```

Pour régénérer votre projet avec l’ensemble d’outils Visual C++ 11,0 de Windows XP, entrez la commande suivante :

> `msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`

### <a name="adding-msbuild-customizations"></a>Ajout de personnalisations MSBuild

MSBuild vous permet de personnaliser votre processus de build de différentes façons. Ces articles montrent comment ajouter des étapes de génération personnalisée, des outils et des événements à votre projet MSBuild :

- [Comment : ajouter une étape de génération personnalisée à des projets MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)

- [Comment : ajouter des outils de génération personnalisée à des projets MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)

- [Comment : utiliser des événements de build dans des projets MSBuild](how-to-use-build-events-in-msbuild-projects.md)
