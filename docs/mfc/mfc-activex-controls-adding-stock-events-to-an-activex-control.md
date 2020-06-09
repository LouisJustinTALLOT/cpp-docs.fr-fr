---
title: "Contrôles ActiveX MFC : ajout d'événements stock à un contrôle ActiveX"
ms.date: 11/04/2016
f1_keywords:
- EVENT__STOCK_ERROR
- EVENT__STOCK_READYSTATECHANGE
- ReadyStateChange
- EVENT__STOCK_MOUSEMOVE
- EVENT__STOCK_MOUSEUP
- EVENT__STOCK_DBLCLICK
- KeyPress
- EVENT__STOCK_KEYDOWN
- EVENT__STOCK
- EVENT__STOCK_MOUSEDOWN
- EVENT__STOCK_KEYPRESS
- EVENT__STOCK_CLICK
- EVENT__STOCK_KEYUP
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- KeyPress event
- FireDblClick event
- FireMouseDown event
- events [MFC], stock
- FireKeyPress event
- EVENT_STOCK_MOUSEMOVE event
- EVENT_STOCK_CLICK event
- FireClick event
- FireKeyUp event
- FireMouseUp event
- EVENT_STOCK_ERROREVENT event
- EVENT_STOCK_KEYDOWN event
- EVENT_STOCK_MOUSEDOWN event
- EVENT_STOCK_KEYPRESS macro [MFC]
- EVENT_STOCK_KEYUP event
- EVENT_STOCK_DBLCLICK event
- FireError event
- FireKeyDown event
- ReadyStateChange event
- EVENT_STOCK_MOUSEUP event
- FireMouseMove event
- EVENT_STOCK prefix
- EVENT_STOCK_READYSTATECHANGE event
- EVENT_STOCK_KEYPRESS event
ms.assetid: 3eeadc67-4b3d-4444-8caa-53054073988a
ms.openlocfilehash: a97c08baaf3c11b0436e52bb4fd4ac380999d69a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615589"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>Contrôles ActiveX MFC : ajout d'événements stock à un contrôle ActiveX

Les événements stock diffèrent des événements personnalisés en ce qu’ils sont déclenchés automatiquement par la classe [COleControl](reference/colecontrol-class.md). `COleControl`contient des fonctions membres prédéfinies qui déclenchent des événements résultant d’actions courantes. Certaines actions courantes implémentées par `COleControl` incluent des clics simples et doubles sur le contrôle, des événements de clavier et des modifications de l’état des boutons de la souris. Les entrées de la table des événements pour les événements stock sont toujours précédées du préfixe EVENT_STOCK.

## <a name="stock-events-supported-by-the-add-event-wizard"></a><a name="_core_stock_events_supported_by_classwizard"></a>Événements stock pris en charge par l’Assistant Ajout d’événement

La `COleControl` classe fournit dix événements boursiers, listés dans le tableau suivant. Vous pouvez spécifier les événements que vous souhaitez dans votre contrôle à l’aide de l' [Assistant Ajout d’événement](../ide/add-event-wizard.md).

### <a name="stock-events"></a>Événements stock

|Événement|Déclenchement de la fonction|Commentaires|
|-----------|---------------------|--------------|
|Cliquez sur |**void FireClick ()**|Déclenché lorsque le contrôle capture la souris, tout message **BUTTONUP** (à gauche, au milieu ou à droite) est reçu et le bouton est relâché au-dessus du contrôle. Les événements action MouseDown et MouseUp se produisent avant cet événement.<br /><br /> Entrée de la table des événements : **EVENT_STOCK_CLICK ()**|
|Double|**void FireDblClick ()**|Semblable à Click, mais déclenché lors de la réception d’un message **BUTTONDBLCLK** .<br /><br /> Entrée de la table des événements : **EVENT_STOCK_DBLCLICK ()**|
|Error|**void FireError ((SCODE***SCODE* **, LPCSTR** `lpszDescription` **, uint** `nHelpID` **= 0)**        |Déclenché lorsqu’une erreur se produit dans votre contrôle ActiveX en dehors de la portée d’un appel de méthode ou d’un accès à une propriété.<br /><br /> Entrée de la table des événements : **EVENT_STOCK_ERROREVENT ()**|
|KeyDown|**void FireKeyDown (Short** `nChar` **, Short** `nShiftState` **)**      |Déclenché lors de la réception d’un `WM_SYSKEYDOWN` `WM_KEYDOWN` message ou.<br /><br /> Entrée de la table des événements : **EVENT_STOCK_KEYDOWN ()**|
|KeyPress|**void FireKeyPress (Short** <strong>\*</strong> `pnChar` **)**    |Déclenché lors de la réception d’un `WM_CHAR` message.<br /><br /> Entrée de la table des événements : **EVENT_STOCK_KEYPRESS ()**|
|KeyUp|**void FireKeyUp (Short** `nChar` **, Short** `nShiftState` **)**      |Déclenché lors de la réception d’un `WM_SYSKEYUP` `WM_KEYUP` message ou.<br /><br /> Entrée de la table des événements : **EVENT_STOCK_KEYUP ()**|
|MouseDown|**void FireMouseDown (Short** `nButton` **, Short** `nShiftState` **, float***x* **, float***y***)**          |Déclenché en cas de réception d’un **BUTTONDOWN** (gauche, du milieu ou de droite). La souris est capturée immédiatement avant le déclenchement de cet événement.<br /><br /> Entrée de la table des événements : **EVENT_STOCK_MOUSEDOWN ()**|
|MouseMove|**void FireMouseMove (Short** `nButton` **, Short** `nShiftState` **, float***x* **, float***y***)**          |Déclenché lors de la réception d’un message de WM_MOUSEMOVE.<br /><br /> Entrée de la table des événements : **EVENT_STOCK_MOUSEMOVE ()**|
|Lâché|**void FireMouseUp (Short** `nButton` **, Short** `nShiftState` **, float***x* **, float***y***)**          |Déclenché en cas de réception d’un **BUTTONUP** (gauche, du milieu ou de droite). La capture de la souris est libérée avant que cet événement soit déclenché.<br /><br /> Entrée de la table des événements : **EVENT_STOCK_MOUSEUP ()**|
|ReadyStateChange|**void FireReadyStateChange ()**|Déclenché lorsqu’un contrôle passe à l’état prêt suivant en raison de la quantité de données reçues.<br /><br /> Entrée de la table des événements : **EVENT_STOCK_READYSTATECHANGE ()**|

## <a name="adding-a-stock-event-using-the-add-event-wizard"></a><a name="_core_adding_a_stock_event_using_classwizard"></a>Ajout d’un événement stock à l’aide de l’Assistant Ajout d’événement

L’ajout d’événements stock requiert moins de travail que l’ajout d’événements personnalisés, car le déclenchement de l’événement réel est géré automatiquement par la classe de base, `COleControl` . La procédure suivante ajoute un événement stock à un contrôle qui a été développé à l’aide de l' [Assistant contrôle ActiveX MFC](reference/mfc-activex-control-wizard.md). L’événement, appelé KeyPress, se déclenche lorsqu’une touche est enfoncée et que le contrôle est actif. Cette procédure peut également être utilisée pour ajouter d’autres événements boursiers. Remplacez le nom de l’événement stock sélectionné par Appuyez sur.

#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>Pour ajouter l’événement stock KeyPress à l’aide de l’Assistant Ajout d’événement

1. Chargez votre projet de contrôle.

1. Dans Affichage de classes, cliquez avec le bouton droit sur votre classe de contrôle ActiveX pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **Ajouter** , puis sur **Ajouter un événement**.

   L’Assistant Ajout d’événement s’ouvre.

1. Dans la liste déroulante nom de l' **événement** , sélectionnez `KeyPress` .

1. Cliquez sur **Terminer**.

## <a name="add-event-wizard-changes-for-stock-events"></a><a name="_core_classwizard_changes_for_stock_events"></a>Modifications de l’Assistant Ajout d’événement pour les événements stock

Étant donné que les événements stock sont gérés par la classe de base du contrôle, l’Assistant Ajout d’événement ne modifie en aucune façon votre déclaration de classe. Il ajoute l’événement à la table d’événements du contrôle et crée une entrée dans son. Fichier IDL. La ligne suivante est ajoutée à la table des événements du contrôle, située dans l’implémentation de la classe du contrôle (. CPP) :

[!code-cpp[NVC_MFC_AxUI#5](codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]

L’ajout de ce code déclenche un événement KeyPress lorsqu’un WM_CHAR message est reçu et que le contrôle est actif. L’événement KeyPress peut être déclenché à d’autres moments en appelant sa fonction de déclenchement (par exemple, `FireKeyPress` ) à partir du code de contrôle.

L’Assistant Ajout d’événement ajoute la ligne de code suivante au du contrôle. Fichier IDL :

[!code-cpp[NVC_MFC_AxUI#6](codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]

Cette ligne associe l’événement KeyPress à son ID de dispatch standard et permet au conteneur d’anticiper l’événement KeyPress.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : méthodes](mfc-activex-controls-methods.md)<br/>
[COleControl, classe](reference/colecontrol-class.md)
