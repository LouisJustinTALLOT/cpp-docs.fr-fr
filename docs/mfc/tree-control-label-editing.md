---
title: Étiquettes de contrôle d’arborescence modification | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- editing tree control labels
- CTreeCtrl class [MFC], editing labels
- label editing in CTreeCtrl class [MFC]
- tree controls [MFC], label editing
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d665ae37bfc843fc2ab0f24fe4489b76935e62d2
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956263"
---
# <a name="tree-control-label-editing"></a>Modification des étiquettes de contrôles d’arborescence
L’utilisateur peut modifier directement les étiquettes des éléments dans un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) qui a le **TVS_EDITLABELS** style. L’utilisateur commence à modifier en cliquant sur l’étiquette de l’élément qui a le focus. Une application commence à modifier à l’aide de la [EditLabel](../mfc/reference/ctreectrl-class.md#editlabel) fonction membre. Le contrôle d’arborescence envoie la notification lorsque la modification commence et lorsqu’elle est annulée ou terminée. Lorsque la modification est effectuée, vous êtes responsable de la mise à jour de l’étiquette de l’élément, le cas échéant.  
  
 Quand une modification d’étiquette commence, un contrôle d’arborescence envoie un [TVN_BEGINLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773506) message de notification. Par le traitement de cette notification, vous pouvez autoriser la modification de certaines étiquettes et empêcher d’autres. Retour de 0 autorise la modification et retour différente de zéro empêche.  
  
 Lors de la modification d’étiquette est annulée ou terminée, un contrôle d’arborescence envoie un [TVN_ENDLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773515) message de notification. Le *lParam* paramètre est l’adresse d’un [structure NMTVDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773418) structure. Le **élément** membre est une [structure TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) structure qui identifie l’élément et comprend le texte modifié. Vous êtes responsable de la mise à jour l’étiquette de l’élément, le cas échéant, par exemple après la validation de la chaîne modifiée. Le *pszText* membre `TV_ITEM` est 0 si la modification est annulée.  
  
 Au cours de la modification d’étiquette, généralement en réponse à la [TVN_BEGINLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773506) message de notification, vous pouvez obtenir un pointeur vers le contrôle d’édition utilisé pour la modification des étiquettes à l’aide de la [fonction membre GetEditControl](../mfc/reference/ctreectrl-class.md#geteditcontrol) membre fonction. Vous pouvez appeler le contrôle d’édition [SetLimitText](../mfc/reference/cedit-class.md#setlimittext) fonction membre pour limiter la quantité de texte, un utilisateur peut entrer ou sous-classe le contrôle d’édition pour intercepter et ignorer les caractères non valides. Toutefois, notez que le contrôle d’édition est affiché uniquement *après* **TVN_BEGINLABELEDIT** est envoyé.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

