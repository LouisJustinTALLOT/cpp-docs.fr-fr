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
ms.openlocfilehash: 79cd4fc572e55c67cc5a2cfe3a00e04f2a4a7850
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364688"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>Contrôles ActiveX MFC : ajout d'événements stock à un contrôle ActiveX

Les événements boursiers diffèrent des événements personnalisés en ce qu’ils sont automatiquement tirés par la classe [COleControl](../mfc/reference/colecontrol-class.md). `COleControl`contient des fonctions prédéfinises des membres que les événements d’incendie résultant d’actions communes. Certaines actions courantes `COleControl` mises en œuvre en incluant des clics simples et doubles sur le contrôle, les événements clavier, et les changements dans l’état des boutons de la souris. Les entrées de carte d’événement pour les événements de stock sont toujours précédées par le préfixe EVENT_STOCK.

## <a name="stock-events-supported-by-the-add-event-wizard"></a><a name="_core_stock_events_supported_by_classwizard"></a>Événements boursiers soutenus par l’Assistant d’Événement Add

La `COleControl` classe fournit dix événements boursiers, répertoriés dans le tableau suivant. Vous pouvez spécifier les événements que vous souhaitez sous votre contrôle à l’aide de [l’Assistant d’Événement Add](../ide/add-event-wizard.md).

### <a name="stock-events"></a>Événements boursiers

|Événement|Fonction de tir|Commentaires|
|-----------|---------------------|--------------|
|Cliquez sur |**void FireClick( )**|Tiré lorsque le contrôle capture la souris, tout message **BUTTONUP** (gauche, milieu ou droite) est reçu, et le bouton est libéré sur le contrôle. Les événements MouseDown et MouseUp se produisent avant cet événement.<br /><br /> Entrée de la carte de l’événement: **EVENT_STOCK_CLICK)**|
|DblClick DblClick|**vide FireDblClick( )**|Semblable à Click, mais tiré quand un message **BUTTONDBLCLK** est reçu.<br /><br /> Entrée de la carte de l’événement: **EVENT_STOCK_DBLCLICK)**|
|Error|**void FireError ( SCODE SCODE***scode* **, LPCSTR** `lpszDescription` **, UINT**`nHelpID`**0 )**        |Tiré lorsqu’une erreur se produit dans votre contrôle ActiveX en dehors de la portée d’un appel de méthode ou d’un accès à la propriété.<br /><br /> Entrée de la carte de l’événement: **EVENT_STOCK_ERROREVENT)**|
|KeyDown|**void FireKeyDown ( court** `nChar` **, court**`nShiftState`**)**      |Tiré lorsqu’un ou `WM_SYSKEYDOWN` `WM_KEYDOWN` un message est reçu.<br /><br /> Entrée de la carte de l’événement: **EVENT_STOCK_KEYDOWN)**|
|Keypress|**void FireKeyPress ( court** <strong>\*</strong> `pnChar` **)**    |Tiré lorsqu’un `WM_CHAR` message est reçu.<br /><br /> Entrée de la carte de l’événement: **EVENT_STOCK_KEYPRESS)**|
|KeyUp|**void FireKeyUp ( court** `nChar` **, court**`nShiftState`**)**      |Tiré lorsqu’un ou `WM_SYSKEYUP` `WM_KEYUP` un message est reçu.<br /><br /> Entrée de la carte de l’événement: **EVENT_STOCK_KEYUP)**|
|Mousedown|**void FireMouseDown ( court** `nButton` **, court** `nShiftState` **, flotteur***x* **, flottez***y***)**          |Tiré si n’importe quel **BUTTONDOWN** (gauche, milieu ou droite) est reçu. La souris est capturée immédiatement avant que cet événement ne soit tiré.<br /><br /> Entrée de la carte de l’événement: **EVENT_STOCK_MOUSEDOWN)**|
|Mousemove|**vide FireMouseMove ( court** `nButton` **, court** `nShiftState` **, flotteur***x* **, flottez***y***)**          |Tiré lorsqu’un message WM_MOUSEMOVE est reçu.<br /><br /> Entrée de la carte de l’événement: **EVENT_STOCK_MOUSEMOVE)**|
|Mouseup|**void FireMouseUp ( court** `nButton` **, court** `nShiftState` **, flotteur***x* **, flottez***y***)**          |Tiré si n’importe quel **BUTTONUP** (à gauche, au milieu ou à droite) est reçu. La capture de la souris est libérée avant que cet événement ne soit déclenché.<br /><br /> Entrée de la carte de l’événement: **EVENT_STOCK_MOUSEUP)**|
|ReadyStateChange (en)|**void FireReadyStateChange( )**|Tiré quand un contrôle passe à l’état suivant prêt en raison de la quantité de données reçues.<br /><br /> Entrée de la carte de l’événement: **EVENT_STOCK_READYSTATECHANGE)**|

## <a name="adding-a-stock-event-using-the-add-event-wizard"></a><a name="_core_adding_a_stock_event_using_classwizard"></a>Ajout d’un événement stock à l’aide de l’assistant d’événement Ajouter

L’ajout d’événements d’actions nécessite moins de travail que d’ajouter des `COleControl`événements personnalisés parce que le tir de l’événement réel est géré automatiquement par la classe de base, . La procédure suivante ajoute un événement de stock à un contrôle qui a été développé en utilisant [MFC ActiveX Control Wizard](../mfc/reference/mfc-activex-control-wizard.md). L’événement, appelé KeyPress, s’allume lorsqu’une clé est pressée et que le contrôle est actif. Cette procédure peut également être utilisée pour ajouter d’autres événements boursiers. Remplacez le nom d’événement d’actions sélectionné par KeyPress.

#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>Pour ajouter l’événement stock KeyPress à l’aide de l’Add Event Wizard

1. Chargez votre projet de contrôle.

1. Dans Class View, cliquez à droite sur votre classe de contrôle ActiveX pour ouvrir le menu raccourci.

1. À partir du menu raccourci, cliquez sur **Ajouter** et cliquez sur **Ajouter l’événement**.

   Cela ouvre le Assistant Événement Add.

1. Dans la liste d’abandon `KeyPress`du nom de l’événement, sélectionnez . **Event Name**

1. Cliquez sur **Terminer**.

## <a name="add-event-wizard-changes-for-stock-events"></a><a name="_core_classwizard_changes_for_stock_events"></a>Ajouter des changements d’assistant d’événement pour les événements boursiers

Étant donné que les événements boursiers sont gérés par la classe de base du contrôle, l’Assistant d’Événement Add ne change en aucune façon votre déclaration de classe. Il ajoute l’événement à la carte de l’événement du contrôle et fait une entrée dans son . Fichier IDL. La ligne suivante est ajoutée à la carte d’événements du contrôle, située dans la mise en œuvre de la classe de contrôle (. Dossier du RPC :

[!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]

L’ajout de ce code déclenche un événement KeyPress lorsqu’un message WM_CHAR est reçu et que le contrôle est actif. L’événement KeyPress peut être tiré à d’autres `FireKeyPress`moments en appelant sa fonction de tir (par exemple, ) à partir du code de contrôle.

Le Assistant d’Événement Add ajoute la ligne de code suivante à la commande . Fichier IDL:

[!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]

Cette ligne associe l’événement KeyPress à son ID de répartition standard et permet au conteneur d’anticiper l’événement KeyPress.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : méthodes](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl, classe](../mfc/reference/colecontrol-class.md)
