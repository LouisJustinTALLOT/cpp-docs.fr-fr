---
title: 'Conteneurs de contrôles ActiveX : Gestion des événements à partir d’un contrôle ActiveX'
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
ms.openlocfilehash: 7487792fbc9fe6775640f40755a7f725543fb9f3
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907773"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>Conteneurs de contrôles ActiveX : Gestion des événements à partir d’un contrôle ActiveX

Cet article décrit l’utilisation de la fenêtre **Propriétés** (dans **affichage de classes**) pour installer des gestionnaires d’événements pour les contrôles ActiveX dans un conteneur de contrôles ActiveX. Les gestionnaires d’événements sont utilisés pour recevoir des notifications (du contrôle) de certains événements et effectuer une action en réponse. Cette notification est appelée « déclenchement » de l’événement.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

> [!NOTE]
>  Cet article utilise un projet de conteneur de contrôles ActiveX basé sur des boîtes de dialogue nommé conteneur et un contrôle incorporé nommé CIRC comme exemples dans les procédures et le code.

À l’aide du bouton événements de la fenêtre **Propriétés** (dans **affichage de classes**), vous pouvez créer un mappage d’événements qui peuvent se produire dans votre application conteneur de contrôles ActiveX. Ce mappage, appelé « mappage de récepteur d’événements », est créé et géré par le C++ visuel quand vous ajoutez des gestionnaires d’événements à la classe de conteneur de contrôle. Chaque gestionnaire d’événements, implémenté avec une entrée de la table des événements, mappe un événement spécifique à une fonction membre du gestionnaire d’événements de conteneur. Cette fonction de gestionnaire d’événements est appelée lorsque l’événement spécifié est déclenché par l’objet de contrôle ActiveX.

Pour plus d’informations sur les tables de récepteurs d’événements, consultez [tables de récepteurs d’événements](../mfc/reference/event-sink-maps.md) dans la référence de la bibliothèque de *classes*.

##  <a name="_core_event_handler_modifications_to_the_project"></a>Modifications du gestionnaire d’événements dans le projet

Lorsque vous utilisez la fenêtre **Propriétés** pour ajouter des gestionnaires d’événements, un mappage de récepteur d’événements est déclaré et défini dans votre projet. Les instructions suivantes sont ajoutées au contrôle. Fichier CPP la première fois qu’un gestionnaire d’événements est ajouté. Ce code déclare une table de récepteurs d’événements pour la classe de boîte de dialogue (dans `CContainerDlg`ce cas,) :

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

Quand vous utilisez la fenêtre **Propriétés** pour ajouter des événements, une entrée de la`ON_EVENT`table des événements () est ajoutée au mappage du récepteur d’événements et une fonction de gestionnaire d’événements est ajoutée à l’implémentation du conteneur (. CPP).

L’exemple suivant déclare un gestionnaire d’événements, appelé `OnClickInCircCtrl`, pour l’événement du `ClickIn` contrôle CIRC :

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

En outre, le modèle suivant est ajouté à l' `CContainerDlg` implémentation de classe (. CPP) pour la fonction membre du gestionnaire d’événements :

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

Pour plus d’informations sur les macros du récepteur d’événements, consultez [tables de récepteurs d’événements](../mfc/reference/event-sink-maps.md) dans la référence de la bibliothèque de *classes*.

#### <a name="to-create-an-event-handler-function"></a>Pour créer une fonction de gestionnaire d’événements

1. Dans Affichage de classes, sélectionnez la classe de boîte de dialogue qui contient le contrôle ActiveX. Pour cet exemple, utilisez `CContainerDlg`.

1. Dans la fenêtre **Propriétés** , cliquez sur le bouton **Événements** .

1. Dans la fenêtre **Propriétés** , sélectionnez l’ID de contrôle du contrôle ActiveX incorporé. Pour cet exemple, utilisez `IDC_CIRCCTRL1`.

   La fenêtre **Propriétés** affiche une liste d’événements qui peuvent être déclenchés par le contrôle ActiveX incorporé. Toute fonction membre affichée en gras est déjà assignée à des fonctions de gestionnaire.

1. Sélectionnez l’événement que vous souhaitez que la classe de dialogue gère. Pour cet exemple, sélectionnez **Click**.

1. Dans la liste déroulante située à droite, sélectionnez  **\<Ajouter > ClickCircctrl1**.

1. Double-cliquez sur la nouvelle fonction de gestionnaire de Affichage de classes pour accéder au code du gestionnaire d’événements dans l’implémentation (. CPP) de `CContainerDlg`.

## <a name="see-also"></a>Voir aussi

[Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)
