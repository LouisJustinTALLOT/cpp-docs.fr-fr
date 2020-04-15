---
title: Vue d'ensemble du contrôle RichEdit
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
ms.openlocfilehash: 9ef696bc348dfb18b797b487224b97261020e11c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366873"
---
# <a name="overview-of-the-rich-edit-control"></a>Vue d'ensemble du contrôle RichEdit

> [!IMPORTANT]
> Si vous utilisez un contrôle d’édition riche dans une boîte de dialogue (indépendamment du fait que votre application soit SDI, MDI ou basée sur le dialogue), vous devez appeler [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) une fois avant que la boîte de dialogue ne s’affiche. Un endroit typique pour appeler cette fonction `InitInstance` est dans la fonction de membre de votre programme. Vous n’avez pas besoin de l’appeler pour chaque fois que vous affichez la boîte de dialogue, seulement la première fois. Vous n’avez `AfxInitRichEdit` pas à appeler `CRichEditView`si vous travaillez avec .

Les contrôles d’édition riches ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) fournissent une interface de programmation pour le formatage du texte. Toutefois, une application doit implémenter tous les composants d’interface utilisateur nécessaires pour mettre les opérations de formatage à la disposition de l’utilisateur. Autrement dit, le contrôle de modification riche prend en charge la modification des attributs de caractère ou de paragraphe du texte sélectionné. Quelques exemples d’attributs de caractère sont audacieux, italiques, famille de police, et la taille de point. Des exemples d’attributs de paragraphe incluent l’alignement, les marges et les arrêts d’onglet. Cependant, c’est à vous de fournir l’interface utilisateur, qu’il s’agisse de boutons de barre d’outils, d’éléments de menu ou d’une boîte de dialogue de caractères format. Il ya aussi des fonctions pour interroger le contrôle de modification riche pour les attributs de la sélection actuelle. Utilisez ces fonctions pour afficher les paramètres actuels pour les attributs, par exemple, en définissant une marque de contrôle sur l’interface utilisateur de commande si la sélection a l’attribut de formatage de caractère audacieux.

Pour plus d’informations sur le formatage des caractères et des paragraphes, voir [Formatting des personnages](../mfc/character-formatting-in-rich-edit-controls.md) et [formatage de paragraphe](../mfc/paragraph-formatting-in-rich-edit-controls.md) plus tard dans ce sujet.

Les contrôles d’édition riches prennent en charge la quasi-totalité des opérations et des messages de notification utilisés avec les contrôles de modification multilignes. Ainsi, les applications qui utilisent déjà des contrôles de modification peuvent être facilement modifiées pour utiliser de riches contrôles d’édition. Des messages et des notifications supplémentaires permettent aux applications d’accéder à la fonctionnalité unique aux contrôles de modification riches. Pour plus d’informations sur les contrôles de modification, voir [CEdit](../mfc/reference/cedit-class.md).

Pour plus d’informations sur les notifications, voir [Notifications from a Rich Edit Control](../mfc/notifications-from-a-rich-edit-control.md) plus tard dans ce sujet.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
