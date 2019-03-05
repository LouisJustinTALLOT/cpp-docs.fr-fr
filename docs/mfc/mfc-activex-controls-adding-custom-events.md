---
title: 'Contrôles ActiveX MFC : Ajout d’événements personnalisés'
ms.date: 11/04/2016
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
ms.openlocfilehash: 626aae04e0b19dc951814e4741cad3729acd3b72
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263011"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>Contrôles ActiveX MFC : Ajout d’événements personnalisés

Événements personnalisés diffèrent des événements stock car ils ne sont pas automatiquement déclenchés par la classe `COleControl`. Un événement personnalisé reconnaît une action particulière, déterminée par le développeur de contrôle, comme un événement. Les entrées de mappage d’événement pour les événements personnalisés sont représentées par la macro EVENT_CUSTOM. La section suivante implémente un événement personnalisé pour un projet de contrôle ActiveX qui a été créé à l’aide de l’Assistant contrôle ActiveX.

##  <a name="_core_adding_a_custom_event_with_classwizard"></a> Ajout d’un événement personnalisé avec l’Assistant Ajout d’événement

La procédure suivante ajoute un événement personnalisé spécifique, ClickIn. Vous pouvez utiliser cette procédure pour ajouter d’autres événements personnalisés. Remplacez par le nom de votre événement personnalisé et ses paramètres pour le nom de l’événement ClickIn et les paramètres.

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>Pour ajouter l’événement personnalisé ClickIn à l’aide de l’Assistant Ajout d’événement

1. Chargez votre projet de contrôle.

1. Dans l’affichage de classes, cliquez sur votre classe de contrôle ActiveX pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter un événement**.

   Cette opération ouvre l’Assistant Ajout d’événement.

1. Dans le **nom de l’événement** boîte, tout d’abord sélectionner n’importe quel événement existant, puis cliquez sur le **personnalisé** radio bouton, puis tapez *ClickIn*.

1. Dans le **nom interne** , tapez le nom de la fonction de déclenchement de l’événement. Pour cet exemple, utilisez la valeur par défaut fournie par l’Assistant Ajout d’événement (`FireClickIn`).

1. Ajoutez un paramètre appelé *xCoord* (type *OLE_XPOS_PIXELS*), en utilisant le **nom du paramètre** et **Type de paramètre** contrôles.

1. Ajoutez un deuxième paramètre, appelé *yCoord* (type *OLE_YPOS_PIXELS*).

1. Cliquez sur **Terminer** pour créer l’événement.

##  <a name="_core_classwizard_changes_for_custom_events"></a> Ajouter l’Assistant Modification des événements pour les événements personnalisés

Lorsque vous ajoutez un événement personnalisé, l’Assistant Ajout d’événement apporte des modifications à la classe de contrôle. H. CPP, et. Fichiers IDL. Exemples de code suivants sont spécifiques à l’événement ClickIn.

Les lignes suivantes sont ajoutées à l’en-tête (. H) fichier de votre classe de contrôle :

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

Ce code déclare une fonction inline appelée `FireClickIn` qui appelle [COleControl::FireEvent](../mfc/reference/colecontrol-class.md#fireevent) avec les paramètres et ClickIn (événement), vous avez défini à l’aide de l’Assistant Ajout d’événement.

En outre, la ligne suivante est ajoutée à la table d’événements pour le contrôle, situé dans l’implémentation (. Fichier CPP) de votre classe de contrôle :

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

Ce code est mappé à l’événement ClickIn à la fonction inline `FireClickIn`, en passant les paramètres que vous avez défini à l’aide de l’Assistant Ajout d’événement.

Enfin, la ligne suivante est ajoutée à de votre contrôle. Fichier IDL :

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

Cette ligne affecte à l’événement ClickIn un numéro d’identification spécifique, effectuée à partir de la position de l’événement dans la liste des événements Assistant Ajout d’événement. L’entrée dans la liste des événements permet à un conteneur d’anticiper l’événement. Par exemple, il peut fournir code du gestionnaire à exécuter lorsque l’événement est déclenché.

##  <a name="_core_calling_fireclickin"></a> Appel de FireClickIn

Maintenant que vous avez ajouté l’événement personnalisé ClickIn à l’aide de l’Assistant Ajout d’un événement, vous devez décider quand cet événement doit être déclenché. Pour cela, vous devez appeler `FireClickIn` lorsque se produit l’action appropriée. Pour cette discussion, le contrôle utilise le `InCircle` fonction à l’intérieur d’un gestionnaire de messages WM_LBUTTONDOWN pour déclencher l’événement ClickIn lorsqu’un utilisateur clique à l’intérieur d’une zone circulaire ou elliptique. La procédure suivante ajoute le gestionnaire WM_LBUTTONDOWN.

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>Pour ajouter un gestionnaire de messages avec l’Assistant Ajout d’événement

1. Chargez votre projet de contrôle.

1. Dans l’affichage de classes, sélectionnez votre classe de contrôle ActiveX.

1. Dans la fenêtre Propriétés, cliquez sur le **Messages** bouton.

   La fenêtre Propriétés affiche une liste de messages qui peuvent être gérés par le contrôle ActiveX. Tout message indiqué en gras déjà possède une fonction de gestionnaire qui lui est assignée.

1. Dans la fenêtre Propriétés, sélectionnez le message que vous souhaitez gérer. Pour cet exemple, sélectionnez WM_LBUTTONDOWN.

1. Dans la zone de liste déroulante à droite, sélectionnez  **\<Ajouter > OnLButtonDown**.

1. Double-cliquez sur la nouvelle fonction de gestionnaire dans Affichage de classes pour accéder au code de gestionnaire de messages dans l’implémentation (. Fichier CPP) de votre contrôle ActiveX.

Le code suivant exemple appelle la `InCircle` chaque clic sur le bouton gauche de la souris dans la fenêtre de contrôle de la fonction. Cet exemple peut être trouvé dans la fonction gestionnaire WM_LBUTTONDOWN, `OnLButtonDown`, dans le [CERC exemple](../visual-cpp-samples.md) abstraite.

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
>  Lorsque l’Assistant Ajout d’événement crée des gestionnaires de messages pour les actions de bouton de la souris, un appel vers le même gestionnaire de message de la classe de base est automatiquement ajouté. Ne supprimez pas cet appel. Si votre contrôle utilise un des messages de souris stock, les gestionnaires de messages dans la classe de base doivent être appelées pour vous assurer que la capture de souris est gérée correctement.

Dans l’exemple suivant, l’événement est déclenché uniquement quand le clic se produit à l’intérieur d’une zone circulaire ou elliptique dans le contrôle. Pour obtenir ce comportement, vous pouvez placer le `InCircle` fonction dans votre fichier d’implémentation (. Fichier CPP) :

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

Vous devrez également ajouter la déclaration suivante de la `InCircle` fonction permettant d’en-tête (. H) fichier :

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

##  <a name="_core_custom_events_with_stock_names"></a> Événements personnalisés avec des noms de valeurs

Vous pouvez créer des événements personnalisés avec le même nom que les événements stock, mais vous ne pouvez pas implémenter les deux dans le même contrôle. Par exemple, vous souhaiterez peut-être créer un événement personnalisé appelé Click qui ne se déclenche pas lorsque l’événement stock Click se déclenche normalement. Vous pouvez alors déclencher l’événement Click à tout moment en appelant sa fonction de déclenchement.

La procédure suivante ajoute un personnalisé, cliquez sur événement.

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>Pour ajouter un événement personnalisé qui utilise un nom d’événement stock

1. Chargez votre projet de contrôle.

1. Dans l’affichage de classes, cliquez sur votre classe de contrôle ActiveX pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter un événement**.

   Cette opération ouvre l’Assistant Ajout d’événement.

1. Dans le **nom de l’événement** liste déroulante, sélectionnez un nom d’événement stock. Pour cet exemple, sélectionnez **cliquez sur**.

1. Pour **Type d’événement**, sélectionnez **personnalisé**.

1. Cliquez sur **Terminer** pour créer l’événement.

1. Appelez `FireClick` emplacements appropriés dans votre code.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : Méthodes](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl, classe](../mfc/reference/colecontrol-class.md)
