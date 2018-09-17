---
title: Référence de génération C/C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiling source code [C++], additional information
- cl.exe compiler [C++], building programs
- linker [C++], building reference
- builds [C++], additional information
ms.assetid: 100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 116ddca6ed9f5e0b3ea02652958931f88cc8fc13
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703220"
---
# <a name="cc-building-reference"></a>Référence à la génération C/C++

Visual C++ propose deux méthodes de génération d’un programme C/C++. Le moyen le plus simple (et la plus courante) consiste à [générer dans l’environnement de développement Visual C++](../../ide/building-cpp-projects-in-visual-studio.md). L’autre consiste à [construire à partir d’une invite de commandes à l’aide des outils de ligne de commande](../../build/building-on-the-command-line.md). Dans les deux cas, vous pouvez créer vos fichiers source à l’aide de l’éditeur de code source Visual C++ ou un éditeur tiers de votre choix.

Si votre programme utilise un makefile plutôt qu’un fichier .vcxproj, vous pouvez toujours générez-le dans l’environnement de développement comme un [projet externe](../../ide/building-external-projects.md).

## <a name="in-this-section"></a>Dans cette section

[Compilation d’un programme C/C++](../../build/reference/compiling-a-c-cpp-program.md) décrit le compilateur, ce qui crée un fichier objet contenant le code machine, les directives de l’éditeur de liens, sections, des références externes et les noms de fonction/donnée.

[Liaison](../../build/reference/linking.md) décrit l’éditeur de liens, qui combine le code à partir des fichiers objet créés par le compilateur et des bibliothèques liées statiquement, résout les références de nom et crée un fichier exécutable.

[Versions Release](../../build/reference/release-builds.md) présente des informations sur quand et pourquoi vous souhaiteriez modifier à partir d’une version debug à une version Release et aborde également certains des problèmes que vous pouvez rencontrer lors de la modification à partir d’un débogage à une version Release.

[Optimisation de votre Code](../../build/reference/optimizing-your-code.md) fournit des liens vers des rubriques décrivant les mécanismes d’optimisation de code :

[Outils de génération C/C++](../../build/reference/c-cpp-build-tools.md) fournit les outils de ligne de commande suivants pour l’affichage ou la manipulation de sortie de génération :

[Erreurs de génération C/C++](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) présente la section d’erreurs de build dans la table des matières.

## <a name="related-sections"></a>Rubriques connexes

[Référence du préprocesseur C/C++](../../preprocessor/c-cpp-preprocessor-reference.md) présente le préprocesseur, qui prépare les fichiers sources pour le compilateur en convertissant les macros, les opérateurs et les directives.

[Présentation des étapes de Build personnalisée et des événements de Build](../../ide/understanding-custom-build-steps-and-build-events.md) présente personnalisation du processus de génération.

[Génération d’un programme C/C++](../../build/building-c-cpp-programs.md) fournit des liens vers des rubriques qui décrivent comment générer votre programme à partir de la ligne de commande ou à partir de l’environnement de développement intégré de Visual Studio.

[Définition des Options du compilateur](../../build/reference/setting-compiler-options.md) décrit la définition des options du compilateur dans l’environnement de développement ou sur la ligne de commande.

[Options du compilateur](../../build/reference/compiler-options.md) fournit des liens vers des rubriques décrivant l’utilisation des options du compilateur.

[Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md) décrit la définition des options de l’éditeur de liens à l’intérieur ou en dehors de l’environnement de développement intégré.

[Options de l’éditeur de liens](../../build/reference/linker-options.md) fournit des liens vers des rubriques décrivant l’utilisation des options de l’éditeur de liens.

[Référence BSCMAKE](../../build/reference/bscmake-reference.md) décrit l’utilitaire de Maintenance (BSCMAKE. (EXE), qui génère un fichier d’informations de consultation (.bsc) à partir de .sbr fichiers créés pendant la compilation.

[Référence LIB](../../build/reference/lib-reference.md) décrit le Gestionnaire de bibliothèque de Microsoft (LIB.exe), qui crée et gère une bibliothèque de fichiers d’objets fichier Format COFF (Common Object).

[Référence EDITBIN](../../build/reference/editbin-reference.md) décrit l’éditeur de fichiers binaires Microsoft COFF (EDITBIN. (EXE), qui modifie les fichiers binaires du fichier Format COFF (Common Object).

[Référence DUMPBIN](../../build/reference/dumpbin-reference.md) décrit l’outil Microsoft COFF Binary File Dumper (DUMPBIN. (EXE), qui affiche des informations sur les fichiers binaires du fichier Format COFF (Common Object).

[Référence NMAKE](../../build/nmake-reference.md) décrit l’utilitaire Microsoft Program Maintenance (NMAKE. (EXE), qui est un outil qui génère des projets basés sur des commandes contenues dans un fichier de description.