---
title: 'Contrôles ActiveX MFC : ajout de méthodes stock'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
ms.openlocfilehash: ec59ccc0cbd48fc3114eb2dc0833dd3dd65691de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364670"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>Contrôles ActiveX MFC : ajout de méthodes stock

Une méthode de stock diffère d’une méthode personnalisée en ce qu’elle est déjà implémentée par la classe [COleControl](../mfc/reference/colecontrol-class.md). Par exemple, `COleControl` contient une fonction prédéfinie de membre qui prend en charge la méthode Refresh pour votre contrôle. L’entrée de carte de répartition pour cette méthode de stock est DISP_STOCKFUNC_REFRESH.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne devrait pas être utilisée pour de nouveaux développements. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, voir [ActiveX Controls](activex-controls.md).

`COleControl`prend en charge deux méthodes de stock : DoClick et Refresh. Refresh est invoqué par l’utilisateur du contrôle pour mettre immédiatement à jour l’apparence du contrôle; DoClick est invoqué pour tirer l’événement Click du contrôle.

|Méthode|Entrée de carte d’expédition|Commentaire|
|------------|------------------------|-------------|
|`DoClick`|**DISP_STOCKPROP_DOCLICK)**|Feux d’un événement Cliquez.|
|`Refresh`|**DISP_STOCKPROP_REFRESH)**|Mise immédiatement à jour de l’apparence du contrôle.|

## <a name="adding-a-stock-method-using-the-add-method-wizard"></a><a name="_core_adding_a_stock_method_using_classwizard"></a>Ajout d’une méthode stock à l’aide de l’assistant de méthode Add

L’ajout d’une méthode de stock est simple à l’aide de [l’Add Method Wizard](../ide/add-method-wizard.md). La procédure suivante démontre l’ajout de la méthode Refresh à un contrôle créé à l’aide du MFC ActiveX Control Wizard.

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>Pour ajouter la méthode De rafraîchissement du stock à l’aide de la méthode Add Wizard

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. À partir du menu raccourci, cliquez sur **Ajouter** et cliquez ensuite ajouter **la méthode**.

   Cela ouvre le Assistant Méthode Add.

1. Dans la boîte **De nom de méthode,** cliquez sur **Refresh**.

1. Cliquez sur **Terminer**.

## <a name="add-method-wizard-changes-for-stock-methods"></a><a name="_core_classwizard_changes_for_stock_methods"></a>Ajouter des modifications de magicien de méthode pour les méthodes de stock

Étant donné que la méthode De rafraîchissement des stocks est prise en charge par la classe de base du contrôle, **l’Add Method Wizard** ne modifie en aucune façon la déclaration de classe du contrôle. Il ajoute une entrée pour la méthode à la carte de répartition du contrôle et à son . Fichier IDL. La ligne suivante est ajoutée à la carte de répartition du contrôle, située dans sa mise en œuvre (. Dossier du RPC :

[!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

Cela rend la méthode Refresh à la disposition des utilisateurs du contrôle.

La ligne suivante est ajoutée à la ligne de contrôle . Fichier IDL:

[!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

Cette ligne attribue à la méthode Refresh un numéro d’identification spécifique.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)
