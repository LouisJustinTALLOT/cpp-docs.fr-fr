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
ms.openlocfilehash: 723046fc1721cc46608e00f19a4431ef081be13d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366693"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>Mise à jour du texte d'un volet de barre d'état

Cet article explique comment modifier le texte qui apparaît dans un volet de barre d’état MFC. Une barre de statut — un objet de fenêtre de classe [CStatusBar](../mfc/reference/cstatusbar-class.md) — contient plusieurs « vitres ». Chaque volet est une zone rectangulaire de la barre d’état que vous pouvez utiliser pour afficher des informations. Par exemple, de nombreuses applications affichent l’état du CAPS LOCK, NUM LOCK et d’autres touches dans les vitres les plus droites. Les applications affichent aussi souvent du texte informatif dans la vitre la plus à gauche (volet 0), parfois appelée « volet message ». Par exemple, la barre d’état MFC par défaut utilise la vitre du message pour afficher une chaîne expliquant l’élément de menu ou le bouton de barre d’outils actuellement sélectionné. La figure dans [Status Bars](../mfc/status-bar-implementation-in-mfc.md) montre une barre de statut à partir d’une application MFC créée par Application Wizard.

Par défaut, MFC n’active pas une `CStatusBar` vitre lorsqu’elle crée la vitre. Pour activer une vitre, vous devez utiliser la ON_UPDATE_COMMAND_UI macro pour chaque volet sur la barre d’état et mettre à jour les vitres. Étant donné que les vitres n’envoient pas WM_COMMAND messages (ils ne sont pas comme les boutons de barre d’outils), vous devez taper le code manuellement.

Supposons, par exemple, `ID_INDICATOR_PAGE` qu’un volet ait comme identifiant de commande et qu’il contienne le numéro de page actuel dans un document. La procédure suivante décrit comment créer une nouvelle vitre dans la barre d’état.

### <a name="to-make-a-new-pane"></a>Pour faire un nouveau volet

1. Définissez l’ID de commande du volet.

   Sur le menu **View,** cliquez sur **Resource View**. Cliquez à droite sur la ressource du projet et cliquez sur **Les symboles de ressources**. Dans la boîte de dialogue `New`des symboles de ressources, cliquez . Tapez un nom d’identification de commande : par exemple, `ID_INDICATOR_PAGE`. Spécifier une valeur pour l’ID, ou accepter la valeur suggérée par la boîte de dialogue des symboles de ressources. Par exemple, `ID_INDICATOR_PAGE`par exemple, acceptez la valeur par défaut. Fermez la boîte de dialogue des symboles de ressources.

1. Définissez une chaîne par défaut pour afficher dans la vitre.

   Avec Resource View ouvert, **table à deux clics** dans la fenêtre qui répertorie les types de ressources pour votre application. Avec l’éditeur **String Table** ouvert, choisissez **New String** dans le menu **Insert.** Sélectionnez l’ID de commande de `ID_INDICATOR_PAGE`votre volet (par exemple) et tapez une valeur de chaîne par défaut, comme « Page ». Fermez l’éditeur de cordes. (Vous avez besoin d’une chaîne par défaut pour éviter une erreur de compilateur.)

1. Ajouter la vitre au tableau *des indicateurs.*

   Dans le fichier MAINFRM. RPC, localisez le tableau *des indicateurs.* Ce tableau répertorie les Œd de commande pour tous les indicateurs de la barre d’état, afin de gauche à droite. Au point approprié du tableau, entrez l’ID de commande `ID_INDICATOR_PAGE`de votre volet, comme indiqué ici pour :

   [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]

La façon recommandée d’afficher le texte `SetText` dans une `CCmdUI` vitre est d’appeler la fonction membre de la classe dans une fonction de gestionnaire de mise à jour pour la vitre. Par exemple, vous pouvez configurer une *variable d’intégrage m_nPage* qui `SetText` contient le numéro de page actuel et l’utiliser pour définir le texte du volet sur une version de ce numéro.

> [!NOTE]
> L’approche `SetText` est recommandée. Il est possible d’effectuer cette tâche à `CStatusBar` un `SetPaneText`niveau légèrement inférieur en appelant la fonction membre . Malgré cela, vous avez toujours besoin d’un gestionnaire de mise à jour. Sans un tel gestionnaire pour la vitre, MFC désactive automatiquement la vitre, effaçant son contenu.

La procédure suivante montre comment utiliser une fonction de gestionnaire de mise à jour pour afficher le texte dans une vitre.

#### <a name="to-make-a-pane-display-text"></a>Pour faire un texte d’affichage de volet

1. Ajoutez un gestionnaire de mise à jour de commande pour la commande.

   Ajouter manuellement un prototype pour le `ID_INDICATOR_PAGE` gestionnaire, comme indiqué ici pour (dans MAINFRM. H):

   [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]

1. Dans le approprié . Fichier du RPC, ajouter la définition du `ID_INDICATOR_PAGE` gestionnaire, comme indiqué ici pour (dans MAINFRM. RPC:

   [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]

   Les trois dernières lignes de ce gestionnaire sont le code qui affiche votre texte.

1. Dans la carte de message appropriée, ajoutez le ON_UPDATE_COMMAND_UI `ID_INDICATOR_PAGE` macro, comme indiqué ici pour (dans MAINFRM. RPC:

   [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]

Une fois que vous *m_nPage* définissez la valeur de `CMainFrame`la variable m_nPage membre (de classe), cette technique fait apparaître le numéro de page dans le volet pendant le traitement au ralenti de la même manière que l’application met à jour d’autres indicateurs. Si *m_nPage* change, l’affichage change au cours de la prochaine boucle de ralenti.

### <a name="what-do-you-want-to-know-more-about"></a>Qu’est-ce que vous voulez savoir plus sur

- [Mise à jour des objets d’interface utilisateur (comment mettre à jour les boutons de la barre d’outils et les éléments de menu au fur et à mesure que les conditions du programme changent)](../mfc/how-to-update-user-interface-objects.md)

## <a name="see-also"></a>Voir aussi

[Implémentation de la barre d'état dans MFC](../mfc/status-bar-implementation-in-mfc.md)<br/>
[Classe CStatusBar](../mfc/reference/cstatusbar-class.md)
