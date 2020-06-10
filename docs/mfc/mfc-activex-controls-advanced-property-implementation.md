---
title: 'Contrôles ActiveX MFC : implémentation des propriétés avancées'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
ms.openlocfilehash: f5abef4db2f9c6d375428c0b0fd313198ce6283f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621228"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>Contrôles ActiveX MFC : implémentation des propriétés avancées

Cet article décrit les rubriques relatives à l’implémentation des propriétés avancées dans un contrôle ActiveX.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

- [Propriétés en lecture seule et en écriture seule](#_core_read2donly_and_write2donly_properties)

- [Renvoi de codes d’erreur à partir d’une propriété](#_core_returning_error_codes_from_a_property)

## <a name="read-only-and-write-only-properties"></a><a name="_core_read2donly_and_write2donly_properties"></a>Propriétés en lecture seule et en écriture seule

L’Assistant Ajout de propriété fournit une méthode simple et rapide pour implémenter les propriétés en lecture seule ou en écriture seule pour le contrôle.

#### <a name="to-implement-a-read-only-or-write-only-property"></a>Pour implémenter une propriété en lecture seule ou en écriture seule

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **Ajouter** , puis sur **Ajouter une propriété**.

   L' [Assistant Ajouter une propriété](../ide/names-add-property-wizard.md)s’ouvre.

1. Dans la zone nom de la **propriété** , tapez le nom de votre propriété.

1. Pour **Type d’implémentation**, cliquez sur **Méthodes Get/Set**.

1. Dans la zone **type de propriété** , sélectionnez le type approprié pour la propriété.

1. Si vous souhaitez une propriété en lecture seule, effacez le nom de la fonction Set. Si vous souhaitez une propriété en écriture seule, effacez le nom de la fonction obtenir.

1. Cliquez sur **Terminer**.

Dans ce cas, l’Assistant Ajout de propriété insère la fonction `SetNotSupported` ou `GetNotSupported` dans l’entrée de la table de dispatch à la place d’une fonction Set ou obtenir normale.

Si vous souhaitez modifier une propriété existante pour qu’elle soit en lecture seule ou en écriture seule, vous pouvez modifier la table de dispatch manuellement et supprimer la fonction Set ou obtenir inutile de la classe de contrôle.

Si vous souhaitez qu’une propriété soit en lecture seule ou en écriture seule (par exemple, uniquement lorsque votre contrôle fonctionne dans un mode particulier), vous pouvez fournir la fonction Set ou obtenir, comme d’habitude, et appeler la `SetNotSupported` fonction ou le `GetNotSupported` cas échéant. Par exemple :

[!code-cpp[NVC_MFC_AxUI#29](codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]

Cet exemple de code appelle `SetNotSupported` si le `m_bReadOnlyMode` membre de données a la **valeur true**. Si la valeur est **false**, la propriété est définie sur la nouvelle valeur.

## <a name="returning-error-codes-from-a-property"></a><a name="_core_returning_error_codes_from_a_property"></a>Renvoi de codes d’erreur à partir d’une propriété

Pour indiquer qu’une erreur s’est produite lors de la tentative d’obtenir ou de définir une propriété, utilisez la `COleControl::ThrowError` fonction, qui prend un SCODE (code d’État) comme paramètre. Vous pouvez utiliser un SCODE prédéfini ou définir l’un de vos propres. Pour obtenir la liste des SCODEs prédéfinis et des instructions permettant de définir des SCODEs personnalisés, consultez [gestion des erreurs dans votre contrôle ActiveX](mfc-activex-controls-advanced-topics.md) dans l’article contrôles ActiveX : Rubriques avancées.

Les fonctions d’assistance existent pour les SCODEs prédéfinis les plus courants, tels que [COleControl :: SetNotSupported](reference/colecontrol-class.md#setnotsupported), [COleControl :: GetNotSupported](reference/colecontrol-class.md#getnotsupported)et [COleControl :: SetNotPermitted](reference/colecontrol-class.md#setnotpermitted).

> [!NOTE]
> `ThrowError`est destiné à être utilisé uniquement comme moyen de retourner une erreur à partir d’une fonction d’extraction ou de définition d’une propriété ou d’une méthode Automation. Il s’agit de la seule fois où le gestionnaire d’exceptions approprié sera présent sur la pile.

Pour plus d’informations sur la création de rapports d’exceptions dans d’autres zones du code, consultez [COleControl :: FireError (](reference/colecontrol-class.md#fireerror) et la section [gestion des erreurs dans votre contrôle ActiveX](mfc-activex-controls-advanced-topics.md) dans l’article contrôles ActiveX : Rubriques avancées.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : propriétés](mfc-activex-controls-properties.md)<br/>
[Contrôles ActiveX MFC : méthodes](mfc-activex-controls-methods.md)<br/>
[COleControl, classe](reference/colecontrol-class.md)
