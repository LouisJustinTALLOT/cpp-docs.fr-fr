---
description: 'En savoir plus sur : procédure pas à pas : débogage d’un projet (C++)'
title: "Procédure pas à pas : débogage d'un projet (C++)"
ms.date: 04/25/2019
helpviewer_keywords:
- projects [C++], debugging
- project debugging [C++]
- debugging projects
ms.assetid: a5cade77-ba51-4b03-a7a0-6897e3cd6a59
ms.openlocfilehash: 99e5af935c1d5985b8c472fc807b1afbe61d66b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318674"
---
# <a name="walkthrough-debugging-a-project-c"></a>Procédure pas à pas : débogage d'un projet (C++)

Dans cette procédure pas à pas, vous modifiez le programme pour résoudre le problème que vous avez détecté au moment du test du projet.

## <a name="prerequisites"></a>Prérequis

- Cette procédure pas à pas part du principe que vous comprenez les notions de base du langage C++.

- Elle suppose également que vous avez effectué les procédures pas à pas connexes précédentes listées dans [Utilisation de l’IDE Visual Studio pour le développement d’applications de bureau C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

### <a name="to-fix-a-program-that-has-a-bug"></a>Pour corriger un programme contenant un bogue

1. Pour voir ce qui se passe quand un objet `Cardgame` est détruit, examinez le destructeur de la classe `Cardgame`.

   Dans la barre de menus, choisissez **Afficher**  >  **affichage de classes**.

   Dans la fenêtre **Affichage de classes**, développez l’arborescence du projet **Game** et sélectionnez la classe **Cardgame** pour afficher les membres de classe et les méthodes.

   Ouvrez le menu contextuel du destructeur **~Cardgame(void)**, puis choisissez **Atteindre la définition**.

1. Pour réduire la valeur de `totalParticipants` quand un Cardgame se termine, ajoutez le code suivant entre les accolades du destructeur `Cardgame::~Cardgame`.

   [!code-cpp[NVC_Walkthrough_Debugging_A_Project#110](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_1.cpp)]

1. Le fichier Cardgame.cpp doit ressembler au code ci-dessous après le changement :

   [!code-cpp[NVC_Walkthrough_Debugging_A_Project#111](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_2.cpp)]

1. Dans la barre de menus, choisissez **générer**  >  **générer la solution**.

1. Une fois la génération terminée, exécutez-la en mode débogage en choisissant **Déboguer**  >  **Démarrer le débogage** dans la barre de menus, ou en appuyant sur la touche **F5** . Le programme s’interrompt au premier point d’arrêt.

1. Pour effectuer un pas à pas détaillé dans le programme, dans la barre de menus, choisissez **Déboguer**  >  **pas à pas principal** ou appuyez sur la touche **F10** .

   Notez qu’après l’exécution de chaque constructeur `Cardgame`, la valeur de `totalParticipants` augmente. Quand la fonction `PlayGames` retourne une réponse, chaque fois qu’une instance `Cardgame` est hors de portée et supprimée (et que le destructeur est appelé), `totalParticipants` diminue. Juste avant l' **`return`** exécution de l’instruction, est `totalParticipants` égal à 0.

1. Poursuivez l’exécution pas à pas du programme jusqu’à son arrêt, ou laissez-le s’exécuter en choisissant **Déboguer**  >  **exécuter** dans la barre de menus, ou en appuyant sur la touche **F5** .

## <a name="next-steps"></a>Étapes suivantes

**Précédent :** [Procédure pas à pas : test d’un projet (C++)](../ide/walkthrough-testing-a-project-cpp.md)<br/>
**Suivant :** [Procédure pas à pas : déploiement de votre programme (C++)](../ide/walkthrough-deploying-your-program-cpp.md)

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Projets et systèmes de build](../build/projects-and-build-systems-cpp.md)<br/>
