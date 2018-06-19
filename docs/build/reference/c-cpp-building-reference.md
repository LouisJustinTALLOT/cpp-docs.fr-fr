---
title: Référence de génération C/C++ | Documents Microsoft
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
ms.openlocfilehash: 2d26f729f660b3e51677303bb91b99e665a1a950
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375482"
---
# <a name="cc-building-reference"></a>Référence à la génération C/C++
Visual C++ propose deux méthodes de création d’un programme C/C++. La plus simple (et le plus courant) consiste à [générer dans l’environnement de développement Visual C++](../../ide/building-cpp-projects-in-visual-studio.md). L’autre méthode consiste à [construire à partir d’une invite de commandes à l’aide des outils de ligne de commande](../../build/building-on-the-command-line.md). Dans les deux cas, vous pouvez créer vos fichiers sources à l’aide de l’éditeur de code source Visual C++ ou un éditeur tiers de votre choix.  
  
 Si votre programme utilise un makefile plutôt qu’un fichier .vcxproj, vous pouvez le générer dans l’environnement de développement comme un [projet externe](../../ide/building-external-projects.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Compilation d’un programme C/C++](../../build/reference/compiling-a-c-cpp-program.md)  
 Décrit le compilateur, ce qui crée un fichier objet contenant le code machine, les directives de l’éditeur de liens, sections, des références externes et les noms de fonction/donnée.  
  
 [Liaison](../../build/reference/linking.md)  
 Décrit l’éditeur de liens, qui combine le code à partir des fichiers d’objet créés par le compilateur et à partir de bibliothèques liées statiquement, résout les références de nom et crée un fichier exécutable.  
  
 [Versions Release](../../build/reference/release-builds.md)  
 Présente les informations sur quand et pourquoi vous ne souhaitez pas passer d’une build pour une version Release et présente également certains des problèmes que vous pouvez rencontrer lors de la modification à partir d’un débogage à une version Release.  
  
 [Optimisation du code](../../build/reference/optimizing-your-code.md)  
 Fournit des liens vers les rubriques décrivant les mécanismes d’optimisation de code :  
  
 [Outils de génération C/C++](../../build/reference/c-cpp-build-tools.md)  
 Fournit les outils de ligne de commande suivants pour l’affichage ou la manipulation de sortie de génération :  
  
 [Erreurs de build C/C++](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)  
 Présente la section d’erreurs de build dans la table des matières.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Informations de référence sur le préprocesseur C/C++](../../preprocessor/c-cpp-preprocessor-reference.md)  
 Explique le préprocesseur, qui prépare les fichiers sources pour le compilateur en convertissant les macros, les opérateurs et les directives.  
  
 [Présentation des étapes de génération personnalisée et des événements de build](../../ide/understanding-custom-build-steps-and-build-events.md)  
 Traite de la personnalisation du processus de génération.  
  
 [Création d’un programme C/C++](../../build/building-c-cpp-programs.md)  
 Fournit des liens vers des rubriques qui décrivent comment générer votre programme à partir de la ligne de commande ou de l'environnement de développement intégré de Visual Studio.  
  
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)  
 Décrit la définition des options du compilateur dans l’environnement de développement ou sur la ligne de commande.  
  
 [Options du compilateur](../../build/reference/compiler-options.md)  
 Fournit des liens vers des rubriques décrivant l’utilisation des options du compilateur.  
  
 [Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)  
 Décrit la définition des options de l’éditeur de liens à l’intérieur ou à l’extérieur de l’environnement de développement intégré.  
  
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)  
 Fournit des liens vers des rubriques décrivant l’utilisation des options de l’éditeur de liens.  
  
 [Référence BSCMAKE](../../build/reference/bscmake-reference.md)  
 Décrit l’utilitaire de Maintenance (BSCMAKE. (EXE), qui génère un fichier d’informations de consultation (.bsc) à partir de .sbr créés lors de la compilation des fichiers.  
  
 [Référence LIB](../../build/reference/lib-reference.md)  
 Décrit le Gestionnaire de bibliothèque de Microsoft (LIB.exe), qui crée et gère une bibliothèque de fichiers d’objets fichier Format COFF (Common Object).  
  
 [Informations de référence sur EDITBIN](../../build/reference/editbin-reference.md)  
 Décrit l’éditeur de fichiers binaires Microsoft COFF (EDITBIN. (EXE), qui modifie les fichiers binaires du fichier Format COFF (Common Object).  
  
 [Informations de référence sur DUMPBIN](../../build/reference/dumpbin-reference.md)  
 Décrit l’outil Microsoft COFF Binary File Dumper (DUMPBIN. (EXE), qui affiche des informations sur les fichiers binaires du fichier Format COFF (Common Object).  
  
 [NMAKE, référence](../../build/nmake-reference.md)  
 Décrit l’utilitaire Microsoft Program Maintenance (NMAKE. (EXE), qui est un outil qui génère des projets en fonction des commandes contenues dans un fichier de description.