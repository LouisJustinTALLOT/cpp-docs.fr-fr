---
title: Mappage des Messages à des fonctions | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.mapping.msg.function
dev_langs:
- C++
helpviewer_keywords:
- Windows messages [MFC], adding message handlers
- message maps [MFC], mapping messages to functions
ms.assetid: a7727a62-f638-4b20-b7f5-131f47200d6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 962a86139b7fdf8afac08e04e7b42240603b4374
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335524"
---
# <a name="mapping-messages-to-functions"></a>Mappage de messages à des fonctions
La fenêtre Propriétés vous permet de lier des gestionnaires de messages (fonctions membres des classes d’interface utilisateur MFC) les messages générés par les ressources de votre application. Ils utilisent [tables des messages MFC](../../mfc/messages-and-commands-in-the-framework.md) pour créer la liaison.  
  
 Lorsque vous utilisez l’affichage de classes pour créer une nouvelle classe dérivée à partir d’une des classes de framework, il automatiquement place un complets et fonctionnels fichiers de classes dans l’en-tête (.h) et l’implémentation (.cpp) que vous spécifiez.  
  
> [!NOTE]
>  Pour ajouter une nouvelle classe qui ne gère pas les messages, créer la classe directement dans l’éditeur de texte.  
  
### <a name="to-define-or-remove-a-message-handler-using-the-properties-window"></a>Pour définir ou supprimer un gestionnaire de messages à l’aide de la fenêtre Propriétés  
  
1.  Dans Affichage de classes, cliquez sur la classe.  
  
2.  Dans la fenêtre Propriétés, cliquez sur le **Messages** bouton.  
  
    > [!NOTE]
    >  Le **Messages** bouton est disponible lorsque vous sélectionnez le nom de classe dans l’affichage de classes ou lorsque vous cliquez sur dans la fenêtre source.  
  
     Si votre projet a un gestionnaire pour un message, le nom du gestionnaire apparaît dans la colonne de droite en regard du message.  
  
3.  Si le message n’a aucun gestionnaire, puis cliquez sur la cellule dans la colonne de droite dans la fenêtre Propriétés pour afficher le nom proposé pour le gestionnaire en tant que \<Ajouter >*HandlerName*. (Par exemple, le Gestionnaire de messages WM_TIMER suggère \<Ajouter >`OnTimer`).  
  
4.  Cliquez sur le nom suggéré pour ajouter du code stub pour la fonction.  
  
5.  Pour modifier un gestionnaire de messages, double-cliquez sur le message dans l’affichage de classes et modifiez le code dans la fenêtre source.  
  
 Pour supprimer un gestionnaire de messages, double-cliquez sur le gestionnaire dans la colonne de droite et sélectionnez \<Supprimer >*HandlerName*. Le code de la fonction est commenté.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de messages MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)   
 [Ajout d’une fonction membre](../../ide/adding-a-member-function-visual-cpp.md)   
 [Ajout d’une variable membre](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Substitution d’une fonction virtuelle](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Ajout de gestionnaires d’événements pour les contrôles de boîte de dialogue](../../windows/adding-event-handlers-for-dialog-box-controls.md)   
 [Parcours de la structure de classe](../../ide/navigating-the-class-structure-visual-cpp.md)
