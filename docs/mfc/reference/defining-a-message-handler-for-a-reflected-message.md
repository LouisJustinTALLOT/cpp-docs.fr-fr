---
title: Définition d'un gestionnaire de messages pour un message réfléchi
ms.date: 09/07/2019
f1_keywords:
- vc.codewiz.defining.msg.msghandler
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
ms.openlocfilehash: 1e38c63464cacf445688a1d431a65af21eac86f4
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907940"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>Définition d'un gestionnaire de messages pour un message réfléchi

Une fois que vous avez créé une classe de contrôle MFC, vous pouvez définir des gestionnaires de messages pour celle-ci. Les gestionnaires de messages réfléchis permettent à votre classe de contrôle de gérer ses propres messages avant que le message ne soit reçu par le parent. Vous pouvez utiliser la fonction MFC [CWnd :: SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) pour envoyer des messages de votre contrôle à une fenêtre parente.

Avec cette fonctionnalité, vous pouvez, par exemple, créer une zone de liste qui se redessine, plutôt que de s’appuyer sur la fenêtre parente pour le faire (propriétaire dessiné). Pour plus d’informations sur les messages reflétés, consultez [gestion des messages réfléchis](../../mfc/handling-reflected-messages.md).

Pour créer un [contrôle ActiveX](../../mfc/activex-controls-on-the-internet.md) avec la même fonctionnalité, vous devez créer un projet pour le contrôle ActiveX.

> [!NOTE]
>  Vous ne pouvez pas ajouter un message réfléchi (*message*OCM_) pour un contrôle ActiveX à l’aide de l’Assistant classe, comme décrit ci-dessous. Vous devez ajouter ces messages manuellement.

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-class-wizard"></a>Pour définir un gestionnaire de messages pour un message réfléchi à partir de l’Assistant classe

1. Ajoutez un contrôle, tel qu’une liste, un contrôle rebar, une barre d’outils ou un contrôle d’arborescence, à votre projet MFC.

1. Dans Affichage de classes, cliquez sur le nom de votre classe de contrôle.

1. Dans l' [Assistant classe](mfc-class-wizard.md), le nom de la classe de contrôle apparaît dans la liste nom de la **classe** .

1. Cliquez sur l’onglet **messages** pour afficher les messages Windows que vous pouvez ajouter au contrôle.

1. Sélectionnez le message réfléchi pour lequel vous souhaitez définir un gestionnaire. Les messages réfléchis sont marqués d’un signe égal (=).

1. Cliquez sur la cellule dans la colonne de droite de l’Assistant classe pour afficher le nom suggéré du gestionnaire \<en tant qu’ajout >*HandlerName*. (Par exemple, le gestionnaire de messages **= WM_CTLCOLOR** suggère \<Add >**CTLCOLOR**).

1. Cliquez sur le nom suggéré à accepter. Le gestionnaire est ajouté à votre projet.

1. Pour modifier ou supprimer un gestionnaire de messages, répétez les étapes 4 à 7. Cliquez sur la cellule contenant le nom du gestionnaire à modifier ou à supprimer, puis cliquez sur la tâche appropriée.

## <a name="see-also"></a>Voir aussi

[Mappage des messages à des fonctions](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Ajout d’une fonction membre](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Ajout d’une variable membre](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Substitution d’une fonction virtuelle](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Gestionnaire de messages MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Parcours de la structure de classe](../../ide/navigate-code-cpp.md)
