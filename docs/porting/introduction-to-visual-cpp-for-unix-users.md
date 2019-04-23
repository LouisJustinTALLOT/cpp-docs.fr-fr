---
title: Introduction à Visual C++ pour les utilisateurs UNIX
ms.date: 09/01/2017
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
ms.openlocfilehash: 2b0736bca9cc0b67f9ea8ac83dc18fadaeefdb3c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58780819"
---
# <a name="introduction-to-visual-c-for-unix-users"></a>Introduction à Visual C++ pour les utilisateurs UNIX

Cette rubrique fournit des informations aux utilisateurs UNIX qui débutent avec Visual Studio et qui souhaitent tirer pleinement parti de C++ et de l’environnement de développement intégré (IDE) de Visual Studio.

## <a name="getting-started-on-the-command-line"></a>Débuter sur la ligne de commande

Vous pouvez utiliser le compilateur C++ à partir de la ligne de commande, comme vous le feriez dans un environnement de ligne de commande UNIX. Vous pouvez compiler à partir de l’invite de commandes à l’aide du compilateur en ligne de commande C et C++ (CL.EXE), de l’éditeur de liens (LINK.EXE) et d’autres outils comme NMAKE.EXE, la version Microsoft de l’utilitaire UNIX.

Sous UNIX, les commandes sont installées dans un dossier commun, tel que /usr/bin. Dans Visual Studio, les outils en ligne de commande sont installés dans votre répertoire d’installation de Visual Studio, dans le sous-répertoire VC\bin et ses sous-répertoires. Contrairement à UNIX, ces outils ne sont pas disponibles dans une fenêtre d’invite de commandes standard. Pour accéder aux outils en ligne de commande, utilisez un raccourci vers l’invite de commandes développeur, ou exécutez un fichier de commandes développeur tel que vcvarsall.bat. Cela définit le chemin et les autres variables d’environnement nécessaires pour compiler les programmes C++ à partir de la ligne de commande. Pour plus d’informations, consultez [Générer du code C/C++ sur la ligne de commande](../build/building-on-the-command-line.md) et [Procédure pas à pas : Compilation d’un programme C++ natif sur la ligne de commande](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).

Pour ouvrir un raccourci d’invite de commandes développeur, entrez *invite de commandes développeur* dans le contrôle de recherche sur l’ordinateur, puis choisissez le résultat **Invite de commandes développeur** correspondant à votre version de Visual Studio. Pour choisir une invite de commandes développeur préconfigurée pour une architecture hôte et cible spécifique, ouvrez le menu **Démarrer** (icône Windows dans le coin du Bureau), puis faites défiler le menu jusqu’au dossier correspondant à votre version de Visual Studio (par exemple, **Visual Studio 2017**). Ouvrez le dossier et choisissez le raccourci d’invite de commandes pour votre architecture hôte et cible par défaut.

Utilisez l’environnement de développement intégré (IDE) de Visual Studio pour bénéficier d’autres fonctionnalités puissantes, comme le débogueur Visual Studio, la recherche et la saisie semi-automatique des instructions de code IntelliSense, les concepteurs visuels, la gestion de projet, etc.

## <a name="debugging-your-code"></a>Débogage de votre code

Si vous utilisez la ligne de commande et exécutez vos applications sur votre station de travail de développement, vous pouvez voir qu’une boîte de dialogue permettant d’exécuter le débogueur Visual Studio s’affiche quand votre code rencontre une violation d’accès mémoire, une exception non prise en charge ou d’autres erreurs irrécupérables. Si vous cliquez sur **OK**, l’environnement de développement Visual Studio se lance et le débogueur s’ouvre au point de défaillance. Il est possible de déboguer vos applications de cette façon et, dans ce cas, votre code source ne sera disponible que si vous avez effectué la compilation avec le commutateur [/Z7, /Zi, /ZI (format des informations de débogage)](../build/reference/z7-zi-zi-debug-information-format.md). Pour plus d’informations, consultez [Débogage du code natif](/visualstudio/debugger/debugging-native-code) et [Utilisation de l’IDE de Visual Studio pour le développement de bureau C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="using-the-development-environment"></a>Utilisation de l'environnement de développement

Il est plus facile d’utiliser l’environnement de développement pour modifier et générer votre code source dans un *projet*. Un projet est une collection de fichiers sources et de fichiers connexes qui seront compilés en une seule unité, telle qu’une bibliothèque ou un fichier exécutable. Un projet contient également des informations sur la façon dont les fichiers doivent être générés. Les informations sur les projets sont stockées dans un fichier projet avec l’extension .prj.

Les applications composées de plusieurs bibliothèques et fichiers exécutables (chacun ayant pu être généré avec un jeu différent d’options du compilateur ou même dans un langage différent) sont stockées dans plusieurs projets qui font partie d’une seule et même *solution*. Une solution est une abstraction pour un conteneur qui regroupe plusieurs projets. Les informations sur les solutions sont stockées dans un fichier solution avec l’extension .sln. Pour plus d’informations, consultez [Solutions et projets dans Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio) et [Utilisation de l’IDE de Visual Studio pour le développement de bureau C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="importing-your-existing-code"></a>Importation de votre code existant

Vous pouvez utiliser le compilateur C++ pour générer du code existant configuré pour être compilé avec ou sans makefile, et le placer dans un projet Visual Studio. Pour plus d'informations, voir [Procédure : Créer un projet C++ à partir de code existant](../build/how-to-create-a-cpp-project-from-existing-code.md).

## <a name="creating-a-new-project"></a>Création d'un projet

Vous pouvez créer des projets dans l'environnement de développement. Visual Studio propose de nombreux modèles qui fournissent du code standard pour différents projets courants. Vous pouvez utiliser les Assistants Application pour générer des projets à l'aide de schémas de code visant divers types d'application.

Vous pouvez démarrer avec un projet vide dans l’**Assistant Application Console (Win32)**. Cochez la case **Projet vide**. Vous pourrez par la suite ajouter au projet de nouveaux fichiers et des fichiers existants.

Quand vous créez un projet, vous devez lui attribuer un nom. Par défaut, le nom du projet est celui de la bibliothèque de liens dynamiques (DLL) ou du fichier exécutable généré par le projet. Pour plus d’informations, consultez [Création de solutions et de projets](/visualstudio/ide/creating-solutions-and-projects).

## <a name="microsoft-specific-modifiers"></a>Modificateurs Microsoft spécifiques

Le compilateur Microsoft Visual C++ implémente plusieurs extensions du langage de programmation C++ standard pour prendre en charge la programmation sur les systèmes d’exploitation Windows. Ces extensions servent à spécifier des attributs de classe de stockage, des conventions d'appel de fonction et des fonctions d'adressage, entre autres choses. Pour obtenir une liste complète de toutes les extensions C++ prises en charge, consultez [Modificateurs spécifiques Microsoft](../cpp/microsoft-specific-modifiers.md).

Vous pouvez désactiver toutes les extensions spécifiques Microsoft pour C++ à l'aide de l'option `/Za` du compilateur. Cette option est recommandée si vous souhaitez écrire du code devant s'exécuter sur plusieurs plateformes. Pour plus d’informations sur l’option de compilateur `/Za`, consultez [/Za, /Ze (désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md). Pour plus d’informations sur la conformité du compilateur C++, consultez [Conformité du langage Visual C++](../overview/visual-cpp-language-conformance.md) et [Comportement non standard](../cpp/nonstandard-behavior.md).

## <a name="precompiled-headers"></a>En-têtes précompilés

Les compilateurs Microsoft C et C++ offrent des options pour la précompilation du code en C ou C++, y compris du code incorporé. Grâce à cela, vous pouvez compiler un corps de code stable, stocker l'état compilé du code dans un fichier et, lors des compilations suivantes, combiner le code précompilé avec du code qui est toujours en cours de développement. Les compilations ultérieures sont plus rapides, car le code stable n'a pas besoin d'être recompilé.

Par défaut, le code précompilé est spécifié dans les fichiers stdafx.h et stdafx.cpp. L’Assistant **Nouveau projet** créera automatiquement ces fichiers, sauf si vous désélectionnez l’option **En-tête précompilé**. Pour plus d’informations, consultez [Création de fichiers d’en-têtes précompilés](../build/creating-precompiled-header-files.md).

## <a name="related-sections"></a>Rubriques connexes

Pour plus d’informations, consultez [Portage d’UNIX vers Win32](../porting/porting-from-unix-to-win32.md).

## <a name="see-also"></a>Voir aussi

[Projets et systèmes de build](../build/projects-and-build-systems-cpp.md)
