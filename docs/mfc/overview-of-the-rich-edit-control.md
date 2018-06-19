---
title: Vue d’ensemble du contrôle RichEdit | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 143fc93fb07d9ac7c4e803bbce426c114c02bfeb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349972"
---
# <a name="overview-of-the-rich-edit-control"></a>Vue d'ensemble du contrôle RichEdit
> [!IMPORTANT]
>  Si vous utilisez un contrôle RichEdit dans une boîte de dialogue (que votre application soit SDI, MDI ou basée sur une boîte de dialogue), vous devez appeler [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) une fois avant de la boîte de dialogue zone s’affiche. Un emplacement standard pour appeler cette fonction est de votre programme `InitInstance` fonction membre. Vous n’avez pas besoin de l’appeler à chaque fois que vous affichez la boîte de dialogue uniquement la première fois. Vous n’avez pas à appeler `AfxInitRichEdit` si vous travaillez avec `CRichEditView`.  
  
 Contrôles RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) fournissent une interface de programmation pour la mise en forme de texte. Toutefois, une application doit implémenter tous les composants d’interface utilisateur nécessaires pour effectuer les opérations de mise en forme disponibles à l’utilisateur. Autrement dit, le RichEdit contrôle prend en charge la modification des attributs de caractère ou de paragraphe du texte sélectionné. Quelques exemples d’attributs sont des caractères gras, italique, famille de polices et taille en points. Alignement, les marges et les taquets de tabulation sont des exemples d’attributs de paragraphe. Toutefois, c’est à vous pour fournir l’interface utilisateur, que ce soit des boutons de barre d’outils, les éléments de menu ou une boîte de dialogue format caractère. Il existe également des fonctions pour interroger le contrôle d’édition enrichi pour les attributs de la sélection actuelle. Utilisez ces fonctions pour afficher les paramètres actuels pour les attributs, par exemple, définir une coche sur la commande de l’interface utilisateur si la sélection a l’attribut de mise en forme gras.  
  
 Pour plus d’informations sur les caractères et la mise en forme, consultez [mise en forme du caractère](../mfc/character-formatting-in-rich-edit-controls.md) et [mise en forme du paragraphe](../mfc/paragraph-formatting-in-rich-edit-controls.md) plus loin dans cette rubrique.  
  
 RichEdit prennent en charge presque toutes les opérations et les messages de notification utilisés avec les contrôles d’édition multiligne. Par conséquent, les applications que déjà utiliser les contrôles d’édition peuvent être facilement modifiés pour utiliser le riche contrôles d’édition. Les messages supplémentaires et les notifications permettent aux applications accéder à la fonctionnalité des contrôles uniques Rich edit. Pour plus d’informations sur les contrôles d’édition, consultez [CEdit](../mfc/reference/cedit-class.md).  
  
 Pour plus d’informations sur les notifications, consultez [des Notifications à partir d’un contrôle RichEdit](../mfc/notifications-from-a-rich-edit-control.md) plus loin dans cette rubrique.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

