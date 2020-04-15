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
ms.openlocfilehash: ae623ee0973e78db3b542646dd6bdec58cc2dfc8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367950"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>Conteneurs de contrôles ActiveX : gestion d'événements à partir d'un contrôle ActiveX

Cet article traite de l’utilisation de la fenêtre **Properties** (dans **Class View**) pour installer des gestionnaires d’événements pour les commandes ActiveX dans un conteneur de contrôle ActiveX. Les gestionnaires d’événements sont utilisés pour recevoir des notifications (du contrôle) de certains événements et effectuer une certaine action en réponse. Cette notification est appelée "tir" de l’événement.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne devrait pas être utilisée pour de nouveaux développements. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, voir [ActiveX Controls](activex-controls.md).

> [!NOTE]
> Cet article utilise un projet de conteneurs de contrôle ActiveX basé sur le dialogue nommé Container et un contrôle intégré nommé Circ comme exemples dans les procédures et le code.

En utilisant le bouton Events dans la fenêtre **Propriétés** (dans **Class View**), vous pouvez créer une carte des événements qui peuvent se produire dans votre application de conteneur de contrôle ActiveX. Cette carte, appelée « carte d’évier d’événements », est créée et entretenue par Visual CMD lorsque vous ajoutez des gestionnaires d’événements à la classe de conteneurs de contrôle. Chaque gestionnaire d’événements, mis en œuvre avec une entrée de carte d’événement, cartographie un événement spécifique à une fonction de membre de gestionnaire d’événements de conteneur. Cette fonction de gestionnaire d’événements est appelée lorsque l’événement spécifié est déclenché par l’objet de commande ActiveX.

Pour plus d’informations sur les cartes de puits [d’événements,](../mfc/reference/event-sink-maps.md) voir Event Sink Maps dans la *référence de la bibliothèque de classe*.

## <a name="event-handler-modifications-to-the-project"></a><a name="_core_event_handler_modifications_to_the_project"></a>Modifications du gestionnaire d’événements au projet

Lorsque vous utilisez la fenêtre **Propriétés** pour ajouter des gestionnaires d’événements, une carte d’évier d’événement est déclarée et définie dans votre projet. Les déclarations suivantes sont ajoutées au contrôle . Le PPC dépose le dossier de la première fois qu’un gestionnaire d’événements est ajouté. Ce code déclare une carte d’évier d’événement pour `CContainerDlg`la classe de boîte de dialogue (dans ce cas, ):

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

Lorsque vous utilisez la fenêtre **Propriétés** pour`ON_EVENT`ajouter des événements, une entrée de carte d’événement () est ajoutée à la carte de l’évier de l’événement et une fonction de gestionnaire d’événements est ajoutée à la mise en œuvre du conteneur (. dossier du RPC.

L’exemple suivant déclare un `OnClickInCircCtrl`gestionnaire d’événements, appelé `ClickIn` , pour l’événement de contrôle du Circ:

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

En outre, le modèle suivant `CContainerDlg` est ajouté à la mise en œuvre de la classe (. Dossier du RPC pour la fonction de membre du gestionnaire d’événements :

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

Pour plus d’informations sur les macros d’évier [d’événements,](../mfc/reference/event-sink-maps.md) voir Event Sink Maps dans la *référence de bibliothèque de classe*.

#### <a name="to-create-an-event-handler-function"></a>Créer une fonction de gestionnaire d’événements

1. De Class View, sélectionnez la classe de dialogue qui contient le contrôle ActiveX. Pour cet exemple, utiliser `CContainerDlg`.

1. Dans la fenêtre **Propriétés** , cliquez sur le bouton **Événements** .

1. Dans la fenêtre **Propriétés,** sélectionnez l’ID de contrôle du contrôle ActiveX intégré. Pour cet exemple, utiliser `IDC_CIRCCTRL1`.

   La fenêtre **Propriété** affiche une liste d’événements qui peuvent être tirés par le contrôle ActiveX intégré. Toute fonction de membre montrée en gras a déjà des fonctions de gestionnaire qui lui sont assignées.

1. Sélectionnez l’événement que vous voulez que la classe de dialogue à gérer. Pour cet exemple, sélectionnez **Cliquez**.

1. De la case liste d’abandon sur la droite, sélectionnez ** \<Ajouter> ClickCircctrl1**.

1. Double-cliquez sur la nouvelle fonction de gestionnaire de Class View pour sauter au code de gestionnaire d’événement dans l’implémentation (. RPC) fichier `CContainerDlg`de .

## <a name="see-also"></a>Voir aussi

[Conteneurs de contrôle ActiveX](../mfc/activex-control-containers.md)
