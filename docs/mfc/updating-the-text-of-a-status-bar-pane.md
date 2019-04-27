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
ms.openlocfilehash: baf5013e34f262dd3bfed82941697ab9ca21e637
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180783"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>Mise à jour du texte d'un volet de barre d'état

Cet article explique comment modifier le texte qui apparaît dans un volet de barre d’état MFC. Une barre d’état, un objet de fenêtre de la classe [CStatusBar](../mfc/reference/cstatusbar-class.md) — contient plusieurs « volets ». Chaque volet est une zone rectangulaire de la barre d’état que vous pouvez utiliser pour afficher des informations. Par exemple, de nombreuses applications affichent l’état de la touche MAJ, VERR. NUM et autres touches dans les volets plus à droite. Applications également souvent affichent des informations dans le volet de gauche (volet 0), parfois appelée « volet de message. » Par exemple, la barre d’état MFC par défaut utilise le volet de message pour afficher une chaîne décrivant le bouton de barre d’outils ou élément de menu actuellement sélectionné. La figure dans [barres d’état](../mfc/status-bar-implementation-in-mfc.md) affiche une barre d’état à partir d’une application MFC créé par l’Assistant de l’Application.

Par défaut, MFC n’active pas un `CStatusBar` volet lorsqu’il crée le volet. Pour activer un volet, vous devez utiliser la macro ON_UPDATE_COMMAND_UI pour chaque volet dans la barre d’état et mettre à jour les volets. Étant donné que les volets n’envoient pas de messages WM_COMMAND (ils ne sont pas comme des boutons de barre d’outils), vous devez taper le code manuellement.

Par exemple, supposons qu’un d’eux a `ID_INDICATOR_PAGE` en tant que son identificateur de commande et qui, elle contient le numéro de page dans un document. La procédure suivante décrit comment créer un nouveau volet dans la barre d’état.

### <a name="to-make-a-new-pane"></a>Pour créer un nouveau volet

1. Définir l’ID de commande. du volet

   Sur le **vue** menu, cliquez sur **affichage des ressources**. Avec le bouton droit de la ressource de projet et cliquez sur **symboles des ressources**. Dans la boîte de dialogue Symboles des ressources, cliquez sur `New`. Tapez un nom d’ID de commande : par exemple, `ID_INDICATOR_PAGE`. Spécifiez une valeur pour l’ID ou acceptez la valeur proposée dans la boîte de dialogue Symboles des ressources. Par exemple, pour `ID_INDICATOR_PAGE`, acceptez la valeur par défaut. Fermez la boîte de dialogue Symboles des ressources.

1. Définir une chaîne par défaut à afficher dans le volet.

   Affichage des ressources ouvrir, puis double-cliquez sur **Table de chaînes** dans la fenêtre qui répertorie les types de ressources pour votre application. Avec le **Table de chaînes** éditeur ouvert, choisissez **nouvelle chaîne** à partir de la **insérer** menu. Dans la fenêtre Propriétés de chaîne, sélectionnez l’ID de volet commande (par exemple, `ID_INDICATOR_PAGE`) et tapez une valeur de chaîne par défaut, tels que « Page ». Fermez l’éditeur de chaîne. (Vous avez besoin une chaîne par défaut pour éviter une erreur du compilateur).

1. Ajouter le volet à la *indicateurs* tableau.

   Dans le fichier MAINFRM. CPP, recherchez le *indicateurs* tableau. Ce tableau répertorie les ID de commande pour tous les indicateurs de la barre d’état, dans l’ordre de gauche à droite. Au point approprié dans le tableau, entrez l’ID de volet commande, comme indiqué ici pour `ID_INDICATOR_PAGE`:

   [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]

La méthode recommandée pour afficher du texte dans un volet consiste à appeler le `SetText` fonction membre de classe `CCmdUI` dans une fonction de gestionnaire de mise à jour pour le volet. Par exemple, vous souhaiterez peut-être définir une variable entière *m_nPage* qui contient le numéro de page actuel et l’utilisation `SetText` pour définir du texte du volet vers une version de chaîne de ce nombre.

> [!NOTE]
>  Le `SetText` approche est recommandée. Il est possible d’effectuer cette tâche à un niveau légèrement inférieur en appelant le `CStatusBar` fonction membre `SetPaneText`. Même dans ce cas, vous devez toujours un gestionnaire de mise à jour. Sans ce gestionnaire pour le volet, MFC désactive automatiquement le volet, effacer son contenu.

La procédure suivante montre comment utiliser une fonction de gestionnaire de mise à jour pour afficher le texte dans un volet.

#### <a name="to-make-a-pane-display-text"></a>Pour afficher un volet de texte

1. Ajoutez un gestionnaire de mise à jour de commande pour la commande.

   Ajouter manuellement un prototype pour le gestionnaire, comme indiqué ici pour `ID_INDICATOR_PAGE` (dans MAINFRM. (H) :

   [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]

1. Dans les zones appropriées. CPP, ajoutez la définition du gestionnaire, comme indiqué ici pour `ID_INDICATOR_PAGE` (dans MAINFRM. (CPP) :

   [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]

   Les trois dernières lignes de ce gestionnaire sont le code qui affiche votre texte.

1. Dans la table des messages appropriés, ajoutez la macro ON_UPDATE_COMMAND_UI, comme indiqué ici pour `ID_INDICATOR_PAGE` (dans MAINFRM. (CPP) :

   [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]

Une fois que vous définissez la valeur de la *m_nPage* variable membre (de classe `CMainFrame`), cette technique provoque le numéro de page dans le volet pendant le traitement inactif de la même manière que l’application met à jour les autres indicateurs. Si *m_nPage* modifications, l’affichage change pendant la boucle inactive suivante.

### <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [La mise à jour des objets d’interface utilisateur (comment mettre à jour des éléments de menu et boutons de barre d’outils en tant que programme conditions changent)](../mfc/how-to-update-user-interface-objects.md)

## <a name="see-also"></a>Voir aussi

[Implémentation de la barre d’état dans MFC](../mfc/status-bar-implementation-in-mfc.md)<br/>
[CStatusBar, classe](../mfc/reference/cstatusbar-class.md)
