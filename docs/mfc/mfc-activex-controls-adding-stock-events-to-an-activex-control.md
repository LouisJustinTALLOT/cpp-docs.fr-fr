---
title: 'Contrôles ActiveX MFC : Ajout d’événements Stock à un contrôle ActiveX | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41445015f30eb953675f763652fb85ef3eeb857a
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930785"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>Contrôles ActiveX MFC : ajout d'événements stock à un contrôle ActiveX
Événements stock diffèrent des événements personnalisés dans la mesure où ils sont déclenchés automatiquement par la classe [COleControl](../mfc/reference/colecontrol-class.md). `COleControl` contient des fonctions membres prédéfinies qui déclenchent des événements résultant d’actions communes. Certaines actions courantes implémentées par `COleControl` inclure unique - et double - clicks sur le contrôle, les événements de clavier et les modifications dans l’état des boutons de souris. Événement mapper les entrées de stock sont toujours précédés par le préfixe EVENT_STOCK.  
  
##  <a name="_core_stock_events_supported_by_classwizard"></a> Stocker les événements pris en charge par l’Assistant Ajout d’événement  
 La `COleControl` classe fournit dix événements stock, répertoriés dans le tableau suivant. Vous pouvez spécifier les événements que vous souhaitez dans votre contrôle à l’aide de la [Assistant Ajout d’événement](../ide/add-event-wizard.md).  
  
### <a name="stock-events"></a>Événements stock  
  
|Événement|Fonction de déclenchement|Commentaires|  
|-----------|---------------------|--------------|  
|Clic|**void FireClick ()**|Déclenché lorsque le contrôle capture la souris, tout **BUTTONUP** (gauche, du milieu ou de droit) de message est reçu et le bouton est relâché sur le contrôle. Le stock MouseDown et MouseUp événements se produisent avant cet événement.<br /><br /> Entrée de mappage d’événement : **EVENT_STOCK_CLICK)**|  
|Double clic|**void FireDblClick ()**|Similaire à Click mais déclenché quand un **BUTTONDBLCLK** message est reçu.<br /><br /> Entrée de mappage d’événement : **EVENT_STOCK_DBLCLICK)**|  
|Error|**void FireError (SCODE***scode* **, LPCSTR** `lpszDescription` **, UINT**`nHelpID`**= 0)** |Déclenché lorsqu’une erreur se produit au sein de votre contrôle ActiveX en dehors de l’étendue d’un accès d’appel ou de la propriété de méthode.<br /><br /> Entrée de mappage d’événement : **EVENT_STOCK_ERROREVENT)**|  
|KeyDown|**void FireKeyDown (court** `nChar` **, short**`nShiftState`**)** |Déclenché quand un `WM_SYSKEYDOWN` ou `WM_KEYDOWN` message est reçu.<br /><br /> Entrée de mappage d’événement : **EVENT_STOCK_KEYDOWN)**|  
|KeyPress|**void FireKeyPress (court\***`pnChar`**)** |Déclenché quand un `WM_CHAR` message est reçu.<br /><br /> Entrée de mappage d’événement : **EVENT_STOCK_KEYPRESS)**|  
|KeyUp|**void FireKeyUp (court** `nChar` **, short**`nShiftState`**)** |Déclenché quand un `WM_SYSKEYUP` ou `WM_KEYUP` message est reçu.<br /><br /> Entrée de mappage d’événement : **EVENT_STOCK_KEYUP)**|  
|MouseDown|**void FireMouseDown (court** `nButton` **, short** `nShiftState` **, float***x* **, float** *y***)** |Déclenché si n’importe quel **BUTTONDOWN** (gauche, centre ou droite) est reçu. La souris est capturée immédiatement avant cet événement est déclenché.<br /><br /> Entrée de mappage d’événement : **EVENT_STOCK_MOUSEDOWN)**|  
|MouseMove|**void FireMouseMove (court** `nButton` **, short** `nShiftState` **, float***x* **, float** *y***)** |Déclenché lors de la réception d’un message WM_MOUSEMOVE.<br /><br /> Entrée de mappage d’événement : **EVENT_STOCK_MOUSEMOVE)**|  
|MouseUp|**void FireMouseUp (court** `nButton` **, short** `nShiftState` **, float***x* **, float** *y***)** |Déclenché si n’importe quel **BUTTONUP** (gauche, centre ou droite) est reçu. La capture de la souris est relâchée avant que cet événement est déclenché.<br /><br /> Entrée de mappage d’événement : **EVENT_STOCK_MOUSEUP)**|  
|ReadyStateChange|**void FireReadyStateChange ()**|Déclenché lorsqu’un contrôle passe à l’état prêt suivant en raison de la quantité de données reçues.<br /><br /> Entrée de mappage d’événement : **EVENT_STOCK_READYSTATECHANGE)**|  
  
##  <a name="_core_adding_a_stock_event_using_classwizard"></a> Ajout d’un événement Stock à l’aide de l’Assistant Ajout d’événement  
 Ajout d’événements stock nécessite moins de travail que l’ajout d’événements personnalisés, car le déclenchement de l’événement réel est géré automatiquement par la classe de base `COleControl`. La procédure suivante ajoute un événement stock à un contrôle qui a été développé à l’aide de [Assistant contrôle ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md). L’événement, appelé KeyPress, se déclenche lorsqu’une touche est enfoncée et que le contrôle est actif. Cette procédure peut également être utilisée pour ajouter d’autres événements stocks. Remplacez le nom de l’événement stock sélectionné pour KeyPress.  
  
#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>Pour ajouter l’événement stock KeyPress à l’aide de l’Assistant Ajout d’événement  
  
1.  Chargez votre projet de contrôle.  
  
2.  Dans Affichage de classes, cliquez sur la classe du contrôle ActiveX pour ouvrir le menu contextuel.  
  
3.  Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter un événement**.  
  
     L’Assistant Ajout d’événement s’ouvre.  
  
4.  Dans le **nom de l’événement** la liste déroulante, sélectionnez `KeyPress`.  
  
5.  Cliquez sur **Terminer**.  
  
##  <a name="_core_classwizard_changes_for_stock_events"></a> Ajouter l’Assistant Modification des événements pour les événements Stock  
 Événements stock sont gérés par la classe de base du contrôle, l’Assistant Ajout d’événement ne change pas votre déclaration de classe en aucune façon. Il ajoute l’événement à la table d’événements du contrôle et crée une entrée dans son. Fichier IDL. La ligne suivante est ajoutée à la table d’événements du contrôle, située dans le fichier d’implémentation (. Fichier de RPC) :  
  
 [!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]  
  
 Ajout de ce code déclenche un événement KeyPress lors de la réception d’un message WM_CHAR et le contrôle est actif. L’événement KeyPress peut être déclenché à d’autres moments en appelant sa fonction de déclenchement (par exemple, `FireKeyPress`) à partir du code de contrôle.  
  
 L’Assistant Ajout d’événement ajoute la ligne suivante de code du contrôle. Fichier IDL :  
  
 [!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]  
  
 Cette ligne associe l’événement KeyPress avec son ID de dispatch et permet au conteneur d’anticiper l’événement KeyPress.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Contrôles ActiveX MFC : méthodes](../mfc/mfc-activex-controls-methods.md)   
 [COleControl, classe](../mfc/reference/colecontrol-class.md)
