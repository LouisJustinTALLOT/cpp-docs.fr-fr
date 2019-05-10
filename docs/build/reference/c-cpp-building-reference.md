---
title: Référence de génération C/C++ - Visual Studio
description: Contenu de référence pour les outils de génération et de système de projet dans Visual Studio C/C++.
ms.date: 05/06/2019
helpviewer_keywords:
- compiling source code [C++], additional information
- cl.exe compiler [C++], building programs
- linker [C++], building reference
- builds [C++], additional information
ms.assetid: 100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d
ms.openlocfilehash: abe946ce516e915cd597a0f863c5949fed212bfa
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221444"
---
# <a name="cc-building-reference"></a>Référence à la génération C/C++

Visual Studio fournit deux méthodes de génération C /C++ programme. Le moyen le plus simple (et la plus courante) consiste à [générer l’IDE de Visual Studio](../creating-and-managing-visual-cpp-projects.md). L’autre consiste à [construire à partir d’une invite de commandes à l’aide des outils de ligne de commande](../building-on-the-command-line.md). Dans les deux cas, vous pouvez créer et modifier vos fichiers source à l’aide de Visual Studio ou un éditeur tiers de votre choix.

## <a name="in-this-section"></a>Dans cette section

[Référence MSBuild pour les projets C++](msbuild-visual-cpp-overview.md)

[Informations de référence sur le compilateur MSVC](compiling-a-c-cpp-program.md)<br/>
Décrit le compilateur MSVC, qui crée un fichier objet contenant le code machine, les directives de l’éditeur de liens, sections, des références externes et les noms de fonction/donnée.

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
Décrit l’éditeur de liens, qui combine le code à partir des fichiers objet créés par le compilateur et des bibliothèques liées statiquement, résout les références de nom et crée un fichier exécutable.

[Prise en charge Unicode dans le compilateur et l’éditeur de liens](unicode-support-in-the-compiler-and-linker.md)

[Outils de génération MSVC supplémentaires](c-cpp-build-tools.md)<br/>
Outils de ligne de commande supplémentaires pour C++.

[Erreurs de build C/C++](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)<br/>
Présente la section d’erreurs de build dans la table des matières.

## <a name="related-sections"></a>Rubriques connexes

[Informations de référence sur le préprocesseur C/C++](../../preprocessor/c-cpp-preprocessor-reference.md)<br/>
Décrit le préprocesseur, qui prépare les fichiers sources pour le compilateur en convertissant les macros, les opérateurs et les directives.

[Présentation des étapes de génération personnalisée et des événements de build](../understanding-custom-build-steps-and-build-events.md)<br/>
Traite de la personnalisation du processus de génération.

[Génération d’un programme C/C++](../projects-and-build-systems-cpp.md)<br/>
Fournit des liens vers des rubriques qui décrivent comment générer votre programme à partir de la ligne de commande ou de l'environnement de développement intégré de Visual Studio.

[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
Décrit la définition des options du compilateur dans l’environnement de développement ou sur la ligne de commande.

[Options du compilateur MSVC](compiler-options.md)<br/>
Fournit des liens vers des rubriques décrivant l’utilisation des options du compilateur.

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
Décrit la définition des options de l’éditeur de liens à l’intérieur ou en dehors de l’environnement de développement intégré.

[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
Fournit des liens vers des rubriques décrivant l’utilisation des options de l’éditeur de liens.

[Référence BSCMAKE](bscmake-reference.md)<br/>
Décrit l’utilitaire de Maintenance (BSCMAKE. (EXE), qui génère un fichier d’informations de consultation (.bsc) à partir de .sbr fichiers créés pendant la compilation.

[Référence LIB](lib-reference.md)<br/>
Décrit le Gestionnaire de bibliothèque de Microsoft (LIB.exe), qui crée et gère une bibliothèque de fichiers d’objets fichier Format COFF (Common Object).

[Informations de référence sur EDITBIN](editbin-reference.md)<br/>
Décrit l’éditeur de fichiers binaires Microsoft COFF (EDITBIN. (EXE), qui modifie les fichiers binaires du fichier Format COFF (Common Object).

[Informations de référence sur DUMPBIN](dumpbin-reference.md)<br/>
Décrit l’outil Microsoft COFF Binary File Dumper (DUMPBIN. (EXE), qui affiche des informations sur les fichiers binaires du fichier Format COFF (Common Object).

[NMAKE, référence](nmake-reference.md)<br/>
Décrit l’utilitaire Microsoft Program Maintenance (NMAKE. (EXE), qui est un outil qui génère des projets basés sur des commandes contenues dans un fichier de description.
