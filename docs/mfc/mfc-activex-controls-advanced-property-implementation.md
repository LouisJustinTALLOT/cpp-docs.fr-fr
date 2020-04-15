---
title: 'Contrôles ActiveX MFC : implémentation des propriétés avancées'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
ms.openlocfilehash: d4f1265e6540e9f84bdb680e7948a4e308d31bb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364649"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>Contrôles ActiveX MFC : implémentation des propriétés avancées

Cet article décrit des sujets liés à la mise en œuvre de propriétés avancées dans un contrôle ActiveX.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne devrait pas être utilisée pour de nouveaux développements. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, voir [ActiveX Controls](activex-controls.md).

- [Propriétés de lecture seulement et d’écriture seulement](#_core_read2donly_and_write2donly_properties)

- [Retour des codes d’erreur d’une propriété](#_core_returning_error_codes_from_a_property)

## <a name="read-only-and-write-only-properties"></a><a name="_core_read2donly_and_write2donly_properties"></a>Propriétés Read-Only et Write-Only

L’Add Property Wizard fournit une méthode rapide et facile pour implémenter des propriétés de lecture seulement ou d’écrire uniquement pour le contrôle.

#### <a name="to-implement-a-read-only-or-write-only-property"></a>Mettre en œuvre une propriété lue ou une propriété uniquement d’écriture

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. À partir du menu raccourci, cliquez sur **Ajouter** et cliquez ensuite **ajouter la propriété**.

   Cela ouvre le [Add Property Wizard](../ide/names-add-property-wizard.md).

1. Dans la boîte **nom de propriété,** tapez le nom de votre propriété.

1. Pour **Type d’implémentation**, cliquez sur **Méthodes Get/Set**.

1. Dans la boîte **de type de propriété,** sélectionnez le type approprié pour la propriété.

1. Si vous voulez une propriété lue uniquement, effacez le nom de fonction Set. Si vous voulez une propriété d’écriture seulement, effacer le nom de fonction Get.

1. Cliquez sur **Terminer**.

Lorsque vous faites cela, l’Add `SetNotSupported` Property `GetNotSupported` Wizard insère la fonction ou dans l’entrée de la carte de répartition à la place d’un ensemble normal ou de la fonction Get.

Si vous souhaitez modifier une propriété existante pour être lue uniquement ou écrire uniquement, vous pouvez modifier manuellement la carte de répartition et supprimer la fonction d’ensemble ou d’obtenir inutile de la classe de contrôle.

Si vous voulez qu’une propriété soit lue sous condition seulement ou qu’elle n’écrit que (par exemple, seulement lorsque votre `SetNotSupported` `GetNotSupported` contrôle fonctionne dans un mode particulier), vous pouvez fournir la fonction Set or Get, comme d’habitude, et appeler le ou la fonction le cas échéant. Par exemple :

[!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]

Cet échantillon `SetNotSupported` de `m_bReadOnlyMode` code appelle si le membre des données est **VRAI**. Si **FALSE**, alors la propriété est réglée à la nouvelle valeur.

## <a name="returning-error-codes-from-a-property"></a><a name="_core_returning_error_codes_from_a_property"></a>Retour des codes d’erreur d’une propriété

Pour indiquer qu’une erreur s’est produite en `COleControl::ThrowError` tentant d’obtenir ou de définir une propriété, utilisez la fonction, qui prend un SCODE (code d’état) comme paramètre. Vous pouvez utiliser un SCODE prédéfini ou définir l’un des vôtres. Pour une liste de SCODE prédéfinis et des instructions pour définir les SCODE personnalisés, voir [erreurs de manipulation dans votre contrôle ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) dans l’article ActiveX contrôles: Sujets avancés.

Les fonctions d’aide existent pour les SCODE prédéfinis les plus communs, telles que [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), et [COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

> [!NOTE]
> `ThrowError`est destiné à être utilisé uniquement comme un moyen de retourner une erreur à partir de l’intérieur d’une propriété Get or Set fonction ou une méthode d’automatisation. Ce sont les seules fois où le gestionnaire d’exception approprié sera présent sur la pile.

Pour plus d’informations sur les exceptions de rapport dans d’autres domaines du code, voir [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) et la section [Fautes de manipulation dans votre contrôle ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) dans l’article ActiveX Controls: Advanced Topics.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : propriétés](../mfc/mfc-activex-controls-properties.md)<br/>
[Contrôles ActiveX MFC : méthodes](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl, classe](../mfc/reference/colecontrol-class.md)
