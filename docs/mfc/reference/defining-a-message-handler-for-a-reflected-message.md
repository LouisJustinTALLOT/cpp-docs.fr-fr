---
title: Définition d’un gestionnaire de messages pour un Message réfléchi | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.defining.msg.msghandler
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ed941816824c77f14a3364b06af0b3da171ee8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373167"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>Définition d'un gestionnaire de messages pour un message réfléchi
Une fois que vous avez créé une nouvelle classe de contrôle MFC, vous pouvez définir des gestionnaires de messages pour celle-ci. Gestionnaires de messages réfléchis permettent à votre classe de contrôle pour gérer ses propres messages avant que le message est reçu par le parent. Vous pouvez utiliser la bibliothèque MFC [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) fonction pour envoyer des messages à partir de votre contrôle à une fenêtre parente.  
  
 Cette fonctionnalité, par exemple, vous pouvez créer une zone de liste qui sera redessiner plutôt que de compter sur la fenêtre parente à faire c’est le cas (owner-drawn). Pour plus d’informations sur les messages réfléchis, consultez [gestion des Messages](../../mfc/handling-reflected-messages.md).  
  
 Pour créer un [contrôle ActiveX](../../mfc/activex-controls-on-the-internet.md) avec la même fonctionnalité, vous devez créer un projet pour le contrôle ActiveX.  
  
> [!NOTE]
>  Vous ne pouvez pas ajouter de message réfléchi (OCM_*Message*) pour un ActiveX contrôler à l’aide de la fenêtre Propriétés, comme décrit ci-dessous. Vous devez ajouter ces messages manuellement.  
  
### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-properties-window"></a>Pour définir un gestionnaire de messages pour un message réfléchi à partir de la fenêtre Propriétés  
  
1.  Ajouter un contrôle, telles qu’une liste, un contrôle rebar, une barre d’outils ou un contrôle d’arborescence, à votre projet MFC.  
  
2.  Dans l’affichage de classes, cliquez sur le nom de votre classe du contrôle.  
  
3.  Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), le nom de classe du contrôle s’affiche dans le **nom de la classe** liste.  
  
4.  Cliquez sur le **Messages** bouton pour afficher les messages Windows disponibles à ajouter au contrôle.  
  
5.  Faites défiler vers le bas la liste des messages dans la fenêtre Propriétés jusqu'à ce que l’en-tête **réfléchi**. Ou bien, cliquez sur le **catégories** bouton et réduire l’affichage pour voir les **réfléchi** titre.  
  
6.  Sélectionnez le message réfléchi pour lequel vous souhaitez définir un gestionnaire. Messages réfléchis sont marqués d’un signe égal (=).  
  
7.  Cliquez sur la cellule dans la colonne de droite dans la fenêtre Propriétés pour afficher le nom proposé pour le gestionnaire en tant que \<Ajouter >*HandlerName*. (Par exemple, le **= WM_CTLCOLOR** Gestionnaire de messages \<Ajouter >**CtlColor**).  
  
8.  Cliquez sur le nom suggéré pour l’accepter. Le gestionnaire est ajouté à votre projet.  
  
     Les noms de gestionnaires de messages que vous avez ajoutés s’affichent dans la colonne de droite de la fenêtre des messages réfléchis.  
  
9. Pour modifier ou supprimer un gestionnaire de messages, répétez les étapes 4 à 7. Cliquez sur la cellule qui contient le nom du gestionnaire à modifier ou supprimer et cliquez sur la tâche appropriée.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Messages à des fonctions](../../mfc/reference/mapping-messages-to-functions.md)   
 [Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)   
 [Ajout d’une fonction membre](../../ide/adding-a-member-function-visual-cpp.md)   
 [Ajout d’une Variable membre](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Une fonction virtuelle de substitution](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Gestionnaire de messages MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Navigation dans la Structure de classe](../../ide/navigating-the-class-structure-visual-cpp.md)
