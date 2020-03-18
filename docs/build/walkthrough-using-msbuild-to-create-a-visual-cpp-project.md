---
title: 'Procédure pas à pas : utilisation de MSBuild pour créer un projet Visual C++'
ms.date: 05/16/2019
helpviewer_keywords:
- 'msbuild (c++), walkthrough: create a project'
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
ms.openlocfilehash: c93867f3be3b17f703c549aa5c05f3d327934c26
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417186"
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>Procédure pas à pas : utilisation de MSBuild pour créer un projet Visual C++

Cette procédure pas à pas montre comment utiliser MSBuild pour générer un projet Visual Studio C++ dans une invite de commandes. Vous allez découvrir comment créer les fichiers sources C++ et un fichier projet XML pour une application console Visual C++. Après avoir généré le projet, vous allez découvrir comment personnaliser le processus de build.

Cette procédure pas à pas décrit les tâches suivantes :

- Création des fichiers sources C++ de votre projet.

- Création du fichier projet XML MSBuild.

- Génération du projet à l’aide de MSBuild.

- Personnalisation du projet à l’aide de MSBuild.

## <a name="prerequisites"></a>Conditions préalables requises

Les éléments suivants sont nécessaires pour effectuer cette procédure pas à pas :

- Une copie de Visual Studio 2019 avec la charge de travail **Développement Desktop en C++** installée.

- Une compréhension générale du système MSBuild.

> [!NOTE]
> Évitez cette approche si vous prévoyez de modifier le fichier projet par la suite à l’aide de l’IDE Visual Studio. Si vous créez un fichier .vcxproj manuellement, l’IDE Visual Studio ne pourra peut-être pas le modifier ou le charger, surtout si le projet utilise des caractères génériques dans les éléments de projet.

> [!NOTE]
> La plupart des instructions de génération de bas niveau sont contenues dans les fichiers **.targets** et **.props** définis dans le répertoire VCTargets, qui est stocké dans la propriété `$(VCTargetsPath)`. Le chemin par défaut de ces fichiers dans Visual Studio 2019 Enterprise Edition est C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\MSBuild\Microsoft\VC\v160\Microsoft.Cpp.Common.props.

## <a name="creating-the-c-source-files"></a>Création des fichiers sources C++

Dans cette procédure pas à pas, vous allez créer un projet constitué d’un fichier source et d’un fichier d’en-tête. Le fichier source main.cpp contient la fonction principale de l’application console. Le fichier d’en-tête main.h contient le code pour inclure le fichier d’en-tête iostream. Vous pouvez créer ces fichiers C++ à l’aide de Visual Studio ou d’un éditeur de texte comme Visual Studio Code.

### <a name="to-create-the-c-source-files-for-your-project"></a>Pour créer les fichiers sources C++ de votre projet

1. Créez un répertoire pour votre projet.

1. Créez un fichier sous le nom main.cpp et ajoutez le code suivant à ce fichier :

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

1. Créez un fichier sous le nom main.h et ajoutez le code suivant à ce fichier :

    ```cpp
    // main.h: the application header code.
    /* Additional source code to include. */
    ```

## <a name="creating-the-xml-msbuild-project-file"></a>Création du fichier projet XML MSBuild

Un fichier projet MSBuild est un fichier XML qui contient un élément racine de projet (`<Project>`). Dans l’exemple de projet suivant, l’élément `<Project>` contient sept éléments enfants :

- Trois balises de groupe d’éléments (`<ItemGroup>`) qui spécifient la configuration et la plateforme du projet, le nom du fichier source et le nom du fichier d’en-tête.

- Trois balises d’importation (`<Import>`) qui spécifient l’emplacement des paramètres de Microsoft Visual C++.

- Une balise de groupe de propriétés (`<PropertyGroup>`) qui spécifie les paramètres du projet.

### <a name="to-create-the-msbuild-project-file"></a>Pour créer le fichier projet MSBuild

1. Utilisez un éditeur de texte pour créer un fichier projet sous le nom `myproject.vcxproj`, puis ajoutez l’élément `<Project>` racine suivant. Insérez les éléments dans les étapes de procédure suivantes entre les balises `<Project>` racines. (Utilisez ToolsVersion="15.0" si vous utilisez Visual Studio 2017 ou ToolsVersion="16.0" si vous utilisez Visual Studio 2019.)

    ```xml
    <Project DefaultTargets="Build" ToolsVersion="16.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

1. Ajoutez les deux éléments enfants `<ProjectConfiguration>` suivants dans un élément `<ItemGroup>`. L’élément enfant spécifie les configurations Debug et Release pour un système d’exploitation Windows 32 bits :

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

1. Ajoutez l’élément `<Import>` suivant qui spécifie le chemin des paramètres C++ par défaut pour ce projet :

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
    ```

1. Ajoutez l’élément de groupe de propriétés (`<PropertyGroup>`) qui spécifie deux propriétés de projet. (Utilisez v141 si vous utilisez Visual Studio 2017 ou v142 si vous utilisez Visual Studio 2019.)

    ```xml
    <PropertyGroup>
      <ConfigurationType>Application</ConfigurationType>
      <PlatformToolset>v142</PlatformToolset>
    </PropertyGroup>
    ```

1. Ajoutez l’élément `<Import>` suivant qui spécifie le chemin des paramètres C++ actuels pour ce projet :

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
    ```

1. Ajoutez l’élément enfant `<ClCompile>` suivant dans un élément `<ItemGroup>`. L’élément enfant spécifie le nom du fichier source C/C++ à compiler :

    ```xml
    <ItemGroup>
      <ClCompile Include="main.cpp" />
    </ItemGroup>
    ```

   > [!NOTE]
   > `<ClCompile>` est une *cible de build* et est défini dans le répertoire **VCTargets**.

1. Ajoutez l’élément enfant `<ClInclude>` suivant dans un élément `<ItemGroup>`. L’élément enfant spécifie le nom du fichier d’en-tête pour le fichier source C/C++ :

    ```xml
    <ItemGroup>
      <ClInclude Include="main.h" />
    </ItemGroup>
    ```

1. Ajoutez l’élément `<Import>` suivant qui spécifie le chemin du fichier qui définit la cible pour ce projet :

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
    ```

### <a name="complete-project-file"></a>Fichier projet complet

Le code suivant affiche le fichier projet complet que vous avez créé dans la procédure précédente. (Utilisez ToolsVersion="15.0" pour Visual Studio 2017.)

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

Tapez la commande suivante à l’invite de commandes pour générer votre application console :

`msbuild myproject.vcxproj /p:configuration=debug`

MSBuild crée un répertoire pour les fichiers de sortie, puis compile et lie votre projet pour générer le programme Myproject.exe. Une fois le processus de build terminé, utilisez la commande suivante pour exécuter l’application à partir du dossier de débogage :

`myproject`

L’application doit afficher « Hello, from MSBuild! » dans la fenêtre de console.

## <a name="customizing-your-project"></a>Personnalisation de votre projet

MSBuild vous permet d’exécuter des cibles de build prédéfinies, d’appliquer des propriétés définies par l’utilisateur et d’utiliser des outils, des événements et des étapes de build personnalisés. Cette section illustre les tâches suivantes :

- Utilisation de MSBuild avec des cibles de build.

- Utilisation de MSBuild avec des propriétés de build.

- Utilisation de MSBuild avec les outils et le compilateur 64 bits.

- Utilisation de MSBuild avec des ensembles d’outils différents.

- Ajout de personnalisations MSBuild.

### <a name="using-msbuild-with-build-targets"></a>Utilisation de MSBuild avec des cibles de build

Un *cible de build* est un jeu nommé de commandes prédéfinies ou définies par l’utilisateur qui peuvent être exécutées pendant la génération. Utilisez l’option de ligne de commande cible (`/t`) pour spécifier une cible de build. Pour l’exemple de projet `myproject`, la cible **clean** prédéfinie supprime tous les fichiers du dossier de débogage et crée un fichier journal.

À l'invite de commandes, tapez la commande suivante pour nettoyer `myproject`.

`msbuild myproject.vcxproj /t:clean`

### <a name="using-msbuild-with-build-properties"></a>Utilisation de MSBuild avec des propriétés de build

L’option de ligne de commande de propriété (`/p`) vous permet de remplacer une propriété dans votre fichier de build de projet. Dans l’exemple de projet `myproject`, la configuration de build Release ou Debug est spécifiée par la propriété `Configuration`. Et le système d’exploitation qui est censé exécuter l’application générée est spécifié par la propriété `Platform`.

À l’invite de commandes, tapez la commande suivante pour créer une build Debug de l’application `myproject` qui est censée s’exécuter sur Windows 32 bits.

`msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`

Supposez que l’exemple de projet `myproject` définit aussi une configuration pour Windows 64 bits et une autre configuration pour un système d’exploitation personnalisé nommé `myplatform`.

À l’invite de commandes, tapez la commande suivante pour créer une build Release qui s’exécute sur Windows 64 bits.

`msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`

À l’invite de commandes, tapez la commande suivante pour créer une build Release pour `myplatform`.

`msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`

### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>Utilisation de MSBuild avec les outils et le compilateur 64 bits

Si vous avez installé Visual Studio sur Windows 64 bits, par défaut, les outils croisés et natifs x64 64 bits sont installés. Vous pouvez configurer MSBuild pour générer votre application à l’aide des outils et du compilateur 64 bits en définissant la propriété `PreferredToolArchitecture`. Cette propriété n’affecte pas la configuration du projet ou les propriétés de la plateforme. Par défaut, la version 32 bits des outils est utilisée. Pour spécifier la version 64 bits du compilateur et des outils, ajoutez l’élément de groupe de propriétés suivant au fichier projet MyProject. vcxproj après l' `Microsoft.Cpp.default.props` \<élément import/>:

```xml
<PropertyGroup>
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>
</PropertyGroup>
```

À l’invite de commandes, tapez la commande suivante pour générer votre application à l’aide des outils 64 bits.

`msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="using-msbuild-with-a-different-toolset"></a>Utilisation de MSBuild avec un ensemble d’outils différent

Si vous disposez des ensembles d’outils et de bibliothèques d’autres versions de Visual C++, MSBuild peut générer des applications pour la version actuelle de Visual C++ ou pour les autres versions installées. Par exemple, si vous avez installé Visual Studio 2012, pour spécifier l’ensemble C++ d’outils Visual 11,0 pour Windows XP, ajoutez l’élément de groupe de propriétés suivant au fichier projet MyProject. vcxproj après l' `Microsoft.Cpp.props` \<élément Import/>:

```xml
<PropertyGroup>
    <PlatformToolset>v110_xp</PlatformToolset>
</PropertyGroup>
```

Pour regénérer votre projet avec l’ensemble d’outils Visual C++ 11.0 pour Windows XP, tapez les commandes suivantes :

`msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`

### <a name="adding-msbuild-customizations"></a>Ajout de personnalisations MSBuild

MSBuild vous permet de personnaliser votre processus de build de différentes façons. Les rubriques suivantes montrent comment ajouter des étapes de build, des outils et des événements personnalisés à votre projet MSBuild :

- [Guide pratique pour ajouter une étape de génération personnalisée à des projets MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)

- [Guide pratique pour ajouter des outils de génération personnalisés à des projets MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)

- [Guide pratique pour utiliser des événements de build dans des projets MSBuild](how-to-use-build-events-in-msbuild-projects.md)
