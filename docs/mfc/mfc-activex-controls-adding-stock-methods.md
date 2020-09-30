---
title: 'Contrôles ActiveX MFC : ajout de méthodes stock'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
ms.openlocfilehash: b4b01e4fb202cfd7a923d22cb57ce5ec6988e11d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502283"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>Contrôles ActiveX MFC : ajout de méthodes stock

Une méthode stock diffère d’une méthode personnalisée en ce qu’elle est déjà implémentée par la classe [COleControl](reference/colecontrol-class.md). Par exemple, `COleControl` contient une fonction membre prédéfinie qui prend en charge la méthode Refresh pour votre contrôle. L’entrée de la table de dispatch pour cette méthode stock est DISP_STOCKFUNC_REFRESH.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

`COleControl` prend en charge deux méthodes stock : le faire-cliquer et actualiser. L’actualisation est appelée par l’utilisateur du contrôle pour mettre immédiatement à jour l’apparence du contrôle. Le fait de cliquer est appelé pour déclencher l’événement Click du contrôle.

|Méthode|Entrée de la table de dispatch|Commentaire|
|------------|------------------------|-------------|
|`DoClick`|**DISP_STOCKPROP_DOCLICK ()**|Déclenche un événement Click.|
|`Refresh`|**DISP_STOCKPROP_REFRESH ()**|Met immédiatement à jour l’apparence du contrôle.|

## <a name="adding-a-stock-method-using-the-add-method-wizard"></a><a name="_core_adding_a_stock_method_using_classwizard"></a> Ajout d’une méthode stock à l’aide de l’Assistant Ajout de méthode

L’ajout d’une méthode stock est simple à l’aide de l' [Assistant Ajout de méthode](../ide/adding-a-method-visual-cpp.md#add-method-wizard). La procédure suivante montre comment ajouter la méthode Refresh à un contrôle créé à l’aide de l’Assistant contrôle ActiveX MFC.

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>Pour ajouter la méthode d’actualisation des stocks à l’aide de l’Assistant Ajout de méthode

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **Ajouter** , puis sur **Ajouter une méthode**.

   L’Assistant Ajout de méthode s’ouvre.

1. Dans la zone nom de la **méthode** , cliquez sur **Actualiser**.

1. Cliquez sur **Terminer**.

## <a name="add-method-wizard-changes-for-stock-methods"></a><a name="_core_classwizard_changes_for_stock_methods"></a> Modifications de l’Assistant Ajout de méthode pour les méthodes stock

Étant donné que la méthode d’actualisation des actions est prise en charge par la classe de base du contrôle, l' **Assistant Ajout de méthode** ne modifie en aucune façon la déclaration de classe du contrôle. Elle ajoute une entrée pour la méthode au mappage de dispatch du contrôle et à son. Fichier IDL. La ligne suivante est ajoutée au mappage de dispatch du contrôle, situé dans son implémentation (. CPP) :

[!code-cpp[NVC_MFC_AxUI#16](codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

La méthode Refresh est ainsi mise à la disposition des utilisateurs du contrôle.

La ligne suivante est ajoutée au du contrôle. Fichier IDL :

[!code-cpp[NVC_MFC_AxUI#17](codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

Cette ligne affecte à la méthode Refresh un numéro d’identification spécifique.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)
