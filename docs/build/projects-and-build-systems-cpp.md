---
title: Les projets C/C++ et les systèmes de génération dans Visual Studio
ms.description: Use Visual Studio to compile and build C++ projects for Windows, ARM or Linux based on any project system.
ms.date: 05/06/2019
helpviewer_keywords:
- builds [C++]
- C++ projects, building
- projects [C++], building
- builds [C++], options
- C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
ms.openlocfilehash: b345517bb1202030c9d512d16e80484feb4ba737
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220362"
---
# <a name="cc-projects-and-build-systems-in-visual-studio"></a>Les projets C/C++ et les systèmes de génération dans Visual Studio

Vous pouvez utiliser Visual Studio 2017 pour modifier, compiler et générer de code C++ base avec une prise en charge IntelliSense complète sans avoir à convertir ce code dans un projet Visual Studio ou de la compilation avec l’ensemble d’outils MSVC. Par exemple, vous pouvez modifier un projet de CMake inter-plateformes dans Visual Studio sur un ordinateur Windows, puis compilez-le pour Linux à l’aide de g ++ sur un ordinateur Linux distant.

## <a name="c-compilation"></a>Compilation C++

Pour *build* signifie d’un programme C++ à compiler le code source à partir d’un ou plusieurs fichiers et ensuite lier ces fichiers dans un fichier exécutable (.exe), une bibliothèque dynamique-charge (.dll) ou une bibliothèque statique (.lib). 

Compilation de C++ base implique trois étapes principales :

- Le préprocesseur C++ transforme toutes les définitions #directives et macro dans chaque fichier source. Cette opération crée un *unité de traduction*.
- Le compilateur C++ compile chaque unité de traduction dans des fichiers objet (.obj), application de toutes les options du compilateur ont été définies.
- Le *l’éditeur de liens* fusionne les fichiers objets dans un seul exécutable, en appliquant les options de l’éditeur de liens qui ont été définies. 

## <a name="the-msvc-toolset"></a>L’ensemble d’outils MSVC

Microsoft C++ compilateur, éditeur de liens, des bibliothèques standards et d’utilitaires associés constituent l’ensemble d’outils du compilateur MSVC (également appelé une chaîne d’outils ou des « outils de build »). Ceux-ci sont inclus dans Visual Studio. Vous pouvez également télécharger et utiliser gratuitement l’ensemble d’outils sous forme de package autonome à partir de la [emplacement de téléchargement des outils de génération pour Visual Studio 2017](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017).

Vous pouvez créer des programmes simples en appelant le MSVC du compilateur (cl.exe) directement à partir de la ligne de commande. La commande suivante accepte un fichier de code source unique et appelle cl.exe pour générer un fichier exécutable appelé *hello.exe*: 

```cmd
cl /EHsc hello.cpp
```
Notez que le compilateur (cl.exe) ici appelle automatiquement le préprocesseur C++ et l’éditeur de liens pour produire le fichier de sortie finale.  Pour plus d’informations, consultez [génération sur la ligne de commande](building-on-the-command-line.md).

## <a name="build-systems-and-projects"></a>Génération de projets et systèmes

La plupart des programmes du monde réel utilisent certains type de *système de génération* pour gérer les complexités de la compilation de plusieurs fichiers sources pour plusieurs configurations (par exemple, debug et release), plusieurs plateformes (x86, x64, ARM, et ainsi de suite), génération personnalisée étapes et même plusieurs exécutables qui doivent être compilés dans un certain ordre. Vous définissez des paramètres dans un ou plusieurs fichiers de configuration de build, et le système de génération accepte ce fichier en tant qu’entrée avant elle appeler le compilateur. L’ensemble des fichiers de code source et les fichiers de configuration de build nécessaires pour générer un fichier exécutable est appelée un *projet*. 

La liste suivante présente les différentes options pour les projets Visual Studio - C++ :

- créer un projet Visual Studio à l’aide de l’IDE Visual Studio et configurez-le à l’aide des pages de propriétés. Projets Visual Studio générer des programmes qui s’exécutent sur Windows. Pour une vue d’ensemble, consultez [compilation et génération](/visualstudio/ide/compiling-and-building-in-visual-studio) dans la documentation de Visual Studio.

- Ouvrez le dossier qui contient un fichier CMakeLists.txt. Prise en charge de CMake est intégré à Visual Studio. Vous pouvez utiliser l’IDE pour modifier, tester et déboguer sans modifier les fichiers CMake en aucune façon. Cela vous permet d’utiliser dans le même projet CMake en tant que d’autres utilisateurs susceptibles d’utiliser différents éditeurs. CMake est l’approche recommandée pour le développement multiplateforme. Pour plus d’informations, consultez [projets CMake](cmake-projects-in-visual-studio.md).
 
- ouvrir un dossier libre des fichiers sources sans fichier de projet. Visual Studio utilise l’heuristique pour générer les fichiers. Il s’agit d’un moyen simple pour compiler et exécuter des applications de console small. Pour plus d’informations, consultez [Open Folder projects](open-folder-projects-cpp.md).

- Ouvrez le dossier qui contient un makefile, ou tout autre fichier de configuration de système build. Vous pouvez configurer Visual Studio pour appeler des commandes de génération arbitraire en ajoutant des fichiers JSON dans le dossier. Pour plus d’informations, consultez [Open Folder projects](open-folder-projects-cpp.md).
 
- Ouvrez un makefile Windows dans Visual Studio. Pour plus d’informations, consultez [Référence NMAKE](reference/nmake-reference.md).

## <a name="msbuild-from-the-command-line"></a>MSBuild à partir de la ligne de commande 

Vous pouvez appeler MSBuild à partir de la ligne de commande, en lui passant un fichier .vcxproj, ainsi que les options de ligne de commande. Cette approche nécessite une bonne compréhension de MSBuild et est recommandée uniquement lorsque c’est absolument nécessaire. Pour plus d’informations, consultez [MSBuild](msbuild-visual-cpp.md).

## <a name="in-this-section"></a>Dans cette section

[Projets Visual Studio](creating-and-managing-visual-cpp-projects.md) comment créer, configurer, et C++ de générer les (MSBuild) de système de génération de projets dans Visual Studio à l’aide de son natif.

[Projets CMake](cmake-projects-in-visual-studio.md) comment coder, générer et déployer des projets CMake dans Visual Studio.

[Ouvrir des projets de dossier](open-folder-projects-cpp.md) comment utiliser Visual Studio pour du code, générer et déployer des projets C++ basées sur n’importe quel système de génération arbitraire, ou aucun système de génération. Pas du tout. 

[Versions Release](release-builds.md) génère de la création et de résoudre les problèmes de version optimisée pour le déploiement pour les utilisateurs finaux.

[Utiliser le jeu d’outils MSVC à partir de la ligne de commande](building-on-the-command-line.md)<br/>
Explique comment utiliser le compilateur C/C++ et outils de génération directement de la ligne de commande plutôt que d’à l’aide de l’IDE Visual Studio.

[Générez des DLL dans Visual Studio](dlls-in-visual-cpp.md) comment créer, déboguer et déployer les DLL (bibliothèques partagées) C/C++ dans Visual Studio.

[Procédure pas à pas : Création et utilisation d’une bibliothèque statique](walkthrough-creating-and-using-a-static-library-cpp.md) comment créer un fichier binaire .lib.

[Création d’Applications isolées C/C++ et les assemblys côte à côte](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md) décrit le modèle de déploiement pour les applications de bureau de Windows, basée sur l’idée d’applications isolées et assemblys côte à côte.

[Configurer des projets C++ pour x64 64 64 bits, cibles](configuring-programs-for-64-bit-visual-cpp.md) comment à cibler x64 64 64 bits matériel avec le MSVC outils de génération.

[Configurer des projets C++ pour les processeurs ARM](configuring-programs-for-arm-processors-visual-cpp.md) comment utiliser les outils de génération MSVC pour cibler les matériel ARM.

[Optimisation de votre Code](optimizing-your-code.md) comment optimiser votre code de différentes manières, notamment les optimisations de programme guidée.

[Configuration des programmes pour Windows XP](configuring-programs-for-windows-xp.md) comment cible XP de Windows avec le MSVC des outils de génération.

[Référence de la génération C/C++](reference/c-cpp-building-reference.md)<br/>
Fournit des liens vers des articles de référence sur la génération de programmes en C++, les options de compilateur et d'éditeur de liens, ainsi que divers outils de génération.
