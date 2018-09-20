---
title: Messages de Notification de contrôle d’arborescence | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], tree controls
- messages [MFC], notification
- CTreeCtrl class [MFC], notifications
- notifications [MFC], CTreeCtrl
- tree controls [MFC], notification messages
ms.assetid: ac7013b4-91dd-4668-bd75-439ca0680ef9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 07911dec25bf9d6b80f025e2f3738e3d98ffd2cb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390745"
---
# <a name="tree-control-notification-messages"></a>Messages de notification de contrôle d’arborescence

Un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) envoie des messages de notification suivants en tant que messages WM_NOTIFY :

|Message de notification|Description|
|--------------------------|-----------------|
|TVN_BEGINDRAG|Signale le début d’une opération de glisser-déplacer|
|TVN_BEGINLABELEDIT|Signale le début de la modification sur place|
|TVN_BEGINRDRAG|Signale le début d’une opération de glisser-déplacer, en utilisant le bouton droit de la souris|
|TVN_DELETEITEM|Signale la suppression d’un élément spécifique|
|TVN_ENDLABELEDIT|Signale la fin d’une modification d’étiquette|
|TVN_GETDISPINFO|Demande des informations que le contrôle d’arborescence nécessite pour afficher un élément|
|TVN_ITEMEXPANDED|Signale que la liste d’un élément parent des éléments enfants a été développée ou réduite|
|TVN_ITEMEXPANDING|Signale que la liste d’un élément parent des éléments enfants est sur le point d’être développée ou réduite|
|TVN_KEYDOWN|Signale un événement de clavier|
|TVN_SELCHANGED|Signale que la sélection a changé à partir d’un élément à un autre|
|TVN_SELCHANGING|Indique que la sélection est sur le point d’être modifié à partir d’un élément à un autre|
|TVN_SETDISPINFO|Notification pour mettre à jour les informations stockées pour un élément|

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

