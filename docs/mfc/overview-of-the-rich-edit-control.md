---
title: Vue d'ensemble du contrôle RichEdit
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
ms.openlocfilehash: c45cb638ec860bb803c7de32065606dc3cc176b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160170"
---
# <a name="overview-of-the-rich-edit-control"></a>Vue d'ensemble du contrôle RichEdit

> [!IMPORTANT]
>  Si vous utilisez un contrôle RichEdit dans une boîte de dialogue (que votre application soit SDI, MDI ou basée sur la boîte de dialogue), vous devez appeler [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) une fois avant de la boîte de dialogue zone s’affiche. Un emplacement standard pour appeler cette fonction est de votre programme `InitInstance` fonction membre. Vous n’avez pas besoin de l’appeler à chaque fois que vous affichez la boîte de dialogue uniquement la première fois. Vous n’avez pas à appeler `AfxInitRichEdit` si vous travaillez avec `CRichEditView`.

Contrôles RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) fournissent une interface de programmation pour la mise en forme de texte. Toutefois, une application doit implémenter les composants d’interface utilisateur nécessaires pour rendre les opérations de mise en forme disponibles à l’utilisateur. Autrement dit, le RichEdit contrôle prend en charge la modification des attributs de caractère ou de paragraphe du texte sélectionné. Quelques exemples d’attributs sont des caractères gras, italique, famille de polices et taille exprimée en points. L’alignement, marges et taquets de tabulation sont des exemples d’attributs de paragraphe. Toutefois, il vous incombe de fournir l’interface utilisateur, que ce soit des boutons de barre d’outils, des éléments de menu ou une boîte de dialogue format caractère. Il existe également des fonctions pour interroger le contrôle rich edit pour les attributs de la sélection actuelle. Utilisez ces fonctions pour afficher les paramètres actuels pour les attributs, par exemple, définir une coche sur la commande interface utilisateur si la sélection comporte le caractère gras mise en forme d’attribut.

Pour plus d’informations sur les caractères et la mise en forme, consultez [mise en forme de caractère](../mfc/character-formatting-in-rich-edit-controls.md) et [mise en forme du paragraphe](../mfc/paragraph-formatting-in-rich-edit-controls.md) plus loin dans cette rubrique.

RichEdit prennent en charge presque toutes les opérations et les messages de notification utilisés avec les contrôles d’édition multiligne. Par conséquent, les applications que déjà utiliser des contrôles de modification peuvent être facilement modifiés pour utiliser des contrôles d’édition. Les messages supplémentaires et les notifications permettent aux applications à accéder à la fonctionnalité des contrôles uniques Rich edit. Pour plus d’informations sur les contrôles d’édition, consultez [CEdit](../mfc/reference/cedit-class.md).

Pour plus d’informations sur les notifications, consultez [Notifications à partir d’un contrôle Rich Edit](../mfc/notifications-from-a-rich-edit-control.md) plus loin dans cette rubrique.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
