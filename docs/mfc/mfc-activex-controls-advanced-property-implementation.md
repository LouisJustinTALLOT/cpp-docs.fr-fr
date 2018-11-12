---
title: 'Contrôles ActiveX MFC : implémentation des propriétés avancées'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
ms.openlocfilehash: d26dbcb1c18c3c939214051d9010cb5b6db90929
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568023"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>Contrôles ActiveX MFC : implémentation des propriétés avancées

Cet article décrit les rubriques relatives à l’implémentation des propriétés avancées dans un contrôle ActiveX.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

- [Propriétés en lecture seule et en écriture seule](#_core_read2donly_and_write2donly_properties)

- [Renvoi des codes d’erreur à partir d’une propriété](#_core_returning_error_codes_from_a_property)

##  <a name="_core_read2donly_and_write2donly_properties"></a> Propriétés en lecture seule et en écriture seule

L’Assistant Ajout de propriété fournit une méthode rapide et simple pour implémenter des propriétés en lecture seule ou en écriture seule pour le contrôle.

#### <a name="to-implement-a-read-only-or-write-only-property"></a>Pour implémenter une propriété en lecture seule ou en écriture seule

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter une propriété**.

   Cette opération ouvre le [Assistant Ajout de propriété](../ide/names-add-property-wizard.md).

1. Dans le **nom de la propriété** , tapez le nom de votre propriété.

1. Pour **Type d’implémentation**, cliquez sur **Méthodes Get/Set**.

1. Dans le **Type de propriété** , sélectionnez le type approprié pour la propriété.

1. Si vous souhaitez une propriété en lecture seule, désactivez le nom de la fonction Set. Si vous souhaitez une propriété en écriture seule, désactivez le nom de la fonction Get.

9. Cliquez sur **Terminer**.

Lorsque vous effectuez cette opération, l’Assistant Ajout de propriété insère la fonction `SetNotSupported` ou `GetNotSupported` dans l’entrée de mappage de distribution à la place d’un élément normal Set ou Get (fonction).

Si vous souhaitez modifier une propriété existante pour être en lecture seule ou en écriture seule, vous pouvez modifier manuellement de la table de dispatch et supprimer la fonction Set ou Get inutile de la classe de contrôle.

Si vous souhaitez une propriété conditionnellement en lecture seule ou en écriture seule (par exemple, uniquement lorsque votre contrôle fonctionne dans un mode particulier), vous pouvez fournir la fonction Set ou Get, comme d’habitude et appeler le `SetNotSupported` ou `GetNotSupported` fonction des nécessités. Exemple :

[!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]

Cet exemple de code appelle `SetNotSupported` si le `m_bReadOnlyMode` est membre de données **TRUE**. Si **FALSE**, puis la propriété est définie sur la nouvelle valeur.

##  <a name="_core_returning_error_codes_from_a_property"></a> Renvoi des Codes d’erreur à partir d’une propriété

Pour indiquer qu’une erreur s’est produite lors de la tentative obtenir ou définir une propriété, utilisez le `COleControl::ThrowError` (fonction), qui prend SCODE (code d’état) en tant que paramètre. Vous pouvez utiliser un SCODE prédéfini ou définir votre propre. Pour obtenir la liste de paramètres prédéfinis SCODEs et obtenir des instructions pour la définition SCODEs personnalisés, consultez [gestion des erreurs dans votre contrôle ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) dans les contrôles ActiveX : rubriques avancées.

Fonctions d’assistance existent pour la plus courante prédéfinies SCODEs, tel que [courants ;](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), et [COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

> [!NOTE]
>  `ThrowError` est destiné à être utilisé uniquement comme un moyen de retourner une erreur à partir d’au sein Get d’une propriété ou Set fonction ou une méthode automation. Il s’agit de la seule fois où le Gestionnaire d’exceptions approprié sera présent sur la pile.

Pour plus d’informations sur le rapport des exceptions dans d’autres zones du code, consultez [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) et la section [gestion des erreurs dans votre contrôle ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) dans l’article contrôles ActiveX : avancé Rubriques.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : propriétés](../mfc/mfc-activex-controls-properties.md)<br/>
[Contrôles ActiveX MFC : méthodes](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl, classe](../mfc/reference/colecontrol-class.md)
