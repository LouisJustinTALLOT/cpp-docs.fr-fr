---
title: 'Procédure pas à pas : Génération d’un projet (C++) | Microsoft Docs'
ms.custom: ''
ms.date: 09/14/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- building projects [C++]
- projects [C++], building
- project building [C++]
ms.assetid: d459bc03-88ef-48d0-9f9a-82d17f0b6a4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3071b779338150816cb1d52d16932ac0e3878538
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079315"
---
# <a name="walkthrough-building-a-project-c"></a>Procédure pas à pas : génération d’un projet (C++)

Dans cette procédure pas à pas, vous introduisez délibérément une erreur de syntaxe Visual C++ dans votre code pour apprendre à reconnaître une erreur de compilation et à la résoudre. Lorsque vous compilez le projet, un message d'erreur indique en quoi consiste le problème et l'endroit où il s'est produit.

## <a name="prerequisites"></a>Prérequis

- Cette procédure pas à pas part du principe que vous comprenez les notions de base du langage C++.

- Elle suppose également que vous avez effectué les procédures pas à pas connexes précédentes listées dans [Utilisation de l’IDE Visual Studio pour le développement d’applications de bureau C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

### <a name="to-fix-compilation-errors"></a>Pour résoudre les erreurs de compilation

1. Dans Game.cpp, supprimez le point-virgule de la dernière ligne pour obtenir l’instruction suivante :

    `return 0`

1. Dans la barre de menus, choisissez **Générer**  >  **Générer la solution**.

1. Un message dans la fenêtre **Liste d’erreurs** indique qu’une erreur s’est produite pendant la génération du projet. La description ressemble au message d’erreur suivant :

    `error C2143: syntax error: missing ';' before '}'`

  Pour afficher des informations d’aide concernant cette erreur, sélectionnez-la dans la fenêtre **Liste d’erreurs**, puis appuyez sur **F1**.

1. Replacez le point-virgule à la fin de la ligne où se situe l'erreur de syntaxe :

   `return 0;`

1. Dans la barre de menus, choisissez **Générer**  >  **Générer la solution**.

  Un message dans la fenêtre **Sortie** indique que le projet a été compilé.

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>Game.cpp
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

## <a name="next-steps"></a>Étapes suivantes

**Étape précédente :** [Procédure pas à pas : utilisation de projets et de solutions (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)<br/>
**Étape suivante :** [Procédure pas à pas : test d’un projet (C++)](../ide/walkthrough-testing-a-project-cpp.md)<br/>

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Génération de programmes C/C++](../build/building-c-cpp-programs.md)<br/>
