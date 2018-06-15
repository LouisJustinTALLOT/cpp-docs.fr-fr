---
title: 'Procédure pas à pas : Test d’un projet (C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- project testing [C++]
- testing projects
- projects [C++], testing
ms.assetid: 88cdd377-c5c8-4201-889d-32f5653ebead
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a9455fa9bf3c9f903f5018a1263978913aa35b2
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33333562"
---
# <a name="walkthrough-testing-a-project-c"></a>Procédure pas à pas : test d'un projet (C++)
Quand vous exécutez un programme en mode débogage, vous pouvez utiliser des points d’arrêt pour interrompre le programme afin d’examiner l’état des variables et des objets.  
  
 Dans cette procédure pas à pas, vous observez la valeur d’une variable que le programme exécute et comprenez pourquoi la valeur ne correspond pas à celle que vous attendez.  
  
## <a name="prerequisites"></a>Prérequis  
  
-   Cette procédure pas à pas part du principe que vous comprenez les notions de base du langage C++.  
  
-   Elle suppose également que vous avez effectué les procédures pas à pas connexes précédentes répertoriées dans [Utilisation de l’IDE Visual Studio pour le développement d’applications de bureau C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
### <a name="to-run-a-program-in-debug-mode"></a>Pour exécuter le programme en mode débogage  
  
1.  Ouvrez TestGames.cpp pour le modifier.  
  
2.  Sélectionnez cette ligne de code :  
  
     `Cardgame.solitaire(1);`  
  
3.  Pour définir un point d’arrêt sur cette ligne, dans la barre de menus, choisissez **Déboguer**, **Basculer le point d’arrêt** ou appuyez sur F9. Un cercle rouge apparaît à gauche de la ligne. Il indique qu’un point d’arrêt est défini. Pour supprimer un point d’arrêt, vous pouvez choisir la commande de menu ou réappuyer sur F9.  
  
     Si vous utilisez une souris, vous pouvez aussi définir ou supprimer un point d’arrêt en cliquant dans la marge de gauche.  
  
4.  Dans la barre de menus, choisissez **Déboguer**, **Démarrer le débogage** ou appuyez sur F5.  
  
     Quand le programme atteint la ligne contenant le point d’arrêt, l’exécution s’arrête temporairement, car votre programme est en mode Arrêt. Une flèche jaune à la gauche d’une ligne de code indique qu’il s’agit de la ligne suivante à exécuter.  
  
5.  Pour examiner la valeur de la variable `Cardgame::totalParticipants`, déplacez le pointeur sur `Cardgame`, puis déplacez-le sur le contrôle d’extension à gauche de la fenêtre d’info-bulle. Le nom de variable `totalParticipants` et sa valeur (12) sont affichés.  
  
     Ouvrez le menu contextuel de la variable `Cardgame::totalParticipants`, puis choisissez **Ajouter un espion** pour afficher cette variable dans la fenêtre **Espion 1**. Vous pouvez aussi sélectionner une variable et la faire glisser dans la fenêtre **Espion 1**.  
  
6.  Pour passer à la ligne de code suivante, dans la barre de menus, choisissez **Déboguer**, **Pas à pas principal** ou appuyez sur F10.  
  
     La valeur de `Cardgame::totalParticipants` dans la fenêtre **Espion 1** est maintenant affichée comme étant 13.  
  
7.  Ouvrez le menu contextuel de l’instruction `return 0;`, puis choisissez **Exécuter jusqu’au curseur**. La flèche jaune à gauche du code pointe vers l’instruction suivante à exécuter.  
  
8.  Le nombre `Cardgame::totalParticipants` doit diminuer quand un Cardgame se termine. À ce stade, `Cardgame::totalParticipants` doit être égal à 0, car toutes les instances de Cardgame ont été supprimées, mais la fenêtre **Espion 1** indique que `Cardgame::totalparticipants` est égal à 18. Il y a donc un bogue dans le code, que vous pouvez détecter et corriger en effectuant la procédure pas à pas suivante, [Procédure pas à pas : Débogage d’un projet (C++)](../ide/walkthrough-debugging-a-project-cpp.md).  
  
9. Pour arrêter le programme, dans la barre de menus, choisissez **Déboguer**, **Arrêter le débogage** ou appuyez sur le raccourci MAJ + F5.  
  
## <a name="next-steps"></a>Étapes suivantes  
 **Précédent :** [Procédure pas à pas : Génération d’un projet (C++)](../ide/walkthrough-building-a-project-cpp.md) &#124; **Suivant :**[Procédure pas à pas : Débogage d’un projet (C++)](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)   
 [Génération de programmes C/C++](../build/building-c-cpp-programs.md)