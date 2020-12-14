---
description: 'En savoir plus sur : messages de notification de contrôle d’arborescence'
title: Messages de notification de contrôle d'arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], tree controls
- messages [MFC], notification
- CTreeCtrl class [MFC], notifications
- notifications [MFC], CTreeCtrl
- tree controls [MFC], notification messages
ms.assetid: ac7013b4-91dd-4668-bd75-439ca0680ef9
ms.openlocfilehash: 899b6469a2de9a076dd33e62c5023f502448d45f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263983"
---
# <a name="tree-control-notification-messages"></a>Messages de notification de contrôle d'arborescence

Un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) envoie les messages de notification suivants sous forme de messages WM_NOTIFY :

|Message de notification|Description|
|--------------------------|-----------------|
|TVN_BEGINDRAG|Signale le début d’une opération de glisser-déplacer|
|TVN_BEGINLABELEDIT|Signale le début de la modification des étiquettes sur place|
|TVN_BEGINRDRAG|Signale le début d’une opération de glisser-déplacer, à l’aide du bouton droit de la souris|
|TVN_DELETEITEM|Signale la suppression d’un élément spécifique|
|TVN_ENDLABELEDIT|Signale la fin de la modification de l’étiquette|
|TVN_GETDISPINFO|Demande les informations dont le contrôle d’arborescence a besoin pour afficher un élément|
|TVN_ITEMEXPANDED|Signale que la liste des éléments enfants d’un élément parent a été développée ou réduite|
|TVN_ITEMEXPANDING|Signale que la liste des éléments enfants d’un élément parent est sur le point d’être développée ou réduite|
|TVN_KEYDOWN|Signale un événement de clavier|
|TVN_SELCHANGED|Signale que la sélection est passée d’un élément à un autre|
|TVN_SELCHANGING|Signale que la sélection est sur le point d’être modifiée d’un élément à un autre|
|TVN_SETDISPINFO|Notification pour mettre à jour les informations conservées pour un élément|

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
