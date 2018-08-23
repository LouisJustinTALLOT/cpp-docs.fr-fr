---
title: 'Procédure pas à pas : Utilisation de MSBuild pour créer un projet Visual C++ | Microsoft Docs'
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.walkthrough.createproject
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), walkthrough: create a project'
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8bb957f0ab1dd2ea7d05151257aee0e15561e8a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609697"
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>Procédure pas à pas : utilisation de MSBuild pour créer un projet Visual C++

Cette procédure pas à pas montre comment utiliser MSBuild pour générer un projet Visual C++ à l’invite de commande. Vous allez apprendre à créer des fichiers sources C++ et un fichier de projet basé sur XML pour une application de console Visual C++. Après avoir généré le projet, vous allez apprendre à personnaliser le processus de génération.

Cette procédure pas à pas décrit les tâches suivantes :

- Création des fichiers sources C++ pour votre projet.

- Création du fichier de projet XML MSBuild.

- Utilisation de MSBuild pour générer votre projet.

- Utilisation de MSBuild pour personnaliser votre projet.

## <a name="prerequisites"></a>Prérequis

Les éléments suivants sont nécessaires pour effectuer cette procédure pas à pas :

- Une copie de Visual Studio avec le **développement Desktop en C++** charge de travail installée.

- Une compréhension générale du système MSBuild.

> [!NOTE]
> N’utilisez pas cette approche si vous avez l’intention de modifier le fichier projet ultérieurement à l’aide de l’IDE Visual Studio. Si vous créez manuellement un fichier .vcxproj, l’IDE Visual Studio ne peut pas être en mesure de modifier ou de le charger, surtout si le projet utilise des caractères génériques dans les éléments de projet.

> [!NOTE]
> La plupart des instructions de génération de bas niveau est contenues dans le **.targets** et **.props** fichiers qui sont définis dans le répertoire VCTargets, stocké dans la propriété `$(VCTargetsPath)`. Le chemin d’accès par défaut de ces fichiers dans Visual Studio 2017 Enterprise Edition est C:\\Program Files (x86)\\Microsoft Visual Studio\\2017\\Enterprise\\Common7\\IDE\\ VC\\VCTargets\\.

## <a name="creating-the-c-source-files"></a>Création des fichiers sources C++

Dans cette procédure pas à pas, vous allez créer un projet qui a un fichier source et un fichier d’en-tête. Le fichier source main.cpp contient la fonction principale de l’application de console. Le fichier d’en-tête main.h contient le code pour inclure le fichier d’en-tête iostream. Vous pouvez créer ces fichiers C++ à l’aide de Visual Studio ou un message texte éditeur tel que Visual Studio Code.

### <a name="to-create-the-c-source-files-for-your-project"></a>Pour créer des fichiers sources C++ pour votre projet

1. Créez un répertoire pour votre projet.

2. Créez un fichier nommé main.cpp et ajoutez le code suivant à ce fichier :

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

3. Créez un fichier nommé main.h et ajoutez le code suivant à ce fichier :

    ```cpp
    // main.h: the application header code.
    /* Additional source code to include. */
    ```

## <a name="creating-the-xml-msbuild-project-file"></a>Création du fichier projet XML MSBuild

Un fichier projet MSBuild est un fichier XML qui contient un élément racine du projet (\<projet >). Dans l’exemple de projet, le \<projet > élément contient sept éléments enfants :

- Trois balises du groupe d’éléments (\<ItemGroup >) qui spécifient la configuration de projet et de plateforme, nom du fichier source et nom de fichier d’en-tête.

- Trois balises d’importation (\<Importer >) qui spécifient l’emplacement des paramètres de Microsoft Visual C++.

- Une balise de groupe de propriété (\<PropertyGroup >) qui spécifie les paramètres du projet.

### <a name="to-create-the-msbuild-project-file"></a>Pour créer le fichier de projet MSBuild

1. Utilisez un éditeur de texte pour créer un fichier de projet est nommé `myproject.vcxproj`, puis ajoutez la racine suivante \<projet > élément. Insérez les éléments dans les étapes suivantes entre la racine \<projet > balises :

    ```xml
    <Project DefaultTargets="Build" ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. Ajoutez les deux \<ProjectConfiguration > éléments enfants dans un \<ItemGroup > élément. L’élément enfant spécifie debug et release de configurations pour un système d’exploitation de Windows 32 bits :

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

3. Ajoutez le code suivant \<Import / > élément qui spécifie le chemin d’accès des paramètres C++ par défaut pour ce projet :

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
    ```

4. Ajoutez l’élément de groupe de propriétés suivant (\<PropertyGroup >) qui spécifie deux propriétés du projet :

    ```xml
    <PropertyGroup>
      <ConfigurationType>Application</ConfigurationType>
      <PlatformToolset>v141</PlatformToolset>
    </PropertyGroup>
    ```

5. Ajoutez le code suivant \<Import / > élément qui spécifie le chemin d’accès des paramètres C++ actuels pour ce projet :

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
    ```

6. Ajoutez le code suivant \<ClCompile > élément enfant dans un \<ItemGroup > élément. L’élément enfant spécifie le nom du fichier source C/C++ à compiler :

    ```xml
    <ItemGroup>
      <ClCompile Include="main.cpp" />
    </ItemGroup>
    ```

   > [!NOTE]
   > \<ClCompile > est un *cible de génération* et est défini dans le **VCTargets** directory.

7. Ajoutez le code suivant \<ClInclude > élément enfant dans un \<ItemGroup > élément. L’élément enfant spécifie le nom du fichier d’en-tête pour le fichier source C/C++ :

    ```xml
    <ItemGroup>
      <ClInclude Include="main.h" />
    </ItemGroup>
    ```

8. Ajoutez le code suivant \<importation > élément qui spécifie le chemin d’accès du fichier qui définit la cible pour ce projet :

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
    ```

### <a name="complete-project-file"></a>Fichier projet complet

Le code suivant montre le fichier projet complet que vous avez créé dans la procédure précédente.

```xml
<Project DefaultTargets="Build" ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
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
    <PlatformToolset>v141</PlatformToolset>
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

## <a name="using-msbuild-to-build-your-project"></a>À l’aide de MSBuild pour générer votre projet

Tapez la commande suivante à l’invite de commandes pour générer votre application de console :

`msbuild myproject.vcxproj /p:configuration=debug`

MSBuild crée un répertoire pour les fichiers de sortie, puis compile et lie votre projet pour générer le programme Myproject.exe. Une fois le processus de génération est terminée, utilisez la commande suivante pour exécuter l’application :

`myproject`

L’application doit afficher « Hello, from MSBuild ! » dans la fenêtre de console.

## <a name="customizing-your-project"></a>Personnalisation de votre projet

MSBuild permet d’exécuter des cibles de génération prédéfinies, appliquer des propriétés définies par l’utilisateur et utiliser des outils personnalisés, des événements et les étapes de génération. Cette section décrit les tâches suivantes :

- Utilisation de MSBuild avec des cibles de génération.

- Utilisation de MSBuild avec les propriétés de génération.

- Utilisation de MSBuild avec le compilateur 64 bits et outils.

- Utilisation de MSBuild avec différents ensembles d’outils.

- Ajout de personnalisations MSBuild.

### <a name="using-msbuild-with-build-targets"></a>Utilisation de MSBuild avec des cibles de génération

Un *cible de génération* est un jeu nommé de commandes prédéfinies ou définies par l’utilisateur qui peuvent être exécutées pendant la génération. Utilisez l’option de ligne de commande cible (**/t**) pour spécifier une cible de génération. Dans le cas de la `myproject` exemple de projet, prédéfinis **propre** cible supprime tous les fichiers dans le dossier de débogage et crée un nouveau fichier journal.

À l’invite de commandes, tapez la commande suivante pour nettoyer `myproject`.

`msbuild myproject.vcxproj /t:clean`

### <a name="using-msbuild-with-build-properties"></a>Utilisation de MSBuild avec les propriétés de Build

L’option de ligne de commande de propriété (**/p**) vous permet de substituer une propriété dans votre fichier de build de projet. Dans le `myproject` configuration de build de projet, la version ou le débogage exemple est spécifiée par le `Configuration` propriété. Et le système d’exploitation qui est destiné à exécuter l’application générée est spécifié par le `Platform` propriété.

À l’invite de commandes, tapez la commande suivante pour créer une version debug de la `myproject` application est destinée à s’exécuter sur Windows de 32 bits.

`msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`

Supposons que le `myproject` exemple de projet définit également une configuration pour Windows de 64 bits et une autre configuration pour un système d’exploitation personnalisé nommé `myplatform`.

À l’invite de commandes, type de build de la commande suivante pour créer une version qui s’exécute sur Windows de 64 bits.

`msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`

À l’invite de commandes, tapez la commande suivante pour créer une version Release pour `myplatform`.

`msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`

### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>Utilisation de MSBuild avec le compilateur 64 bits et outils

Si vous avez installé Visual C++ sur Windows 64 bits, par défaut, le x64 64 64 bits natif et les outils sont installés. Vous pouvez configurer MSBuild pour utiliser le compilateur 64 bits et outils pour générer votre application en définissant le `PreferredToolArchitecture` propriété. Cette propriété n’affecte pas les propriétés de configuration ou de la plateforme du projet. Par défaut, la version 32 bits des outils est utilisée. Pour spécifier la version 64 bits du compilateur et des outils, ajoutez l’élément de groupe de propriétés suivant au fichier projet Myproject.vcxproj après le `Microsoft.Cpp.default.props` \<Import / > élément :

```xml
<PropertyGroup>
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>
</PropertyGroup>
```

À l’invite de commandes, tapez la commande suivante pour utiliser les outils 64 bits pour générer votre application.

`msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="using-msbuild-with-a-different-toolset"></a>Utilisation de MSBuild avec un autre ensemble d’outils

Si vous avez les ensembles d’outils et les bibliothèques pour d’autres versions de Visual C++ est installé, MSBuild peut générer des applications pour la version Visual C++ actuelle ou pour les autres versions installées. Par exemple, si vous avez installé Visual Studio 2012, pour spécifier l’ensemble d’outils Visual C++ 11.0 pour Windows XP, ajoutez l’élément de groupe de propriétés suivant au fichier projet Myproject.vcxproj après le Microsoft.Cpp.props `<Import />` élément :

```xml
<PropertyGroup>
    <PlatformToolset>v110_xp</PlatformToolset>
</PropertyGroup>
```

Pour régénérer votre projet avec l’ensemble d’outils Visual C++ 11.0 Windows XP, tapez une des commandes suivantes :

`msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`

`msbuild myproject.vcxproj /t:rebuild`

### <a name="adding-msbuild-customizations"></a>Ajout de personnalisations MSBuild

MSBuild fournit différentes façons de personnaliser votre processus de génération. Les rubriques suivantes montrent comment ajouter des étapes de génération personnalisée, des outils et des événements à votre projet MSBuild :

- [Guide pratique pour ajouter une étape de génération personnalisée à des projets MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)

- [Guide pratique pour ajouter des outils de génération personnalisés à des projets MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)

- [Guide pratique pour utiliser des événements de build dans des projets MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)
