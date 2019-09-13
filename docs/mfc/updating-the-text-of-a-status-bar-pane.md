---
title: Mise à jour du texte d'un volet de barre d'état
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- ON_UPDATE_COMMAND_UI macro [MFC]
- user interface objects [MFC], updating
- text, status bar
- CStatusBar class [MFC], updating
- SetText method [MFC]
- panes, status bar
- status bars [MFC], updating
ms.assetid: 4984a3f4-9905-4d8c-a927-dca19781053b
ms.openlocfilehash: 20cd519f15fa9b218bca3dd1348659cfd0d5e473
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907634"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>Mise à jour du texte d'un volet de barre d'état

Cet article explique comment modifier le texte qui s’affiche dans un volet de barre d’État MFC. Une barre d’État (un objet Window de la classe [CStatusBar](../mfc/reference/cstatusbar-class.md) ) contient plusieurs « volets ». Chaque volet est une zone rectangulaire de la barre d’État que vous pouvez utiliser pour afficher des informations. Par exemple, de nombreuses applications affichent l’état de Verr. MAJ, Verr. NUM et autres clés dans les volets les plus à droite. Les applications affichent souvent du texte informatif dans le volet le plus à gauche (volet 0), parfois appelé « volet de message ». Par exemple, la barre d’État MFC par défaut utilise le volet message pour afficher une chaîne expliquant l’élément de menu ou le bouton de barre d’outils actuellement sélectionné. La figure dans les [barres d’État](../mfc/status-bar-implementation-in-mfc.md) affiche une barre d’État à partir d’une application MFC créée par l’Assistant Application.

Par défaut, MFC n’active pas un `CStatusBar` volet lorsqu’il crée le volet. Pour activer un volet, vous devez utiliser la macro ON_UPDATE_COMMAND_UI pour chaque volet de la barre d’État et mettre à jour les volets. Étant donné que les volets n’envoient pas de messages WM_COMMAND (ils ne sont pas similaires aux boutons de la barre d’outils), vous devez taper le code manuellement.

Par exemple, supposons qu’un `ID_INDICATOR_PAGE` volet ait comme identificateur de commande et qu’il contient le numéro de page actuel dans un document. La procédure suivante décrit comment créer un nouveau volet dans la barre d’État.

### <a name="to-make-a-new-pane"></a>Pour créer un nouveau volet

1. Définissez l’ID de commande du volet.

   Dans le menu **affichage** , cliquez sur **affichage des ressources**. Cliquez avec le bouton droit sur la ressource de projet, puis cliquez sur **symboles des ressources**. Dans la boîte de dialogue symboles des ressources `New`, cliquez sur. Tapez un nom d’ID de commande : par `ID_INDICATOR_PAGE`exemple,. Spécifiez une valeur pour l’ID ou acceptez la valeur suggérée par la boîte de dialogue symboles des ressources. Par exemple, pour `ID_INDICATOR_PAGE`, acceptez la valeur par défaut. Fermez la boîte de dialogue symboles des ressources.

1. Définissez une chaîne par défaut à afficher dans le volet.

   Avec Affichage des ressources ouvrir, double-cliquez sur **table de chaînes** dans la fenêtre qui répertorie les types de ressources pour votre application. Avec l’éditeur de **table de chaînes** ouvert, choisissez **nouvelle chaîne** dans le menu **insertion** . Sélectionnez l’ID de commande de votre volet (par `ID_INDICATOR_PAGE`exemple,) et tapez une valeur de chaîne par défaut, telle que « page ». Fermez l’éditeur de chaînes. (Vous avez besoin d’une chaîne par défaut pour éviter une erreur du compilateur.)

1. Ajoutez le volet au tableau des *indicateurs* .

   Dans le fichier MAINFRM. CPP, recherchez le tableau *indicators* . Ce tableau répertorie les ID de commande pour tous les indicateurs de la barre d’État, dans l’ordre, de gauche à droite. Au point approprié dans le tableau, entrez l’ID de commande du volet, comme illustré ici `ID_INDICATOR_PAGE`:

   [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]

La méthode recommandée pour afficher du texte dans un volet est d’appeler `SetText` la fonction membre de `CCmdUI` la classe dans une fonction de gestionnaire de mise à jour pour le volet. Par exemple, vous souhaiterez peut-être configurer une variable entière *m_nPage* qui contient le numéro de page actuel `SetText` et utiliser pour définir le texte du volet sur une version de chaîne de ce nombre.

> [!NOTE]
>  L' `SetText` approche est recommandée. Il est possible d’effectuer cette tâche à un niveau légèrement inférieur en appelant la `CStatusBar` fonction `SetPaneText`membre. Même dans ce cas, vous avez toujours besoin d’un gestionnaire de mise à jour. Sans ce gestionnaire pour le volet, MFC désactive automatiquement le volet, en effaçant son contenu.

La procédure suivante montre comment utiliser une fonction de gestionnaire de mise à jour pour afficher du texte dans un volet.

#### <a name="to-make-a-pane-display-text"></a>Pour afficher le texte d’un volet

1. Ajoutez un gestionnaire de mise à jour de commande pour la commande.

   Ajoutez manuellement un prototype pour le gestionnaire, comme indiqué ici pour `ID_INDICATOR_PAGE` (dans MainFrm. H) :

   [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]

1. Dans le approprié. CPP, ajoutez la définition du gestionnaire, comme indiqué ici pour `ID_INDICATOR_PAGE` (dans MainFrm. CPP) :

   [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]

   Les trois dernières lignes de ce gestionnaire sont le code qui affiche votre texte.

1. Dans la table des messages appropriée, ajoutez la macro ON_UPDATE_COMMAND_UI, comme indiqué ici `ID_INDICATOR_PAGE` pour (dans MainFrm. CPP) :

   [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]

Une fois que vous avez défini la valeur de la variable membre m_nPage `CMainFrame`(de la classe), cette technique entraîne l’affichage du numéro de page dans le volet pendant le traitement inactif de la même manière que l’application met à jour d’autres indicateurs. Si *m_nPage* change, l’affichage change pendant la boucle inactive suivante.

### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Mise à jour des objets d’interface utilisateur (comment mettre à jour les boutons de barre d’outils et les éléments de menu en cas de modification des conditions du programme)](../mfc/how-to-update-user-interface-objects.md)

## <a name="see-also"></a>Voir aussi

[Implémentation de la barre d’état dans MFC](../mfc/status-bar-implementation-in-mfc.md)<br/>
[CStatusBar, classe](../mfc/reference/cstatusbar-class.md)
