---
description: 'En savoir plus sur : contrôles ActiveX MFC : ajout de propriétés personnalisées'
title: 'Contrôles ActiveX MFC : ajout de propriétés personnalisées'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: efae1c7cedc2202a2a40974393be881466442b84
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202936"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>Contrôles ActiveX MFC : ajout de propriétés personnalisées

Les propriétés personnalisées diffèrent des propriétés stock dans le fait que les propriétés personnalisées ne sont pas encore implémentées par la `COleControl` classe. Une propriété personnalisée est utilisée pour exposer un certain État ou l’apparence d’un contrôle ActiveX à un programmeur à l’aide du contrôle.

Cet article explique comment ajouter une propriété personnalisée au contrôle ActiveX à l’aide de l’Assistant Ajout de propriété et explique les modifications de code qui en résultent. Les sujets abordés sont les suivants :

- [Utilisation de l’Assistant Ajout de propriété pour ajouter une propriété personnalisée](#_core_using_classwizard_to_add_a_custom_property)

- [Modifications de l’Assistant Ajout de propriété pour les propriétés personnalisées](#_core_classwizard_changes_for_custom_properties)

Les propriétés personnalisées sont disponibles dans quatre types d’implémentation : variable membre, variable membre avec notification, méthodes obten/Set et paramétrables.

- Implémentation de variable membre

   Cette implémentation représente l’état de la propriété en tant que variable membre dans la classe de contrôle. Utilisez l’implémentation de variable membre lorsqu’il n’est pas important de savoir quand la valeur de propriété change. Parmi les trois types, cette implémentation crée le moins de code de prise en charge pour la propriété. La macro d’entrée de la table de dispatch pour l’implémentation de la variable membre est [DISP_PROPERTY](reference/dispatch-maps.md#disp_property).

- Variable membre avec implémentation de notification

   Cette implémentation se compose d’une variable membre et d’une fonction de notification créée par l’Assistant Ajout de propriété. La fonction de notification est appelée automatiquement par le Framework après que la valeur de la propriété a été modifiée. Utilisez la variable membre avec l’implémentation de notification lorsque vous devez être notifié après la modification d’une valeur de propriété. Cette implémentation nécessite plus de temps, car elle nécessite un appel de fonction. La macro d’entrée de la table de dispatch pour cette implémentation est [DISP_PROPERTY_NOTIFY](reference/dispatch-maps.md#disp_property_notify).

- Implémentation des méthodes de récupération/définition

   Cette implémentation se compose d’une paire de fonctions membres dans la classe de contrôle. L’implémentation des méthodes obtient/Set appelle automatiquement la fonction membre d’extraction lorsque l’utilisateur du contrôle demande la valeur actuelle de la propriété et la fonction membre Set lorsque l’utilisateur du contrôle demande que la propriété soit modifiée. Utilisez cette implémentation lorsque vous avez besoin de calculer la valeur d’une propriété au moment de l’exécution, de valider une valeur passée par l’utilisateur du contrôle avant de modifier la propriété réelle ou d’implémenter un type de propriété en lecture seule ou en écriture seule. La macro d’entrée de la table de dispatch pour cette implémentation est [DISP_PROPERTY_EX](reference/dispatch-maps.md#disp_property_ex). La section suivante, à [l’aide de l’Assistant Ajout d’une propriété, pour ajouter une propriété personnalisée](#_core_using_classwizard_to_add_a_custom_property), utilise la propriété personnalisée CircleOffset pour illustrer cette implémentation.

- Implémentation paramétrée

   L’implémentation paramétrée est prise en charge par l’Assistant Ajout de propriété. Une propriété paramétrable (parfois appelée un tableau de propriétés) peut être utilisée pour accéder à un ensemble de valeurs par le biais d’une seule propriété de votre contrôle. La macro d’entrée de la table de dispatch pour cette implémentation est DISP_PROPERTY_PARAM. Pour plus d’informations sur l’implémentation de ce type, consultez [implémentation d’une propriété paramétrable](mfc-activex-controls-advanced-topics.md) dans l’article contrôles ActiveX : Rubriques avancées.

## <a name="using-the-add-property-wizard-to-add-a-custom-property"></a><a name="_core_using_classwizard_to_add_a_custom_property"></a> Utilisation de l’Assistant Ajout de propriété pour ajouter une propriété personnalisée

La procédure suivante montre comment ajouter une propriété personnalisée, CircleOffset, qui utilise l’implémentation des méthodes obtenir/Set. La propriété personnalisée CircleOffset permet à l’utilisateur du contrôle de décaler le cercle à partir du centre du rectangle englobant du contrôle. La procédure d’ajout de propriétés personnalisées avec une implémentation autre que les méthodes d’obtenir/définir est très similaire.

Cette procédure peut également être utilisée pour ajouter d’autres propriétés personnalisées de votre choix. Remplacez le nom de la propriété CircleOffset et les paramètres par le nom de votre propriété personnalisée.

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>Pour ajouter la propriété personnalisée CircleOffset à l’aide de l’Assistant Ajout de propriété

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **Ajouter** , puis sur **Ajouter une propriété**.

   L' [Assistant Ajouter une propriété](../ide/adding-a-property-visual-cpp.md#names-add-property-wizard)s’ouvre.

1. Dans la zone nom de la **propriété** , tapez *CircleOffset*.

1. Pour **Type d’implémentation**, cliquez sur **Méthodes Get/Set**.

1. Dans la zone **type de propriété** , sélectionnez **`short`** .

1. Tapez des noms uniques pour vos fonctions obtenir et définir, ou acceptez les noms par défaut.

1. Cliquez sur **Terminer**.

## <a name="add-property-wizard-changes-for-custom-properties"></a><a name="_core_classwizard_changes_for_custom_properties"></a> Modifications de l’Assistant Ajout de propriété pour les propriétés personnalisées

Lorsque vous ajoutez la propriété personnalisée CircleOffset, l’Assistant Ajout de propriété apporte des modifications à l’en-tête (. H) et l’implémentation (. CPP) de la classe de contrôle.

Les lignes suivantes sont ajoutées à. Fichier H pour déclarer deux fonctions appelées `GetCircleOffset` et `SetCircleOffset` :

[!code-cpp[NVC_MFC_AxUI#25](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

La ligne suivante est ajoutée au de votre contrôle. Fichier IDL :

[!code-cpp[NVC_MFC_AxUI#26](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

Cette ligne affecte à la propriété CircleOffset un numéro d’identification spécifique, issu de la position de la méthode dans la liste méthodes et propriétés de l’Assistant Ajout de propriété.

En outre, la ligne suivante est ajoutée à la table de dispatch (dans le. CPP de la classe de contrôle) pour mapper la propriété CircleOffset aux deux fonctions de gestionnaire du contrôle :

[!code-cpp[NVC_MFC_AxUI#27](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

Enfin, les implémentations des `GetCircleOffset` fonctions et `SetCircleOffset` sont ajoutées à la fin du du contrôle. Fichier CPP. Dans la plupart des cas, vous allez modifier la fonction obtenir pour retourner la valeur de la propriété. La fonction Set contient généralement du code qui doit être exécuté avant ou après la modification de la propriété.

[!code-cpp[NVC_MFC_AxUI#28](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

Notez que l’Assistant Ajout de propriété ajoute automatiquement un appel, à [SetModifiedFlag](reference/colecontrol-class.md#setmodifiedflag), au corps de la fonction définie. L’appel de cette fonction marque le contrôle comme modifié. Si un contrôle a été modifié, son nouvel État sera enregistré lors de l’enregistrement du conteneur. Cette fonction doit être appelée chaque fois qu’une propriété, enregistrée dans le cadre de l’état persistant du contrôle, change de valeur.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : propriétés](mfc-activex-controls-properties.md)<br/>
[Contrôles ActiveX MFC : méthodes](mfc-activex-controls-methods.md)<br/>
[Classe COleControl](reference/colecontrol-class.md)
