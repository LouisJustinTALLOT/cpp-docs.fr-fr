---
title: 'Conteneurs de contrôles ActiveX : Gestion des événements à partir d’un contrôle ActiveX | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handlers [MFC], ActiveX controls
- ActiveX control containers [MFC], event sinks
- event handling [MFC], ActiveX controls
- ON_EVENT macro [MFC]
- ActiveX controls [MFC], events [MFC]
- END_EVENTSINK_MAP macro, using
- events [MFC], ActiveX controls
- BEGIN_EVENTSINK_MAP macro
ms.assetid: f9c106db-052f-4e32-82ad-750646aa760b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f142fc49d2759c4edd7cdb8701b300d435e67f54
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333828"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>Conteneurs de contrôles ActiveX : gestion d'événements à partir d'un contrôle ActiveX
Cet article explique l’utilisation de la fenêtre Propriétés pour installer des gestionnaires d’événements pour les contrôles ActiveX dans un conteneur de contrôles ActiveX. Les gestionnaires d’événements sont utilisés pour recevoir des notifications (à partir du contrôle) de certains événements et exécuter des actions en réponse. Cette notification est appelée « déclenche » l’événement.  
  
> [!NOTE]
>  Cet article utilise un basée sur la boîte de dialogue conteneur projet de contrôle ActiveX nommé conteneur et un contrôle incorporé (nommé Circ) comme exemples dans les procédures et le code.  
  
 Utilisez le bouton événements dans la fenêtre Propriétés, vous pouvez créer une table d’événements qui peuvent se produire dans votre application conteneur de contrôles ActiveX. Ce mappage, appelé « table d’événements récepteur,'' est créé et géré par Visual C++, lorsque vous ajoutez des gestionnaires d’événements à la classe de conteneur du contrôle. Chaque gestionnaire d’événements, implémenté avec une entrée de mappage d’événement est mappé à un événement spécifique à une fonction de membre du Gestionnaire d’événements de conteneur. Cette fonction de gestionnaire d’événements est appelée lorsque l’événement spécifié est déclenché par l’objet de contrôle ActiveX.  
  
 Pour plus d’informations sur les tables de récepteurs d’événements, consultez [tables de récepteurs d’événements](../mfc/reference/event-sink-maps.md) dans les *Class Library Reference*.  
  
##  <a name="_core_event_handler_modifications_to_the_project"></a> Modifications de gestionnaire d’événements au projet  
 Lorsque vous utilisez la fenêtre Propriétés pour ajouter des gestionnaires d’événements, une table de récepteur d’événements est déclarée et définie dans votre projet. Les instructions suivantes sont ajoutées au contrôle. Fichier CPP la première fois qu’un gestionnaire d’événements est ajouté. Ce code déclare une table de récepteur d’événements pour la classe de boîte de dialogue (dans ce cas, `CContainerDlg`) :  
  
 [!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]  
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]  
  
 Lorsque vous utilisez la fenêtre Propriétés pour ajouter des événements, un événement mapper entrée (`ON_EVENT`) est ajouté à la table de récepteur d’événement et un gestionnaire d’événements (fonction) est ajoutée à la mise en œuvre du conteneur (. (CPP) du contrôle.  
  
 L’exemple suivant déclare un gestionnaire d’événements, appelé `OnClickInCircCtrl`, pour le contrôle de Circ **ClickIn** événement :  
  
 [!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]  
  
 En outre, le modèle suivant est ajouté à la `CContainerDlg` implémentation de la classe (. Fichier CPP) pour la fonction membre gestionnaire d’événements :  
  
 [!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]  
  
 Pour plus d’informations sur les macros de récepteur d’événements, consultez [tables de récepteurs d’événements](../mfc/reference/event-sink-maps.md) dans les *Class Library Reference*.  
  
#### <a name="to-create-an-event-handler-function"></a>Pour créer une fonction de gestionnaire d’événements  
  
1.  À partir de l’affichage de classes, sélectionnez la classe de boîte de dialogue qui contient le contrôle ActiveX. Pour cet exemple, utilisez `CContainerDlg`.  
  
2.  Dans la fenêtre Propriétés, cliquez sur le **événements** bouton.  
  
3.  Dans la fenêtre Propriétés, sélectionnez l’ID de contrôle du contrôle ActiveX incorporé. Pour cet exemple, utilisez `IDC_CIRCCTRL1`.  
  
     La fenêtre Propriétés affiche une liste des événements qui peuvent être déclenchés par le contrôle ActiveX incorporé. N’importe quelle fonction membre indiquée en gras déjà dispose de fonctions de gestionnaire qui lui est affectées.  
  
4.  Sélectionnez l’événement que vous souhaitez que la classe de boîte de dialogue pour gérer. Dans cet exemple, sélectionnez **cliquez sur**.  
  
5.  Dans la zone de liste déroulante à droite, sélectionnez  **\<Ajouter > ClickCircctrl1**.  
  
6.  Double-cliquez sur la nouvelle fonction de gestionnaire à partir de l’affichage de classes pour atteindre le code de gestionnaire d’événements dans l’implémentation (. Fichier CPP) de `CContainerDlg`.  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)

