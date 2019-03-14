---
title: 'Procédure pas à pas : test d’un projet (C++)'
ms.date: 09/14/2018
helpviewer_keywords:
- project testing [C++]
- testing projects
- projects [C++], testing
ms.assetid: 88cdd377-c5c8-4201-889d-32f5653ebead
ms.openlocfilehash: e93236f9bd08741bb757e43309cd59281f828da1
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744605"
---
# <a name="walkthrough-testing-a-project-c"></a>Procédure pas à pas : test d’un projet (C++)

Quand vous exécutez un programme en mode débogage, vous pouvez utiliser des points d’arrêt pour interrompre le programme afin d’examiner l’état des variables et des objets.

Dans cette procédure pas à pas, vous observez la valeur d’une variable que le programme exécute et déduisez pourquoi la valeur ne correspond pas à celle que vous attendez.

## <a name="prerequisites"></a>Prérequis

- Cette procédure pas à pas part du principe que vous comprenez les notions de base du langage C++.

- Elle suppose également que vous avez effectué les procédures pas à pas connexes précédentes listées dans [Utilisation de l’IDE Visual Studio pour le développement d’applications de bureau C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

### <a name="to-run-a-program-in-debug-mode"></a>Pour exécuter le programme en mode débogage

1. Ouvrez Games.cpp pour le modifier.

1. Sélectionnez cette ligne de code :

   `Cardgame.solitaire(1);`

1. Pour définir un point d’arrêt sur cette ligne, dans la barre de menus, choisissez **Déboguer** > **Basculer le point d’arrêt** ou appuyez sur **F9**. Un cercle rouge apparaît à gauche de la ligne. Il indique qu’un point d’arrêt est défini. Pour supprimer un point d’arrêt, vous pouvez choisir la commande de menu ou réappuyer sur **F9**.

   Si vous utilisez une souris, vous pouvez aussi définir ou supprimer un point d’arrêt en cliquant dans la marge de gauche.

1. Dans la barre de menus, choisissez **Déboguer** > **Démarrer le débogage** ou appuyez sur **F5**.

   Quand le programme atteint la ligne contenant le point d’arrêt, l’exécution s’arrête temporairement, car votre programme est en mode Arrêt. Une flèche jaune à gauche d’une ligne de code indique qu’il s’agit de la ligne suivante à exécuter.

1. Pour examiner la valeur de la variable `Cardgame::totalParticipants`, déplacez le pointeur sur `Cardgame`, puis déplacez-le sur le contrôle d’extension à gauche de la fenêtre d’info-bulle. Le nom de variable `totalParticipants` et sa valeur **12** sont affichés.

   Ouvrez le menu contextuel de la variable `Cardgame::totalParticipants`, puis choisissez **Ajouter un espion** pour afficher cette variable dans la fenêtre **Espion 1**. Vous pouvez aussi mettre en surbrillance une variable et la faire glisser dans la fenêtre **Espion 1**.

1. Pour passer à la ligne de code suivante, dans la barre de menus, choisissez **Déboguer** > **Pas à pas principal** ou appuyez sur **F10**.

   La valeur de `Cardgame::totalParticipants` dans la fenêtre **Espion 1** est maintenant affichée comme étant **13**.

1. Ouvrez le menu contextuel de l’instruction `return 0;`, puis choisissez **Exécuter jusqu’au curseur**. La flèche jaune à gauche du code pointe vers l’instruction suivante à exécuter.

1. Le nombre `Cardgame::totalParticipants` doit diminuer quand un `Cardgame` se termine. À ce stade, `Cardgame::totalParticipants` doit être égal à 0, car toutes les instances de `Cardgame` ont été supprimées, mais la fenêtre **Espion 1** indique que `Cardgame::totalparticipants` est égal à **18**. La différence indique qu’il y a un bogue dans le code, que vous pouvez détecter et corriger en effectuant la procédure pas à pas suivante, [Procédure pas à pas : débogage d’un projet (C++)](../ide/walkthrough-debugging-a-project-cpp.md).

1. Pour arrêter le programme, dans la barre de menus, choisissez **Déboguer** > **Arrêter le débogage** ou appuyez sur le raccourci **Maj**+**F5**.

## <a name="next-steps"></a>Étapes suivantes

**Précédent :** [Procédure pas à pas : Génération d’un projet (C++)](../ide/walkthrough-building-a-project-cpp.md)<br/>
**Suivant :** [Procédure pas à pas : Débogage d'un projet (C++)](../ide/walkthrough-debugging-a-project-cpp.md)<br/>

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Génération de programmes C/C++](../build/building-c-cpp-programs.md)<br/>
