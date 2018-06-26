---
title: 'Contrôles ActiveX MFC : Ajout d’événements personnalisés | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], events [MFC]
- EVENT_CUSTOM prefix [MFC]
- custom events [MFC], adding to ActiveX controls
- EVENT_CUSTOM macro [MFC]
- InCircle method [MFC]
- ClickIn event
- FireClickIn event
- COleControl class [MFC], custom events [MFC]
- Click event, custom events [MFC]
- events [MFC], ActiveX controls
- custom events [MFC]
- FireEvent method, adding custom events
ms.assetid: c584d053-1e34-47aa-958e-37d3e9b85892
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2e6e5eeab0be13eb64052eb9e90a570dcc5124d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929050"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>Contrôles ActiveX MFC : ajout d'événements personnalisés
Événements personnalisés diffèrent des événements stock, dans la mesure où ils ne sont pas déclenchés automatiquement par la classe `COleControl`. Un événement personnalisé reconnaît une action particulière, déterminée par le développeur du contrôle, comme un événement. Les entrées de mappage des événements pour les événements personnalisés sont représentées par la macro EVENT_CUSTOM. La section suivante implémente un événement personnalisé pour un projet de contrôle ActiveX qui a été créé à l’aide de l’Assistant contrôle ActiveX.  
  
##  <a name="_core_adding_a_custom_event_with_classwizard"></a> Ajout d’un événement personnalisé avec l’Assistant Ajout d’événement  
 La procédure suivante ajoute un événement personnalisé spécifique, ClickIn. Vous pouvez utiliser cette procédure pour ajouter d’autres événements personnalisés. Remplacez par le nom de votre événement personnalisé et ses paramètres pour le nom de l’événement ClickIn et les paramètres.  
  
#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>Pour ajouter l’événement personnalisé ClickIn à l’aide de l’Assistant Ajout d’événement  
  
1.  Chargez votre projet de contrôle.  
  
2.  Dans Affichage de classes, cliquez sur la classe du contrôle ActiveX pour ouvrir le menu contextuel.  
  
3.  Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter un événement**.  
  
     L’Assistant Ajout d’événement s’ouvre.  
  
4.  Dans le **nom de l’événement** zone, tout d’abord sélectionner n’importe quel événement existant, puis cliquez sur le **personnalisé** radio bouton, puis tapez *ClickIn*.  
  
5.  Dans le **nom interne** , tapez le nom de la fonction de déclenchement de l’événement. Pour cet exemple, utilisez la valeur par défaut fournie par l’Assistant Ajout d’événement (`FireClickIn`).  
  
6.  Ajoutez un paramètre appelé *xCoord* (type *OLE_XPOS_PIXELS*), à l’aide du **nom de paramètre** et **Type de paramètre** contrôles.  
  
7.  Ajoutez un deuxième paramètre, appelé *yCoord* (type *OLE_YPOS_PIXELS*).  
  
8.  Cliquez sur **Terminer** pour créer l’événement.  
  
##  <a name="_core_classwizard_changes_for_custom_events"></a> Ajouter l’Assistant Modification des événements pour les événements personnalisés  
 Lorsque vous ajoutez un événement personnalisé, l’Assistant Ajout d’événement apporte des modifications à la classe du contrôle. H. RPC, et. Fichiers IDL. Les exemples de code suivants sont spécifiques à l’événement ClickIn.  
  
 Les lignes suivantes sont ajoutées à l’en-tête (. H) fichier de votre classe de contrôle :  
  
 [!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]  
  
 Ce code déclare une fonction inline appelée `FireClickIn` qui appelle [COleControl::FireEvent](../mfc/reference/colecontrol-class.md#fireevent) avec les paramètres et ClickIn (événement), vous avez défini à l’aide de l’Assistant Ajout d’événement.  
  
 En outre, la ligne suivante est ajoutée à la table d’événements pour le contrôle, situé dans l’implémentation (. Fichier CPP) de votre classe de contrôle :  
  
 [!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]  
  
 Ce code est mappé à l’événement ClickIn à la fonction inline `FireClickIn`, en passant les paramètres que vous avez défini à l’aide de l’Assistant Ajout d’événement.  
  
 Enfin, la ligne suivante est ajoutée à votre contrôle de code. Fichier IDL :  
  
 [!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]  
  
 Cette ligne assigne à l’événement ClickIn un numéro d’identification spécifique, obtenue à partir de la position de l’événement dans la liste des événements Assistant Ajout d’événement. L’entrée dans la liste des événements permet à un conteneur d’anticiper l’événement. Par exemple, il peut fournir de code de gestionnaire à exécuter lorsque l’événement est déclenché.  
  
##  <a name="_core_calling_fireclickin"></a> Appel de FireClickIn  
 Maintenant que vous avez ajouté l’événement personnalisé ClickIn à l’aide de l’Assistant Ajout d’événement, vous devez décider quand cet événement doit être déclenché. Pour cela, vous devez appeler `FireClickIn` lorsque se produit l’action appropriée. Dans le cadre de cette présentation, le contrôle utilise le `InCircle` fonction à l’intérieur d’un gestionnaire de messages WM_LBUTTONDOWN pour déclencher l’événement ClickIn lorsqu’un utilisateur clique à l’intérieur d’une zone circulaire ou elliptique. La procédure suivante ajoute le gestionnaire WM_LBUTTONDOWN.  
  
#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>Pour ajouter un gestionnaire de messages avec l’Assistant Ajout d’événement  
  
1.  Chargez votre projet de contrôle.  
  
2.  Dans l’affichage de classes, sélectionnez votre classe du contrôle ActiveX.  
  
3.  Dans la fenêtre Propriétés, cliquez sur le **Messages** bouton.  
  
     La fenêtre Propriétés affiche une liste de messages qui peuvent être gérés par le contrôle ActiveX. Tout message apparaissant en gras est déjà possède une fonction de gestionnaire qui lui est affectée.  
  
4.  Dans la fenêtre Propriétés, sélectionnez le message que vous souhaitez gérer. Dans cet exemple, sélectionnez WM_LBUTTONDOWN.  
  
5.  Dans la zone de liste déroulante à droite, sélectionnez  **\<Ajouter > OnLButtonDown**.  
  
6.  Double-cliquez sur la nouvelle fonction de gestionnaire dans Affichage de classes pour atteindre le code du Gestionnaire de messages dans l’implémentation (. Fichier CPP) de votre contrôle ActiveX.  
  
 Le code suivant appelle de l’exemple le `InCircle` chaque clic sur le bouton gauche de la souris dans la fenêtre de contrôle de fonction. Cet exemple peut être trouvé dans la fonction gestionnaire WM_LBUTTONDOWN, `OnLButtonDown`, dans le [exemple Circ](../visual-cpp-samples.md) abstraite.  
  
 [!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]  
  
> [!NOTE]
>  Lorsque l’Assistant Ajout d’événement crée des gestionnaires de messages pour les actions de bouton de la souris, un appel au même gestionnaire de messages de la classe de base est automatiquement ajouté. Ne supprimez pas cet appel. Si votre contrôle utilise un des messages d’action de la souris, les gestionnaires de messages dans la classe de base doivent être appelées pour vous assurer que la capture de souris est gérée correctement.  
  
 Dans l’exemple suivant, l’événement est déclenché uniquement quand le clic se produit à l’intérieur d’une zone circulaire ou elliptique dans le contrôle. Pour obtenir ce comportement, vous pouvez placer le `InCircle` fonction dans votre fichier d’implémentation (. Fichier de RPC) :  
  
 [!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]  
  
 Vous devrez également ajouter la déclaration suivante de la `InCircle` fonction d’en-tête (. H) fichier :  
  
 [!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]  
  
##  <a name="_core_custom_events_with_stock_names"></a> Événements personnalisés avec des noms de valeurs  
 Vous pouvez créer des événements personnalisés avec le même nom que des événements stock, toutefois, vous ne pouvez pas implémenter à la fois dans le même contrôle. Par exemple, vous souhaiterez créer un événement personnalisé appelé Click qui ne se déclenche pas lorsque l’événement stock Click se déclenche normalement. Vous pouvez alors déclencher l’événement Click à tout moment en appelant la fonction de son déclenchement.  
  
 La procédure suivante ajoute un personnalisé, cliquez sur événement.  
  
#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>Pour ajouter un événement personnalisé qui utilise un nom d’événement stock  
  
1.  Chargez votre projet de contrôle.  
  
2.  Dans Affichage de classes, cliquez sur la classe du contrôle ActiveX pour ouvrir le menu contextuel.  
  
3.  Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter un événement**.  
  
     L’Assistant Ajout d’événement s’ouvre.  
  
4.  Dans le **nom de l’événement** liste déroulante, sélectionnez un nom d’événement stock. Dans cet exemple, sélectionnez **cliquez sur**.  
  
5.  Pour **Type d’événement**, sélectionnez **personnalisé**.  
  
6.  Cliquez sur **Terminer** pour créer l’événement.  
  
7.  Appelez `FireClick` emplacements appropriés dans votre code.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Contrôles ActiveX MFC : méthodes](../mfc/mfc-activex-controls-methods.md)   
 [COleControl, classe](../mfc/reference/colecontrol-class.md)
