---
title: 'Procédure pas à pas : Déboguer un projet (C++)'
ms.date: 09/14/2018
helpviewer_keywords:
- projects [C++], debugging
- project debugging [C++]
- debugging projects
ms.assetid: a5cade77-ba51-4b03-a7a0-6897e3cd6a59
ms.openlocfilehash: 0a1ceddca3234ead7d10cc839d41a6d644ec1866
ms.sourcegitcommit: 9e85c2e029d06b4c1c69837437468718b4d54908
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "57812029"
---
# <a name="walkthrough-debugging-a-project-c"></a>Procédure pas à pas : Déboguer un projet (C++)

Dans cette procédure pas à pas, vous modifiez le programme pour résoudre le problème que vous avez détecté au moment du test du projet.

## <a name="prerequisites"></a>Prérequis

- Cette procédure pas à pas part du principe que vous comprenez les notions de base du langage C++.

- Elle suppose également que vous avez effectué les procédures pas à pas connexes précédentes listées dans [Utilisation de l’IDE Visual Studio pour le développement d’applications de bureau C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

### <a name="to-fix-a-program-that-has-a-bug"></a>Pour corriger un programme contenant un bogue

1. Pour voir ce qui se passe quand un objet `Cardgame` est détruit, examinez le destructeur de la classe `Cardgame`.

   Dans la barre de menus, choisissez **Affichage** > **Affichage de classes**.

   Dans la fenêtre **Affichage de classes**, développez l’arborescence du projet **Game** et sélectionnez la classe **Cardgame** pour afficher les membres de classe et les méthodes.

   Ouvrez le menu contextuel du destructeur **~Cardgame(void)**, puis choisissez **Atteindre la définition**.

1. Pour réduire la valeur de `totalParticipants` quand un Cardgame se termine, ajoutez le code suivant entre les accolades du destructeur `Cardgame::~Cardgame`.

   [!code-cpp[NVC_Walkthrough_Debugging_A_Project#110](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_1.cpp)]

1. Le fichier Cardgame.cpp doit ressembler au code ci-dessous après le changement :

   [!code-cpp[NVC_Walkthrough_Debugging_A_Project#111](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_2.cpp)]

1. Dans la barre de menus, choisissez **Générer**  >  **Générer la solution**.

1. Dès que la build est effectuée, exécutez-la en mode débogage en choisissant **Déboguer** > **Démarrer le débogage** dans la barre de menus, ou appuyez sur la touche **F5**. Le programme s’interrompt au premier point d’arrêt.

1. Pour exécuter pas à pas le programme, dans la barre de menus, choisissez **Déboguer** > **Pas à pas principal**, ou appuyez sur **F10**.

   Notez qu’après l’exécution de chaque constructeur `Cardgame`, la valeur de `totalParticipants` augmente. Quand la fonction `PlayGames` retourne une réponse, chaque fois qu’une instance `Cardgame` est hors de portée et supprimée (et que le destructeur est appelé), `totalParticipants` diminue. Juste avant l’exécution de l’instruction `return`, `totalParticipants` est égal à 0.

1. Continuer à exécuter pas à pas le programme jusqu’à la fin, ou laissez-le s’exécuter en choisissant **Déboguer** > **Exécuter** dans la barre de menus, ou appuyez sur **F5**.

## <a name="next-steps"></a>Étapes suivantes

**Précédent :** [Procédure pas à pas : Test d’un projet (C++)](../ide/walkthrough-testing-a-project-cpp.md)<br/>
**Suivant :** [Procédure pas à pas : Déploiement de votre programme (C++)](../ide/walkthrough-deploying-your-program-cpp.md)<br/>

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Projets et systèmes de build](../build/projects-and-build-systems-cpp.md)<br/>
