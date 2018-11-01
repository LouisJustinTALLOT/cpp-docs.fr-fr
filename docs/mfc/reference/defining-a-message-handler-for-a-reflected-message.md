---
title: Définition d'un gestionnaire de messages pour un message réfléchi
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.defining.msg.msghandler
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
ms.openlocfilehash: 89cb1631be7b8588d02518eacbc93b466a275828
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531874"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>Définition d'un gestionnaire de messages pour un message réfléchi

Une fois que vous avez créé une nouvelle classe de contrôle MFC, vous pouvez définir des gestionnaires de messages pour celle-ci. Gestionnaires de messages réfléchis permettent à votre classe de contrôle pour gérer ses propres messages avant que le message est reçu par le parent. Vous pouvez utiliser la bibliothèque MFC [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) (fonction) pour envoyer des messages à partir de votre contrôle à une fenêtre parente.

Cette fonctionnalité, par exemple, vous pouvez créer une zone de liste qui se redessine elle-même plutôt que de compter sur la fenêtre parente à faire c’est le cas (owner-drawn). Pour plus d’informations sur les messages réfléchis, consultez [gestion des Messages](../../mfc/handling-reflected-messages.md).

Pour créer un [contrôle ActiveX](../../mfc/activex-controls-on-the-internet.md) avec la même fonctionnalité, vous devez créer un projet pour le contrôle ActiveX.

> [!NOTE]
>  Vous ne pouvez pas ajouter un message réfléchi (OCM_*Message*) pour un ActiveX contrôler à l’aide de la fenêtre Propriétés, comme décrit ci-dessous. Vous devez ajouter ces messages manuellement.

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-properties-window"></a>Pour définir un gestionnaire de messages pour un message réfléchi à partir de la fenêtre Propriétés

1. Ajouter un contrôle, telles qu’une liste, un contrôle rebar, une barre d’outils ou un contrôle d’arborescence, à votre projet MFC.

1. Dans l’affichage de classes, cliquez sur le nom de votre classe de contrôle.

1. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), le nom de classe de contrôle s’affiche dans le **nom de la classe** liste.

1. Cliquez sur le **Messages** bouton pour afficher les messages Windows disponibles à ajouter au contrôle.

1. Défilement vers le bas de la liste des messages dans la fenêtre Propriétés jusqu'à ce que vous voyiez l’en-tête **réfléchi**. Ou bien, cliquez sur le **catégories** bouton et réduire la vue pour voir les **réfléchi** titre.

1. Sélectionnez le message réfléchi pour lequel vous souhaitez définir un gestionnaire. Messages réfléchis sont marqués par un signe égal (=).

1. Cliquez sur la cellule dans la colonne de droite dans la fenêtre Propriétés pour afficher le nom proposé pour le gestionnaire en tant que \<Ajouter >*HandlerName*. (Par exemple, le **= WM_CTLCOLOR** Gestionnaire de messages \<Ajouter >**CtlColor**).

1. Cliquez sur le nom suggéré pour accepter. Le gestionnaire est ajouté à votre projet.

   Les noms de gestionnaires de messages que vous avez ajoutés s’affichent dans la colonne de droite de la fenêtre de messages réfléchis.

9. Pour modifier ou supprimer un gestionnaire de messages, répétez les étapes 4 à 7. Cliquez sur la cellule qui contient le nom du gestionnaire à modifier ou supprimer et cliquez sur la tâche appropriée.

## <a name="see-also"></a>Voir aussi

[Mappage des messages à des fonctions](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Ajout d’une fonction membre](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Ajout d’une variable membre](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Substitution d’une fonction virtuelle](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Gestionnaire de messages MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Parcours de la structure de classe](../../ide/navigating-the-class-structure-visual-cpp.md)
