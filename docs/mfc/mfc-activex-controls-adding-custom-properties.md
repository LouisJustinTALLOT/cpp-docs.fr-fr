---
title: 'Contrôles ActiveX MFC : Ajout de propriétés personnalisées'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: e02d5523b894f89aa93c8d2765a128920afa2353
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392776"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>Contrôles ActiveX MFC : Ajout de propriétés personnalisées

Propriétés personnalisées diffèrent des propriétés stocks, propriétés personnalisées ne sont pas déjà implémentées par le `COleControl` classe. Une propriété personnalisée est utilisée pour exposer un département ou une apparence d’un contrôle ActiveX à un programmeur en utilisant le contrôle.

Cet article décrit comment ajouter une propriété personnalisée au contrôle ActiveX à l’aide de l’Assistant Ajout de propriété et explique les modifications de code qui en résulte. Les rubriques traitées ici sont les suivantes :

- [À l’aide de l’Assistant Ajout de propriété pour ajouter une propriété personnalisée](#_core_using_classwizard_to_add_a_custom_property)

- [Ajoutez les modifications de propriété Assistant pour les propriétés personnalisées](#_core_classwizard_changes_for_custom_properties)

Propriétés personnalisées sont fournis en quatre variantes d’implémentation : Variable de membre, la Variable membre avec Notification, méthodes Get/Set et paramétrable.

- Implémentation des variables membres

   Cette implémentation représente l’état de la propriété sous la forme d’une variable de membre dans la classe du contrôle. Utiliser l’implémentation d’une Variable membre lorsqu’il n’est pas important de savoir quand la valeur de propriété change. Les trois types, cette implémentation crée le moins de code de prise en charge pour la propriété. Pour l’implémentation des variables membres, la macro d’entrée de la table de dispatch est [DISP_PROPERTY](../mfc/reference/dispatch-maps.md#disp_property).

- Variable de membre avec l’implémentation de Notification

   Cette implémentation se compose d’une variable de membre et une fonction de notification créée par l’Assistant Ajout de propriété. La fonction de notification est automatiquement appelée par l’infrastructure après la modification de valeur de propriété. Utilise la Variable membre avec l’implémentation de Notification lorsque vous avez besoin d’être averti une fois une valeur de propriété a changé. Cette implémentation nécessite plus de temps, car elle nécessite un appel de fonction. Pour cette implémentation, la macro d’entrée de la table de dispatch est [DISP_PROPERTY_NOTIFY](../mfc/reference/dispatch-maps.md#disp_property_notify).

- Obtient ou définit l’implémentation de méthodes

   Cette implémentation se compose d’une paire de fonctions membres de la classe du contrôle. L’implémentation des méthodes Get/Set appelle automatiquement l’obtention de membre (fonction) lorsque l’utilisateur du contrôle demande la valeur actuelle de la propriété et la fonction membre quand l’utilisateur du contrôle demande que de modifier la propriété. Utilisez cette implémentation lorsque vous avez besoin pour calculer la valeur d’une propriété pendant l’exécution, valider une valeur passée par l’utilisateur du contrôle avant de modifier la propriété réelle, ou implémenter un type de propriété en lecture ou écriture-seule. Pour cette implémentation, la macro d’entrée de la table de dispatch est [DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex). La section suivante, [à l’aide de l’Assistant Ajout de propriété pour ajouter une propriété personnalisée](#_core_using_classwizard_to_add_a_custom_property), utilise la propriété personnalisée CircleOffset pour illustrer cette implémentation.

- Implémentation paramétrée

   Implémentation paramétrée est prise en charge par l’Assistant Ajout de propriété. Une propriété paramétrée (parfois appelée un tableau de propriétés) peut être utilisée pour accéder à un ensemble de valeurs via une propriété unique de votre contrôle. Pour cette implémentation, la macro d’entrée de la table de dispatch est DISP_PROPERTY_PARAM. Pour plus d’informations sur l’implémentation de ce type, consultez [implémentation d’une propriété paramétrée](../mfc/mfc-activex-controls-advanced-topics.md) dans l’article contrôles ActiveX : Rubriques avancées.

##  <a name="_core_using_classwizard_to_add_a_custom_property"></a> À l’aide de l’Assistant Ajout de propriété pour ajouter une propriété personnalisée

La procédure suivante illustre l’ajout d’une propriété personnalisée, CircleOffset, qui utilise l’implémentation des méthodes Get/Set. La propriété personnalisée CircleOffset permet à l’utilisateur du contrôle décaler le cercle à partir du centre du rectangle englobant du contrôle. La procédure d’ajout de propriétés personnalisées avec une implémentation autre que les méthodes Get/Set est très similaire.

Cette procédure peut également servir à ajouter d’autres propriétés personnalisées que vous souhaitez. Indiquez le nom de votre propriété personnalisée pour le nom de la propriété CircleOffset et les paramètres.

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>Pour ajouter la propriété personnalisée CircleOffset à l’aide de l’Assistant Ajout de propriété

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter une propriété**.

   Cette opération ouvre le [Assistant Ajout de propriété](../ide/names-add-property-wizard.md).

1. Dans le **nom de la propriété** , tapez *CircleOffset*.

1. Pour **Type d’implémentation**, cliquez sur **Méthodes Get/Set**.

1. Dans le **Type de propriété** boîte, sélectionnez **court**.

1. Tapez un nom unique pour vos fonctions Get et Set, ou acceptez les noms par défaut.

9. Cliquez sur **Terminer**.

##  <a name="_core_classwizard_changes_for_custom_properties"></a> Ajoutez des modifications d’Assistant de propriété pour les propriétés personnalisées

Lorsque vous ajoutez la propriété personnalisée CircleOffset, l’Assistant Ajout de propriété apporte des modifications à l’en-tête (. (H) et l’implémentation (. (CPP) de la classe du contrôle.

Les lignes suivantes sont ajoutées à la. Fichier de H pour déclarer deux fonctions appelées `GetCircleOffset` et `SetCircleOffset`:

[!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

La ligne suivante est ajoutée à de votre contrôle. Fichier IDL :

[!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

Cette ligne assigne la propriété CircleOffset un numéro d’identification spécifique, effectuée à partir de la position dans la liste des méthodes et propriétés de l’Assistant Ajout de propriété.

En outre, la ligne suivante est ajoutée à la table de dispatch (dans le. Cpp de la classe control) pour mapper la propriété CircleOffset aux deux fonctions de gestionnaire du contrôle :

[!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

Enfin, les implémentations de la `GetCircleOffset` et `SetCircleOffset` fonctions sont ajoutées à la fin du contrôle. Fichier CPP. Dans la plupart des cas, vous allez modifier la fonction Get pour retourner la valeur de la propriété. La fonction Set contient généralement le code qui doit être exécuté avant ou après les modifications de propriété.

[!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

Notez que l’Assistant Ajout de propriété ajoute automatiquement un appel, à [SetModifiedFlag](../mfc/reference/colecontrol-class.md#setmodifiedflag), le corps de la fonction Set. Appel de cette fonction de marque le contrôle comme modifié. Si un contrôle a été modifié, son nouvel état est enregistré lorsque le conteneur est enregistré. Cette fonction doit être appelée chaque fois qu’une propriété, enregistrée en tant que partie de l’état du contrôle persistant, change de valeur.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : Propriétés](../mfc/mfc-activex-controls-properties.md)<br/>
[Contrôles ActiveX MFC : Méthodes](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl, classe](../mfc/reference/colecontrol-class.md)
