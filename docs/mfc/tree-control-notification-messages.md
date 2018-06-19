---
title: Les Messages de Notification de contrôle d’arborescence | Documents Microsoft
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
ms.openlocfilehash: f7c352da9f9283f53c926a8223984620ee7fa6ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385734"
---
# <a name="tree-control-notification-messages"></a>Messages de notification de contrôle d’arborescence
Un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) envoie les messages de notification suivants en tant que **WM_NOTIFY** messages :  
  
|Message de notification|Description|  
|--------------------------|-----------------|  
|**TVN_BEGINDRAG**|Signale le début d’une opération de glisser-déplacer|  
|**TVN_BEGINLABELEDIT**|Signale le début de la modification sur place|  
|**TVN_BEGINRDRAG**|Signale le début d’une opération de glisser-déplacer, l’aide du bouton droit de la souris|  
|**TVN_DELETEITEM**|Signale la suppression d’un élément spécifique|  
|**TVN_ENDLABELEDIT**|Signale la fin d’une modification d’étiquette|  
|**TVN_GETDISPINFO**|Demandes informations requises pour que le contrôle d’arborescence pour afficher un élément|  
|**TVN_ITEMEXPANDED**|Signale que la liste d’un élément parent des éléments enfants a été développée ou réduite|  
|**TVN_ITEMEXPANDING**|Indique que la liste d’un élément parent des éléments enfants est sur le point d’être développée ou réduite|  
|**TVN_KEYDOWN**|Signale un événement de clavier|  
|**TVN_SELCHANGED**|Indique que la sélection a changé d’un élément à un autre|  
|**TVN_SELCHANGING**|Indique que la sélection est sur le point d’être modifié à partir d’un élément à un autre|  
|**TVN_SETDISPINFO**|Notification pour mettre à jour les informations stockées pour un élément|  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

