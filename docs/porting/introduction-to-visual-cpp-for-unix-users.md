---
description: 'En savoir plus sur : présentation de Microsoft C++ pour les utilisateurs UNIX'
title: Introduction à Microsoft C++ pour les utilisateurs UNIX
ms.date: 10/23/2019
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
ms.openlocfilehash: 1047ba4e07803bfd6863a0b7da5d0e8473938586
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159828"
---
# <a name="introduction-to-microsoft-c-for-unix-users"></a>Introduction à Microsoft C++ pour les utilisateurs UNIX

Cette rubrique fournit des informations pour les utilisateurs de toutes les versions d’UNIX qui sont nouvelles dans Visual Studio et qui souhaitent devenir productifs avec C++ à partir de la ligne de commande ou à l’aide de Visual Studio. Vous pouvez utiliser Visual Studio avec le compilateur Microsoft C++ pour cibler Windows. Vous pouvez également utiliser l’IDE de Visual Studio avec GCC ou Clang dans des environnements UNIX tels que des machines Linux distantes, MinGW-W64 et le sous-système Windows pour Linux. Pour utiliser C++ dans Visual Studio, la charge de travail **développement Desktop en c++** doit être installée. Ouvrez la Visual Studio Installer pour installer la charge de travail ou ajouter ou supprimer des composants facultatifs. Installez également la charge de travail **développement Linux avec C++** si vous ciblez une machine Linux distante. Pour le développement Android ou iOS, installez le **développement mobile avec** la charge de travail C++.

## <a name="getting-started-on-the-command-line"></a>Mise en route sur la ligne de commande

Vous pouvez utiliser le compilateur Microsoft C++ à partir de la ligne de commande de la même façon que vous utilisez un environnement de ligne de commande UNIX. Vous pouvez compiler à partir de l’invite de commandes à l’aide du compilateur en ligne de commande C et C++ (CL.EXE), de l’éditeur de liens (LINK.EXE) et d’autres outils comme NMAKE.EXE, la version Microsoft de l’utilitaire UNIX.

Sous UNIX, les commandes sont installées dans un dossier commun, tel que /usr/bin. Dans Visual Studio, les outils en ligne de commande sont installés dans votre répertoire d’installation de Visual Studio, dans le sous-répertoire VC\bin et ses sous-répertoires. Contrairement à UNIX, ces outils ne sont pas disponibles dans une fenêtre d’invite de commandes standard. Pour utiliser les outils en ligne de commande, vous devez utiliser une invite de commandes développeur spéciale qui configure le chemin d’accès et d’autres variables d’environnement nécessaires pour compiler les programmes C++. Pour plus d’informations, consultez [Générer du code C/C++ sur la ligne de commande](../build/building-on-the-command-line.md) et [Procédure pas à pas : compilation d’un programme C++ natif sur la ligne de commande](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).

## <a name="debugging-your-code"></a>Débogage de votre code

Vous pouvez utiliser le débogueur Visual Studio pour les projets Microsoft C++ à partir de la ligne de commande, ou à partir de l’IDE. Compilez avec le commutateur [/Z7,/Zi,/ZI (format des informations de débogage)](../build/reference/z7-zi-zi-debug-information-format.md) pour activer l’exécution pas à pas des sources. Pour plus d’informations, consultez [Débogage du code natif](/visualstudio/debugger/debugging-native-code) et [Utilisation de l’IDE de Visual Studio pour le développement de bureau C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

Pour les programmes compilés avec GCC ou Clang, Visual Studio appelle GDB, LLDB ou tout autre débogueur personnalisé que vous spécifiez.

## <a name="visual-studio-project-system"></a>Système de projet Visual Studio

Le système de projet Visual Studio est appelé MSBuild. Il utilise les fichiers projet au format XML ; Les fichiers projet C++ portent l’extension. vcxproj. Les applications composées de plusieurs bibliothèques et fichiers exécutables (chacun ayant pu être généré avec un jeu différent d’options du compilateur ou même dans un langage différent) sont stockées dans plusieurs projets qui font partie d’une seule et même *solution*. Une solution est une abstraction pour un conteneur qui regroupe plusieurs projets. Les informations sur les solutions sont stockées dans un fichier solution avec l’extension .sln. Pour plus d’informations, consultez [Solutions et projets dans Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio) et [Utilisation de l’IDE de Visual Studio pour le développement de bureau C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md). Dans le menu principal, choisissez **fichier**  >  **nouveau**  >  **projet** pour afficher les modèles de projet Visual Studio disponibles.

À compter de Visual Studio 2017, la prise en charge des projets CMake est ajoutée, ainsi que des options permettant d’utiliser le compilateur Microsoft C++ avec n’importe quel système de génération arbitraire, ou avec un dossier libre de fichiers sources et aucun fichier projet. Pour plus d’informations, consultez [projets cmake dans Visual Studio](../build/cmake-projects-in-visual-studio.md) et [ouvrir des projets de dossier dans Visual Studio](../build/open-folder-projects-cpp.md).

## <a name="microsoft-specific-modifiers"></a>Modificateurs propres à Microsoft

Le compilateur Microsoft C++ implémente plusieurs extensions du langage de programmation C++ standard pour prendre en charge la programmation sur les systèmes d’exploitation Windows. Ces extensions servent à spécifier des attributs de classe de stockage, des conventions d'appel de fonction et des fonctions d'adressage, entre autres choses. Pour obtenir une liste complète de toutes les extensions C++ prises en charge, consultez [Modificateurs spécifiques Microsoft](../cpp/microsoft-specific-modifiers.md).

Vous pouvez désactiver toutes les extensions spécifiques Microsoft pour C++ à l'aide de l'option `/Za` du compilateur. Cette option est recommandée si vous souhaitez écrire du code devant s'exécuter sur plusieurs plateformes. Pour plus d’informations sur l’option de compilateur `/Za`, consultez [/Za, /Ze (désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md). Pour plus d’informations sur la conformité du compilateur C++, consultez la [table de conformité du langage Microsoft c++](../overview/visual-cpp-language-conformance.md) et le [comportement non standard](../cpp/nonstandard-behavior.md).

## <a name="precompiled-headers"></a>En-têtes précompilés

Les compilateurs Microsoft C et C++ offrent des options pour la précompilation du code en C ou C++, y compris du code incorporé. Grâce à cela, vous pouvez compiler un corps de code stable, stocker l'état compilé du code dans un fichier et, lors des compilations suivantes, combiner le code précompilé avec du code qui est toujours en cours de développement. Les compilations ultérieures sont plus rapides, car le code stable n'a pas besoin d'être recompilé.

Par défaut, le code précompilé est spécifié dans les fichiers *pch.h* et *pch.cpp* (*stdafx.h* et *stdafx.cpp* dans Visual Studio 2017 et les versions antérieures). Pour plus d’informations, consultez [Création de fichiers d’en-têtes précompilés](../build/creating-precompiled-header-files.md).

## <a name="related-sections"></a>Sections connexes

Pour plus d’informations, consultez [exécution de programmes Linux sur Windows](../porting/porting-from-unix-to-win32.md).

## <a name="see-also"></a>Voir aussi

[Projets et systèmes de build](../build/projects-and-build-systems-cpp.md)
