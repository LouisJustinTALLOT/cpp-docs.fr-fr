---
title: 'Contrôles ActiveX MFC : Ajout de méthodes Stock | Microsoft Docs'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7967b63a14c296d7f0d73bb403aa5b74a6c3689b
ms.sourcegitcommit: a3c9e7888b8f437a170327c4c175733ad9eb0454
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50204301"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>Contrôles ActiveX MFC : ajout de méthodes stock

Une méthode stockée diffère d’une méthode personnalisée car il est déjà implémenté par classe [COleControl](../mfc/reference/colecontrol-class.md). Par exemple, `COleControl` contient une fonction membre prédéfinie qui prend en charge de la méthode d’actualisation pour votre contrôle. L’entrée de mappage de répartition pour cette méthode stockée est DISP_STOCKFUNC_REFRESH.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

`COleControl` prend en charge deux méthodes stock : DoClick et l’actualisation. L’actualisation est appelée par l’utilisateur du contrôle pour mettre immédiatement à jour l’apparence du contrôle ; DoClick est appelée pour déclencher Click du contrôle événement.

|Méthode|Entrée de mappage de dispatch|Commentaire|
|------------|------------------------|-------------|
|`DoClick`|**() DISP_STOCKPROP_DOCLICK**|Déclenche un événement Click.|
|`Refresh`|**() DISP_STOCKPROP_REFRESH**|Met immédiatement à jour de l’apparence du contrôle.|

##  <a name="_core_adding_a_stock_method_using_classwizard"></a> Ajout d’une méthode Stock à l’aide de l’Assistant Ajout de méthode

Ajout d’une méthode stockée est simple à l’aide de la [Assistant Ajout de méthode](../ide/add-method-wizard.md). La procédure suivante illustre l’ajout de la méthode d’actualisation pour un contrôle créé à l’aide de l’Assistant de contrôle ActiveX MFC.

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>Pour ajouter la méthode stock Refresh à l’aide de l’Assistant Ajout de méthode

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter une méthode**.

   Cette opération ouvre l’Assistant Ajout de méthode.

1. Dans le **nom de la méthode** , cliquez sur **Actualiser**.

1. Cliquez sur **Terminer**.

##  <a name="_core_classwizard_changes_for_stock_methods"></a> Méthode modifications effectuées Assistant Ajout de méthodes Stock

Étant donné que la méthode stock Refresh est pris en charge par la classe de base du contrôle, le **Assistant Ajout de méthode** ne modifie pas la déclaration de classe du contrôle en aucune façon. Il ajoute une entrée pour la méthode à la table de dispatch du contrôle et à ses. Fichier IDL. La ligne suivante est ajoutée à la table de dispatch du contrôle, située dans son implémentation (. Fichier CPP) :

[!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

La méthode d’actualisation sont ainsi disponibles pour les utilisateurs du contrôle.

La ligne suivante est ajoutée pour le contrôle. Fichier IDL :

[!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

Cette ligne affecte un numéro d’identification spécifique à la méthode d’actualisation.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

