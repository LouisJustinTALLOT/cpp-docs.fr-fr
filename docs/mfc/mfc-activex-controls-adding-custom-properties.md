---
title: 'Contrôles ActiveX MFC : ajout de propriétés personnalisées'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: 00f7a879582bca562ce626fe224206094fd19bc7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364702"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>Contrôles ActiveX MFC : ajout de propriétés personnalisées

Les propriétés personnalisées diffèrent des propriétés de `COleControl` stock en ce que les propriétés personnalisées ne sont pas déjà mises en œuvre par la classe. Une propriété personnalisée est utilisée pour exposer un certain état ou l’apparence d’un contrôle ActiveX à un programmeur utilisant le contrôle.

Cet article décrit comment ajouter une propriété personnalisée au contrôle ActiveX à l’aide de l’Assistant De propriété Add et explique les modifications de code qui en résultent. Les sujets abordés sont les suivants :

- [Utilisation de l’Assistant De propriété Add pour ajouter une propriété personnalisée](#_core_using_classwizard_to_add_a_custom_property)

- [Ajouter des modifications de l’assistant de propriété pour les propriétés personnalisées](#_core_classwizard_changes_for_custom_properties)

Les propriétés personnalisées se présentent en quatre variétés de mise en œuvre : Variable membre, Variable membre avec Notification, Méthodes d’obtenir/ensemble et Paramétrisation.

- Mise en œuvre variable des membres

   Cette mise en œuvre représente l’état du bien en tant que variable membre dans la classe de contrôle. Utilisez la mise en œuvre variable du membre lorsqu’il n’est pas important de savoir quand la valeur de la propriété change. Sur les trois types, cette implémentation crée le moins de code de support pour la propriété. La macro d’entrée de carte de répartition pour la mise en œuvre variable de membre est [DISP_PROPERTY](../mfc/reference/dispatch-maps.md#disp_property).

- Variable des membres avec mise en œuvre de notification

   Cette implémentation se compose d’une variable membre et d’une fonction de notification créée par l’Assistant De Propriété Add. La fonction de notification est automatiquement appelée par le cadre après les changements de valeur de la propriété. Utilisez la variable membre avec la mise en œuvre de notification lorsque vous devez être informé après qu’une valeur de propriété a changé. Cette implémentation demande plus de temps car elle nécessite un appel de fonction. La carte d’expédition macro d’entrée pour cette mise en œuvre est [DISP_PROPERTY_NOTIFY](../mfc/reference/dispatch-maps.md#disp_property_notify).

- Mise en œuvre de méthodes d’obtenir/ensemble

   Cette implémentation se compose d’une paire de fonctions de membre dans la classe de contrôle. La mise en œuvre de Get/Set Methods appelle automatiquement la fonction membre Get lorsque l’utilisateur du contrôle demande la valeur actuelle de la propriété et la fonction membre Set lorsque l’utilisateur du contrôle demande que la propriété soit modifiée. Utilisez cette implémentation lorsque vous devez calculer la valeur d’une propriété pendant le temps d’exécution, valider une valeur passée par l’utilisateur du contrôle avant de modifier la propriété réelle, ou implémenter un type de propriété lu ou écrit uniquement. La carte d’expédition macro d’entrée pour cette mise en œuvre est [DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex). La section suivante, [En utilisant l’assistant de propriété Add pour ajouter une propriété personnalisée](#_core_using_classwizard_to_add_a_custom_property), utilise la propriété personnalisée CircleOffset pour démontrer cette mise en œuvre.

- Mise en œuvre paramétrée

   La mise en œuvre paramétrée est prise en charge par l’Assistant De Propriété Add. Une propriété paramétrée (parfois appelée un tableau de propriété) peut être utilisée pour accéder à un ensemble de valeurs par le biais d’une seule propriété de votre contrôle. La macro d’entrée de carte de répartition pour cette mise en œuvre est DISP_PROPERTY_PARAM. Pour plus d’informations sur la mise en œuvre de ce type, voir [La mise en œuvre d’une propriété paramétisée](../mfc/mfc-activex-controls-advanced-topics.md) dans l’article ActiveX Controls: Advanced Topics.

## <a name="using-the-add-property-wizard-to-add-a-custom-property"></a><a name="_core_using_classwizard_to_add_a_custom_property"></a>Utilisation de l’assistant de propriété Add pour ajouter une propriété personnalisée

La procédure suivante démontre l’ajout d’une propriété personnalisée, CircleOffset, qui utilise la mise en œuvre Get/Set Methods. La propriété personnalisée CircleOffset permet à l’utilisateur du contrôle de compenser le cercle depuis le centre du rectangle de délimitation du contrôle. La procédure d’ajout de propriétés personnalisées avec une implémentation autre que Get/ Set Methods est très similaire.

Cette même procédure peut également être utilisée pour ajouter d’autres propriétés personnalisées que vous voulez. Remplacez votre nom de propriété personnalisé par le nom et les paramètres de propriété CircleOffset.

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>Pour ajouter la propriété personnalisée CircleOffset à l’aide de l’Add Property Wizard

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. À partir du menu raccourci, cliquez sur **Ajouter** et cliquez ensuite **ajouter la propriété**.

   Cela ouvre le [Add Property Wizard](../ide/names-add-property-wizard.md).

1. Dans la boîte **nom de propriété,** tapez *CircleOffset*.

1. Pour **Type d’implémentation**, cliquez sur **Méthodes Get/Set**.

1. Dans la boîte **de type de propriété,** sélectionnez **court**.

1. Tapez des noms uniques pour vos fonctions Get and Set, ou acceptez les noms par défaut.

1. Cliquez sur **Terminer**.

## <a name="add-property-wizard-changes-for-custom-properties"></a><a name="_core_classwizard_changes_for_custom_properties"></a>Ajouter des modifications de sorcier de propriété pour les propriétés personnalisées

Lorsque vous ajoutez la propriété personnalisée CircleOffset, l’Add Property Wizard apporte des modifications à l’en-tête (. H) et la mise en œuvre (. CPP) dossiers de la classe de contrôle.

Les lignes suivantes sont ajoutées à la . Fichier H pour déclarer `GetCircleOffset` deux `SetCircleOffset`fonctions appelées et :

[!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

La ligne suivante est ajoutée à votre contrôle . Fichier IDL:

[!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

Cette ligne attribue à la propriété CircleOffset un numéro d’identification spécifique, tiré de la position de la méthode dans la liste des méthodes et des propriétés de l’Assistant De propriété Add.

En outre, la ligne suivante est ajoutée à la carte d’expédition (dans le . Fichier du RPC de la classe de contrôle) pour cartographier la propriété CircleOffset aux deux fonctions de gestionnaire du contrôle :

[!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

Enfin, les implémentations et `GetCircleOffset` `SetCircleOffset` les fonctions sont ajoutées à la fin de la commande . Dossier du RPC. Dans la plupart des cas, vous modifierez la fonction Get pour retourner la valeur de la propriété. La fonction Set contiendra habituellement du code qui doit être exécuté avant ou après les modifications de la propriété.

[!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

Notez que l’Assistant De Propriété Add ajoute automatiquement un appel, à [SetModifiedFlag](../mfc/reference/colecontrol-class.md#setmodifiedflag), à l’organisme de la fonction Set. L’appel de cette fonction marque le contrôle tel qu’il est modifié. Si un contrôle a été modifié, son nouvel état sera enregistré lorsque le conteneur sera enregistré. Cette fonction doit être appelée chaque fois qu’une propriété, sauvée dans le cadre de l’état persistant du contrôle, change de valeur.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : propriétés](../mfc/mfc-activex-controls-properties.md)<br/>
[Contrôles ActiveX MFC : méthodes](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl, classe](../mfc/reference/colecontrol-class.md)
