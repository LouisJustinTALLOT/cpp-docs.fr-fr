---
title: Définition d'un gestionnaire de messages pour un message réfléchi
ms.date: 09/07/2019
f1_keywords:
- vc.codewiz.defining.msg.msghandler
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
ms.openlocfilehash: f7f90d3347ac61abcfcb48e77ef39aa2626ae5c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365855"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>Définition d'un gestionnaire de messages pour un message réfléchi

Une fois que vous avez créé une nouvelle classe de contrôle MFC, vous pouvez définir les gestionnaires de messages pour cela. Les gestionnaires de messages réfléchis permettent à votre classe de contrôle de gérer ses propres messages avant que le message ne soit reçu par le parent. Vous pouvez utiliser le MFC [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) fonction pour envoyer des messages de votre contrôle à une fenêtre parente.

Avec cette fonctionnalité, vous pourriez, par exemple, créer une boîte de liste qui va se redessiner plutôt que de compter sur la fenêtre parente pour le faire (propriétaire dessiné). Pour plus d’informations sur les messages réfléchis, voir [Handling Reflected Messages](../../mfc/handling-reflected-messages.md).

Pour créer un [contrôle ActiveX](../../mfc/activex-controls-on-the-internet.md) avec la même fonctionnalité, vous devez créer un projet pour le contrôle ActiveX.

> [!NOTE]
> Vous ne pouvez pas ajouter un message réfléchi (OCM_*Message*) pour un contrôle ActiveX à l’aide de l’assistant de classe, tel que décrit ci-dessous. Vous devez ajouter ces messages manuellement.

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-class-wizard"></a>Définir un gestionnaire de message pour un message réfléchi de l’assistant de classe

1. Ajoutez un contrôle, comme une liste, un contrôle des barres d’armature, une barre d’outils ou un contrôle des arbres, à votre projet MFC.

1. Dans la vue de classe, cliquez sur le nom de votre classe de contrôle.

1. Dans le [Class Wizard](mfc-class-wizard.md), le nom de la classe de contrôle apparaît dans la liste de nom **de classe.**

1. Cliquez sur l’onglet **Messages** pour afficher les messages Windows disponibles pour ajouter au contrôle.

1. Sélectionnez le message réfléchi pour lequel vous souhaitez définir un gestionnaire. Les messages réfléchis sont marqués d’un signe égal ( ).

1. Cliquez sur la cellule dans la colonne droite dans le \<Maître de classe pour afficher le nom suggéré du gestionnaire comme ajouter>*HandlerName*. (Par exemple, le gestionnaire **de** message \<WM_CTLCOLOR suggère d’ajouter>**CtlColor**).

1. Cliquez sur le nom suggéré pour accepter. Le gestionnaire est ajouté à votre projet.

1. Pour modifier ou supprimer un gestionnaire de message, répétez les étapes 4 à 7. Cliquez sur la cellule contenant le nom du gestionnaire pour modifier ou supprimer et cliquer sur la tâche appropriée.

## <a name="see-also"></a>Voir aussi

[Mappage de messages à des fonctions](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Ajout d’une fonction membre](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Ajout d’une variable membre](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Substitution d’une fonction virtuelle](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Gestionnaire de messages MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Parcours de la structure de classe](../../ide/navigate-code-cpp.md)
