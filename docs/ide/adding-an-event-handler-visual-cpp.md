---
title: Ajout d’un gestionnaire d’événements (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.eventhandler.overview
dev_langs:
- C++
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 184161b22358f77845b5f7c4b6da0bb42f3ea15f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324913"
---
# <a name="adding-an-event-handler-visual-c"></a>Ajout d'un gestionnaire d'événements (Visual C++)
À partir de l’éditeur de ressources, vous pouvez ajouter un nouveau gestionnaire d’événements ou modifier un gestionnaire existant pour un contrôle de boîte de dialogue en recourant à [l’Assistant Gestionnaire d’événements](../ide/event-handler-wizard.md).  
  
 Vous pouvez ajouter un événement à la classe implémentant la boîte de dialogue à l’aide de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Si vous souhaitez ajouter l’événement à une classe autre que celle de la boîte de dialogue, utilisez l’Assistant Gestionnaire d’événements.  
  
### <a name="to-add-an-event-handler-to-a-dialog-box-control"></a>Pour ajouter un gestionnaire d’événements à un contrôle de boîte de dialogue  
  
1.  Double-cliquez sur la ressource boîte de dialogue dans [l’affichage des ressources](../windows/resource-view-window.md) pour ouvrir la ressource boîte de dialogue qui contient le contrôle dans [l’Éditeur de boîtes de dialogue](../windows/dialog-editor.md).  
  
2.  Cliquez avec le bouton droit sur le contrôle pour lequel vous souhaitez gérer l’événement de notification.  
  
3.  Dans le menu contextuel, cliquez sur **Ajouter un gestionnaire d’événements** pour afficher l’Assistant Gestionnaire d’événements.  
  
4.  Dans la zone **Type de message**, sélectionnez l’événement à ajouter à la classe sélectionnée dans la zone **Liste de classes**.  
  
5.  Acceptez le nom par défaut de la zone **Nom du gestionnaire de fonctions** ou indiquez le nom de votre choix.  
  
6.  Cliquez sur **Ajouter et modifier** pour ajouter le gestionnaire d’événements au projet et ouvrir l’éditeur de texte à l’emplacement de la nouvelle fonction pour ajouter le code approprié du gestionnaire d’événements.  
  
     Si le type de message sélectionné possède déjà un gestionnaire d’événements pour la classe sélectionnée, **Ajouter et modifier** n’est pas disponible contrairement à **Modifier le code**. Cliquez sur **Modifier le code** pour ouvrir l’éditeur de texte à l’emplacement de la fonction existante.  
  
 Une autre solution consiste à ajouter les gestionnaires d’événements à partir de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Pour plus d’informations, consultez [Ajout de gestionnaires d’événements pour les contrôles de boîte de dialogue](../windows/adding-event-handlers-for-dialog-box-controls.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de fonctionnalités à l’aide des Assistants Code](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md)   
 [Ajout d’une variable membre](../ide/adding-a-member-variable-visual-cpp.md)   
 [Ajout d’une fonction membre](../ide/adding-a-member-function-visual-cpp.md)   
 [Gestionnaire de messages MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Parcours de la structure de classe](../ide/navigating-the-class-structure-visual-cpp.md)