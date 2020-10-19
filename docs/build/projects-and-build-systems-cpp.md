---
title: Projets C/C++ et systèmes de génération dans Visual Studio
description: Utilisez Visual Studio pour compiler et générer des projets C++ pour Windows, ARM ou Linux basé sur n’importe quel système de projet.
ms.date: 07/17/2019
helpviewer_keywords:
- builds [C++]
- C++ projects, building
- projects [C++], building
- builds [C++], options
- C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
ms.topic: overview
ms.openlocfilehash: 193230ef393aa83d7ce4b9aec11a1fa2cb5052ce
ms.sourcegitcommit: f19f02f217b80804ab321d463c76ce6f681abcc6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92176071"
---
# <a name="cc-projects-and-build-systems-in-visual-studio"></a>Projets C/C++ et systèmes de génération dans Visual Studio

Vous pouvez utiliser Visual Studio pour modifier, compiler et générer toute base de code C++ avec une prise en charge complète d’IntelliSense sans avoir à convertir ce code en projet Visual Studio ou à compiler avec l’ensemble d’outils MSVC. Par exemple, vous pouvez modifier un projet CMake multiplateforme dans Visual Studio sur un ordinateur Windows, puis le compiler pour Linux à l’aide de g + + sur une machine Linux distante.

## <a name="c-compilation"></a>Compilation C++

Pour *générer* un programme C++ signifie compiler le code source à partir d’un ou de plusieurs fichiers, puis lier ces fichiers dans un fichier exécutable (. exe), une bibliothèque de chargement dynamique (. dll) ou une bibliothèque statique (. lib).

La compilation C++ de base implique trois étapes principales :

- Le préprocesseur C++ transforme toutes les définitions de #directives et de macro dans chaque fichier source. Cela crée une *unité de traduction*.
- Le compilateur C++ compile chaque unité de traduction en fichiers objets (. obj), en appliquant les options du compilateur qui ont été définies.
- L' *éditeur de liens* fusionne les fichiers objets en un seul exécutable, en appliquant les options de l’éditeur de liens qui ont été définies.

## <a name="the-msvc-toolset"></a>Ensemble d’outils MSVC

Le compilateur Microsoft C++, l’éditeur de liens, les bibliothèques standard et les utilitaires associés composent l’ensemble d’outils du compilateur MSVC (également appelé chaîne d’outils ou « outils de génération »). Celles-ci sont incluses dans Visual Studio. Vous pouvez également télécharger et utiliser l’ensemble d’outils en tant que package autonome gratuit à partir des [outils de génération pour Visual Studio 2019 Download](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019).

Vous pouvez générer des programmes simples en appelant le compilateur MSVC (cl.exe) directement à partir de la ligne de commande. La commande suivante accepte un fichier de code source unique et appelle cl.exe pour générer un fichier exécutable appelé *hello.exe*:

```cmd
cl /EHsc hello.cpp
```

Ici, le compilateur (cl.exe) appelle automatiquement le préprocesseur C++ et l’éditeur de liens pour générer le fichier de sortie final. Pour plus d’informations, consultez [génération sur la ligne de commande](building-on-the-command-line.md).

## <a name="build-systems-and-projects"></a>Créer des systèmes et des projets

La plupart des programmes réels utilisent un type de *système de génération* pour gérer les complexités de la compilation de plusieurs fichiers sources pour plusieurs configurations (débogage et version), plusieurs plateformes (x86, x64, ARM, etc.), des étapes de génération personnalisée et même plusieurs exécutables qui doivent être compilés dans un certain ordre. Vous définissez des paramètres dans un ou plusieurs fichiers de configuration de build, et le système de génération accepte ce fichier comme entrée avant d’appeler le compilateur. L’ensemble des fichiers de code source et des fichiers de configuration de build nécessaires pour générer un fichier exécutable est appelé *projet*.

La liste suivante présente différentes options pour les projets Visual Studio-C++ :

- Créez un projet Visual Studio à l’aide de l’IDE de Visual Studio et configurez-le à l’aide des pages de propriétés. Les projets Visual Studio produisent des programmes qui s’exécutent sur Windows. Pour obtenir une vue d’ensemble, consultez [compilation et génération](/visualstudio/ide/compiling-and-building-in-visual-studio) dans la documentation de Visual Studio.

- Ouvrez un dossier qui contient un fichier CMakeLists.txt. La prise en charge de CMake est intégrée à Visual Studio. Vous pouvez utiliser l’IDE pour modifier, tester et déboguer sans modifier les fichiers CMake de quelque manière que ce soit. Cela vous permet de travailler dans le même projet CMake que ceux qui utilisent peut-être des éditeurs différents. CMake est l’approche recommandée pour le développement multiplateforme. Pour plus d’informations, consultez [projets cmake](cmake-projects-in-visual-studio.md).

- Ouvrez un dossier libre de fichiers sources sans fichier projet. Visual Studio utilise l’heuristique pour générer les fichiers. Il s’agit d’un moyen simple de compiler et d’exécuter de petites applications console. Pour plus d’informations, consultez [ouvrir des projets de dossier](open-folder-projects-cpp.md).

- Ouvrez un dossier qui contient un Makefile ou tout autre fichier de configuration du système de génération. Vous pouvez configurer Visual Studio pour appeler des commandes de génération arbitraires en ajoutant des fichiers JSON au dossier. Pour plus d’informations, consultez [ouvrir des projets de dossier](open-folder-projects-cpp.md).

- Ouvrez un Makefile Windows dans Visual Studio. Pour plus d’informations, consultez la [Référence NMAKE](reference/nmake-reference.md).

## <a name="msbuild-from-the-command-line"></a>MSBuild à partir de la ligne de commande

Vous pouvez appeler MSBuild à partir de la ligne de commande en lui transmettant un fichier. vcxproj avec les options de ligne de commande. Cette approche nécessite une bonne compréhension de MSBuild et est recommandée uniquement lorsque cela est nécessaire. Pour plus d’informations, consultez [MSBuild](msbuild-visual-cpp.md).

## <a name="in-this-section"></a>Dans cette section

[Projets Visual Studio](creating-and-managing-visual-cpp-projects.md)\
Comment créer, configurer et générer des projets C++ dans Visual Studio à l’aide de son système de génération natif (MSBuild).

[Projets CMake](cmake-projects-in-visual-studio.md)\
Comment coder, générer et déployer des projets CMake dans Visual Studio.

[Ouvrir des projets de dossier](open-folder-projects-cpp.md)\
Comment utiliser Visual Studio pour coder, générer et déployer des projets C++ basés sur un système de génération arbitraire, ou aucun système de génération.

[Versions release](release-builds.md)\
Comment créer et dépanner des builds de version optimisées pour le déploiement vers les utilisateurs finaux.

[Utiliser l’ensemble d’outils MSVC à partir de la ligne de commande](building-on-the-command-line.md)\
Explique comment utiliser le compilateur C/C++ et les outils de génération directement à partir de la ligne de commande plutôt que d’utiliser l’IDE de Visual Studio.

[Génération de dll dans Visual Studio](dlls-in-visual-cpp.md)\
Comment créer, déboguer et déployer des dll C/C++ (bibliothèques partagées) dans Visual Studio.

[Procédure pas à pas : création et utilisation d’une bibliothèque statique](walkthrough-creating-and-using-a-static-library-cpp.md)\
Comment créer un fichier binaire **. lib** .

[Génération d’applications isolées C/C++ et d’assemblys côte à côte](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)\
Décrit le modèle de déploiement pour des applications de bureau Windows en partant du principe qu'il s'agit d'applications isolées et d'assemblys côte à côte.

[Configurer des projets C++ pour des cibles x64 64 bits](configuring-programs-for-64-bit-visual-cpp.md)\
Comment cibler un matériel x64 64 bits avec les outils de génération MSVC.

[Configurer des projets C++ pour les processeurs ARM](configuring-programs-for-arm-processors-visual-cpp.md)\
Comment utiliser les outils de génération MSVC pour cibler le matériel ARM.

[Optimisation de votre code](optimizing-your-code.md)\
Comment optimiser votre code de différentes façons, y compris des optimisations guidées par programme.

[Configuration des programmes pour Windows XP](configuring-programs-for-windows-xp.md)\
Comment cibler Windows XP avec les outils de génération MSVC.

[Informations de référence sur la génération C/C++](reference/c-cpp-building-reference.md)\
Fournit des liens vers des articles de référence sur la génération de programmes en C++, les options de compilateur et d'éditeur de liens, ainsi que divers outils de génération.
