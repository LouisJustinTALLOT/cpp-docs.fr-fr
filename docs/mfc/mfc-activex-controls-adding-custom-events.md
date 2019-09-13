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
ms.openlocfilehash: d22eb6016635c509d6b8bb2068f00125d0227ca2
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907308"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>Contrôles ActiveX MFC : Ajout d’événements personnalisés

Les événements personnalisés diffèrent des événements stock en ce qu’ils ne sont pas `COleControl`déclenchés automatiquement par la classe. Un événement personnalisé reconnaît une certaine action, déterminée par le développeur de contrôle, en tant qu’événement. Les entrées de la table des événements pour les événements personnalisés sont représentées par la macro EVENT_CUSTOM. La section suivante implémente un événement personnalisé pour un projet de contrôle ActiveX qui a été créé à l’aide de l’Assistant contrôle ActiveX.

##  <a name="_core_adding_a_custom_event_with_classwizard"></a>Ajout d’un événement personnalisé à l’aide de l’Assistant Ajout d’événement

La procédure suivante ajoute un événement personnalisé spécifique, cliquez sur. Vous pouvez utiliser cette procédure pour ajouter d’autres événements personnalisés. Remplacez le nom et les paramètres de l’événement Click par le nom et les paramètres de l’événement Click.

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>Pour ajouter l’événement personnalisé clicko à l’aide de l’Assistant Ajout d’événement

1. Chargez votre projet de contrôle.

1. Dans **affichage de classes**, cliquez avec le bouton droit sur votre classe de contrôle ActiveX pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **Ajouter** , puis sur **Ajouter un événement**.

   L’Assistant Ajout d’événement s’ouvre.

1. Dans la zone nom de l' **événement** , sélectionnez tout d’abord un événement existant, cliquez sur la case d’option **personnalisée** , puis tapez *Click*.

1. Dans la zone **nom interne** , tapez le nom de la fonction de déclenchement de l’événement. Pour cet exemple, utilisez la valeur par défaut fournie par l’Assistant Ajout d'`FireClickIn`événement ().

1. Ajoutez un paramètre, appelé *xCoord* (type *OLE_XPOS_PIXELS*), à l’aide du **nom de paramètre** et des contrôles de **type de paramètre** .

1. Ajoutez un deuxième paramètre, appelé *yCoord* (tapez *OLE_YPOS_PIXELS*).

1. Cliquez sur **Terminer** pour créer l’événement.

##  <a name="_core_classwizard_changes_for_custom_events"></a>Modifications de l’Assistant Ajout d’événement pour les événements personnalisés

Lorsque vous ajoutez un événement personnalisé, l’Assistant Ajout d’événement apporte des modifications à la classe de contrôle. H,. CPP, et. Fichiers IDL. Les exemples de code suivants sont spécifiques à l’événement Click.

Les lignes suivantes sont ajoutées à l’en-tête (. H) de votre classe de contrôle :

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

Ce code déclare une fonction inline appelée `FireClickIn` qui appelle [COleControl :: FireEvent](../mfc/reference/colecontrol-class.md#fireevent) avec l’événement Click et les paramètres que vous avez définis à l’aide de l’Assistant Ajout d’événement.

En outre, la ligne suivante est ajoutée à la table des événements pour le contrôle, situé dans l’implémentation (. CPP) de votre classe de contrôle :

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

Ce code mappe l’événement Click à la fonction `FireClickIn`Inline, en passant les paramètres que vous avez définis à l’aide de l’Assistant Ajout d’événement.

Enfin, la ligne suivante est ajoutée au de votre contrôle. Fichier IDL :

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

Cette ligne affecte un numéro d’ID spécifique à l’événement Click, issu de la position de l’événement dans la liste des événements de l’Assistant Ajout d’événement. L’entrée dans la liste des événements permet à un conteneur d’anticiper l’événement. Par exemple, il peut fournir le code de gestionnaire à exécuter lorsque l’événement est déclenché.

##  <a name="_core_calling_fireclickin"></a>Appel de FireClickIn

Maintenant que vous avez ajouté l’événement personnalisé clicko à l’aide de l’Assistant Ajout d’événement, vous devez décider quand cet événement doit être déclenché. Pour ce faire, appelez `FireClickIn` quand l’action appropriée se produit. Dans le cadre de cette discussion, le `InCircle` contrôle utilise la `WM_LBUTTONDOWN` fonction à l’intérieur d’un gestionnaire de messages pour déclencher l’événement Click lorsqu’un utilisateur clique dans une zone circulaire ou elliptique. La procédure suivante ajoute le `WM_LBUTTONDOWN` gestionnaire.

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>Pour ajouter un gestionnaire de messages à l’aide de l’Assistant Ajout d’événement

1. Chargez votre projet de contrôle.

1. Dans **affichage de classes**, sélectionnez votre classe de contrôle ActiveX.

1. Dans la fenêtre **Propriétés** , vous voyez une liste des messages qui peuvent être gérés par le contrôle ActiveX. Tout message affiché en gras a déjà une fonction de gestionnaire qui lui est assignée.

1. Sélectionnez le message que vous souhaitez gérer. Pour cet exemple, sélectionnez `WM_LBUTTONDOWN`.

1. Dans la liste déroulante située à droite, sélectionnez  **\<Ajouter > OnLButtonDown**.

1. Double-cliquez sur la nouvelle fonction de gestionnaire dans **affichage de classes** pour accéder au code du gestionnaire de messages dans l’implémentation (. CPP) de votre contrôle ActiveX.

L’exemple de code suivant appelle `InCircle` la fonction chaque fois que l’utilisateur clique sur le bouton gauche de la souris dans la fenêtre de contrôle. Cet exemple se trouve dans la `WM_LBUTTONDOWN` fonction gestionnaire, `OnLButtonDown`, dans l’exemple abstrait [CIRC](../overview/visual-cpp-samples.md) .

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
>  Lorsque l’Assistant Ajout d’événement crée des gestionnaires de messages pour les actions de bouton de la souris, un appel au même gestionnaire de messages de la classe de base est ajouté automatiquement. Ne supprimez pas cet appel. Si votre contrôle utilise l’un des messages de la souris, les gestionnaires de messages de la classe de base doivent être appelés pour s’assurer que la capture de la souris est correctement gérée.

Dans l’exemple suivant, l’événement se déclenche uniquement lorsque le clic se produit à l’intérieur d’une zone circulaire ou elliptique dans le contrôle. Pour obtenir ce comportement, vous pouvez placer la `InCircle` fonction dans l’implémentation de votre contrôle (. CPP) :

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

Vous devrez également ajouter la déclaration suivante de la `InCircle` fonction à l’en-tête de votre contrôle (. H) :

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

##  <a name="_core_custom_events_with_stock_names"></a>Événements personnalisés avec des noms de stock

Vous pouvez créer des événements personnalisés portant le même nom que les événements stock, mais vous ne pouvez pas implémenter les deux dans le même contrôle. Par exemple, vous souhaiterez peut-être créer un événement personnalisé appelé Click qui ne se déclenche pas lorsque l’événement stock Click devrait normalement se déclencher. Vous pouvez ensuite déclencher l’événement Click à tout moment en appelant sa fonction de déclenchement.

La procédure suivante ajoute un événement Click personnalisé.

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>Pour ajouter un événement personnalisé qui utilise un nom d’événement stock

1. Chargez votre projet de contrôle.

1. Dans **affichage de classes**, cliquez avec le bouton droit sur votre classe de contrôle ActiveX pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **Ajouter** , puis sur **Ajouter un événement**.

   L’Assistant Ajout d’événement s’ouvre.

1. Dans la liste déroulante nom de l' **événement** , sélectionnez un nom d’événement stock. Pour cet exemple, sélectionnez **Click**.

1. Pour **type d’événement**, sélectionnez **personnalisé**.

1. Cliquez sur **Terminer** pour créer l’événement.

1. Appelez `FireClick` aux emplacements appropriés dans votre code.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : Méthodes](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl, classe](../mfc/reference/colecontrol-class.md)
