---
title: "Contrôles ActiveX MFC : ajout d'événements personnalisés"
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
ms.openlocfilehash: 8d464e5d7c9731e158e44d66d569fd1555401e17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364732"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>Contrôles ActiveX MFC : ajout d'événements personnalisés

Les événements personnalisés diffèrent des événements boursiers `COleControl`en ce qu’ils ne sont pas automatiquement tirés par classe . Un événement personnalisé reconnaît une certaine action, déterminée par le développeur de contrôle, comme un événement. Les entrées de carte d’événement pour les événements personnalisés sont représentées par la macro EVENT_CUSTOM. La section suivante met en œuvre un événement personnalisé pour un projet de contrôle ActiveX qui a été créé à l’aide de l’Assistant de Contrôle ActiveX.

## <a name="adding-a-custom-event-with-the-add-event-wizard"></a><a name="_core_adding_a_custom_event_with_classwizard"></a>Ajout d’un événement personnalisé avec l’Assistant De l’Événement Add

La procédure suivante ajoute un événement personnalisé spécifique, ClickIn. Vous pouvez utiliser cette procédure pour ajouter d’autres événements personnalisés. Remplacez votre nom d’événement personnalisé et ses paramètres par le nom et les paramètres de l’événement ClickIn.

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>Pour ajouter l’événement personnalisé ClickIn à l’aide de l’Assistant d’Événement Add

1. Chargez votre projet de contrôle.

1. Dans **Class View**, cliquez à droite sur votre classe de contrôle ActiveX pour ouvrir le menu raccourci.

1. À partir du menu raccourci, cliquez sur **Ajouter** et cliquez sur **Ajouter l’événement**.

   Cela ouvre le Assistant Événement Add.

1. Dans la boîte **de nom de l’événement,** sélectionnez d’abord n’importe quel événement existant, puis cliquez sur le bouton radio **personnalisé,** puis *tapez ClickIn*.

1. Dans la boîte **à noms interne,** tapez le nom de la fonction de mise à feu de l’événement. Pour cet exemple, utilisez la valeur par`FireClickIn`défaut fournie par l’Add Event Wizard ( ).

1. Ajoutez un paramètre, appelé *xCoord* (type *OLE_XPOS_PIXELS),* à l’aide des contrôles **de type Nom paramètre** et **Paramètre.**

1. Ajouter un deuxième paramètre, appelé *yCoord* (type *OLE_YPOS_PIXELS*).

1. Cliquez sur **Finition** pour créer l’événement.

## <a name="add-event-wizard-changes-for-custom-events"></a><a name="_core_classwizard_changes_for_custom_events"></a>Ajouter des changements d’assistant d’événement pour les événements personnalisés

Lorsque vous ajoutez un événement personnalisé, le Assistant d’Événement Add apporte des modifications à la classe de contrôle . H, . RPC, et . Fichiers IDL. Les échantillons de code suivants sont spécifiques à l’événement ClickIn.

Les lignes suivantes sont ajoutées à l’en-tête (. H) fichier de votre classe de contrôle:

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

Ce code déclare une fonction `FireClickIn` en ligne appelée qui appelle [COleControl::FireEvent](../mfc/reference/colecontrol-class.md#fireevent) avec l’événement ClickIn et les paramètres que vous avez définis à l’aide de l’Add Event Wizard.

En outre, la ligne suivante est ajoutée à la carte de l’événement pour le contrôle, situé dans la mise en œuvre (. Dossier du RPC de votre catégorie de contrôle :

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

Ce code cartographie l’événement ClickIn `FireClickIn`à la fonction en ligne , en passant les paramètres que vous avez définis à l’aide de l’Assistant d’Événement Add.

Enfin, la ligne suivante est ajoutée à votre contrôle . Fichier IDL:

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

Cette ligne attribue à l’événement ClickIn un numéro d’identification spécifique, tiré de la position de l’événement dans la liste des événements Add Event Wizard. L’inscription dans la liste des événements permet à un conteneur d’anticiper l’événement. Par exemple, il peut fournir le code de gestionnaire à exécuter lorsque l’événement est déclenché.

## <a name="calling-fireclickin"></a><a name="_core_calling_fireclickin"></a>Appel FireClickIn

Maintenant que vous avez ajouté l’événement personnalisé ClickIn à l’aide de l’Assistant d’Événement Add, vous devez décider quand cet événement doit être tiré. Pour ce faire, vous appelez `FireClickIn` lorsque l’action appropriée se produit. Pour cette discussion, le `InCircle` contrôle `WM_LBUTTONDOWN` utilise la fonction à l’intérieur d’un gestionnaire de message pour tirer l’événement ClickIn quand un utilisateur clique à l’intérieur d’une région circulaire ou elliptique. La procédure suivante `WM_LBUTTONDOWN` ajoute le gestionnaire.

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>Pour ajouter un gestionnaire de message avec le Assistant d’Événement Add

1. Chargez votre projet de contrôle.

1. Dans **Class View**, sélectionnez votre classe de contrôle ActiveX.

1. Dans la fenêtre **Propriétés,** vous voyez une liste de messages qui peuvent être traités par le contrôle ActiveX. Tout message présenté en gras a déjà une fonction de gestionnaire qui lui est assignée.

1. Sélectionnez le message que vous souhaitez gérer. Pour cet exemple, sélectionnez `WM_LBUTTONDOWN`.

1. De la case liste de drop-down sur la droite, sélectionnez ** \<Ajouter> OnLButtonDown**.

1. Double-cliquez sur la fonction de nouveau gestionnaire dans **Class View** pour sauter au code de gestionnaire de message dans l’implémentation (. CPP) fichier de votre contrôle ActiveX.

L’échantillon de `InCircle` code suivant appelle la fonction chaque fois que le bouton de la souris gauche est cliqué dans la fenêtre de contrôle. Cet échantillon peut être `WM_LBUTTONDOWN` trouvé `OnLButtonDown`dans la fonction de gestionnaire, , dans l’abstrait [de l’échantillon Circ.](../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
> Lorsque l’Assistant d’Événement Add crée des gestionnaires de messages pour les actions de bouton de souris, un appel au même gestionnaire de message de la classe de base est automatiquement ajouté. Ne supprimez pas cet appel. Si votre contrôle utilise l’un des messages de souris stock, les gestionnaires de messages dans la classe de base doivent être appelés pour s’assurer que la capture de la souris est traitée correctement.

Dans l’exemple suivant, l’événement ne s’déclenche que lorsque le clic se produit à l’intérieur d’une région circulaire ou elliptique dans le contrôle. Pour atteindre ce comportement, `InCircle` vous pouvez placer la fonction dans la mise en œuvre de votre contrôle (. Dossier du RPC :

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

Vous devrez également ajouter la déclaration `InCircle` suivante de la fonction à l’en-tête de votre contrôle (. H) fichier:

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

## <a name="custom-events-with-stock-names"></a><a name="_core_custom_events_with_stock_names"></a>Événements personnalisés avec des noms d’actions

Vous pouvez créer des événements personnalisés avec le même nom que les événements stock, mais vous ne pouvez pas implémenter les deux dans le même contrôle. Par exemple, vous pouvez créer un événement personnalisé appelé Click qui ne tire pas lorsque l’événement stock Cliquez serait normalement feu. Vous pouvez alors tirer l’événement Click à tout moment en appelant sa fonction de tir.

La procédure suivante ajoute un événement Clic personnalisé.

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>Pour ajouter un événement personnalisé qui utilise un nom d’événement stock

1. Chargez votre projet de contrôle.

1. Dans **Class View**, cliquez à droite sur votre classe de contrôle ActiveX pour ouvrir le menu raccourci.

1. À partir du menu raccourci, cliquez sur **Ajouter** et cliquez sur **Ajouter l’événement**.

   Cela ouvre le Assistant Événement Add.

1. Dans la liste d’abandon du **nom de l’événement,** sélectionnez un nom d’événement boursier. Pour cet exemple, sélectionnez **Cliquez**.

1. Pour **le type d’événement**, sélectionnez **Personnalisé**.

1. Cliquez sur **Finition** pour créer l’événement.

1. Appelez `FireClick` à des endroits appropriés dans votre code.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : méthodes](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl, classe](../mfc/reference/colecontrol-class.md)
