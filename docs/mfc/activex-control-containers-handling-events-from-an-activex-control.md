---
title: "Conteneurs de contrôles ActiveX : gestion d'événements à partir d'un contrôle ActiveX"
ms.date: 09/12/2018
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
ms.openlocfilehash: 5deff0a50de813cc5faa43a86e591d3003a3c03e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659626"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>Conteneurs de contrôles ActiveX : gestion d'événements à partir d'un contrôle ActiveX

Cet article décrit l’utilisation de la fenêtre Propriétés pour installer des gestionnaires d’événements pour les contrôles ActiveX dans un conteneur de contrôles ActiveX. Les gestionnaires d’événements sont utilisés pour recevoir des notifications (à partir du contrôle) de certains événements et effectuer une action en réponse. Cette notification est appelée « déclenche » l’événement.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

> [!NOTE]
>  Cet article utilise un boîte de dialogue ActiveX conteneur projet de contrôle nommé conteneur et un contrôle incorporé nommé CERC comme exemples dans les procédures et le code.

Utilisez le bouton événements dans la fenêtre Propriétés, vous pouvez créer une table d’événements qui peuvent se produire dans votre application de conteneur de contrôle ActiveX. Ce mappage, appelé « table d’événements récepteur,'' est créé et géré par Visual C++ lorsque vous ajoutez des gestionnaires d’événements à la classe de conteneur du contrôle. Chaque gestionnaire d’événements, implémentée avec une entrée de mappage d’événement, mappe un événement spécifique à une fonction de membre du Gestionnaire d’événements de conteneur. Cette fonction de gestionnaire d’événements est appelée lorsque l’événement spécifié est déclenché par l’objet de contrôle ActiveX.

Pour plus d’informations sur les tables de récepteurs d’événements, consultez [tables de récepteurs d’événements](../mfc/reference/event-sink-maps.md) dans le *Class Library Reference*.

##  <a name="_core_event_handler_modifications_to_the_project"></a> Modifications de gestionnaire d’événements au projet

Lorsque vous utilisez la fenêtre Propriétés pour ajouter des gestionnaires d’événements, une table de récepteur d’événements est déclarée et définie dans votre projet. Les instructions suivantes sont ajoutées au contrôle. Fichier CPP la première fois qu’un gestionnaire d’événements est ajouté. Ce code déclare une table de récepteur d’événements pour la classe de boîte de dialogue (dans ce cas, `CContainerDlg`) :

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

Lorsque vous utilisez la fenêtre Propriétés pour ajouter des événements, un événement mapper entrée (`ON_EVENT`) est ajouté à la table de récepteur d’événements et un gestionnaire d’événements (fonction) est ajoutée à la mise en œuvre du conteneur (. Fichier CPP).

L’exemple suivant déclare un gestionnaire d’événements, appelé `OnClickInCircCtrl`, pour le contrôle CERC `ClickIn` événement :

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

En outre, le modèle suivant est ajouté à la `CContainerDlg` implémentation de la classe (. Fichier CPP) pour la fonction membre gestionnaire d’événements :

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

Pour plus d’informations sur les macros de récepteur d’événements, consultez [tables de récepteurs d’événements](../mfc/reference/event-sink-maps.md) dans le *Class Library Reference*.

#### <a name="to-create-an-event-handler-function"></a>Pour créer une fonction de gestionnaire d’événements

1. À partir de l’affichage de classes, sélectionnez la classe de boîte de dialogue qui contient le contrôle ActiveX. Pour cet exemple, utilisez `CContainerDlg`.

1. Dans la fenêtre Propriétés, cliquez sur le **événements** bouton.

1. Dans la fenêtre Propriétés, sélectionnez l’ID de contrôle du contrôle ActiveX incorporé. Pour cet exemple, utilisez `IDC_CIRCCTRL1`.

   La fenêtre Propriétés affiche une liste des événements qui peuvent être déclenchés par le contrôle ActiveX incorporé. N’importe quelle fonction membre indiquée en gras déjà dispose de fonctions de gestionnaire qui lui est assignées.

1. Sélectionnez l’événement que vous souhaitez que la classe de boîte de dialogue à gérer. Pour cet exemple, sélectionnez **cliquez sur**.

1. Dans la zone de liste déroulante à droite, sélectionnez  **\<Ajouter > ClickCircctrl1**.

1. Double-cliquez sur la nouvelle fonction de gestionnaire à partir de l’affichage de classes pour accéder au code de gestionnaire d’événements dans l’implémentation (. Fichier CPP) de `CContainerDlg`.

## <a name="see-also"></a>Voir aussi

[Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)

