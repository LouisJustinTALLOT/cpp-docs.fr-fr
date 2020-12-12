---
description: 'En savoir plus sur : vue d’ensemble du contrôle RichEdit'
title: Vue d'ensemble du contrôle RichEdit
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
ms.openlocfilehash: 9971eb7340ddf270c6094d239737c89cff66e6e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205965"
---
# <a name="overview-of-the-rich-edit-control"></a>Vue d'ensemble du contrôle RichEdit

> [!IMPORTANT]
> Si vous utilisez un contrôle RichEdit dans une boîte de dialogue (que votre application soit SDI, MDI ou basée sur une boîte de dialogue), vous devez appeler [AfxInitRichEdit](reference/application-information-and-management.md#afxinitrichedit) une fois pour que la boîte de dialogue s’affiche. Vous pouvez appeler cette fonction dans la fonction membre de votre programme `InitInstance` . Vous n’avez pas besoin de l’appeler pour chaque fois que vous affichez la boîte de dialogue, uniquement la première fois. Vous n’avez pas besoin d’appeler `AfxInitRichEdit` si vous utilisez `CRichEditView` .

Les contrôles Rich Edit ([CRichEditCtrl](reference/cricheditctrl-class.md)) fournissent une interface de programmation pour mettre en forme le texte. Toutefois, une application doit implémenter tous les composants d’interface utilisateur nécessaires pour rendre les opérations de mise en forme disponibles pour l’utilisateur. Autrement dit, le contrôle Rich Edit prend en charge la modification des attributs de caractère ou de paragraphe du texte sélectionné. Voici quelques exemples d’attributs de caractères : gras, italique, famille de polices et taille de point. Parmi les exemples d’attributs de paragraphe figurent l’alignement, les marges et les taquets de tabulation. Toutefois, il vous revient de fournir l’interface utilisateur, qu’il s’agisse de boutons de barre d’outils, d’éléments de menu ou d’une boîte de dialogue de caractères de format. Il existe également des fonctions permettant d’interroger le contrôle Rich Edit pour les attributs de la sélection actuelle. Utilisez ces fonctions pour afficher les paramètres actuels des attributs, par exemple, en définissant une coche sur l’interface utilisateur de la commande si la sélection a l’attribut de mise en forme de caractères gras.

Pour plus d’informations sur la mise en forme des caractères et des paragraphes, consultez mise en forme des [caractères](character-formatting-in-rich-edit-controls.md) et [mise en forme des paragraphes](paragraph-formatting-in-rich-edit-controls.md) plus loin dans cette rubrique.

Les contrôles RichEdit prennent en charge la quasi-totalité des opérations et des messages de notification utilisés avec les contrôles d’édition multiligne. Ainsi, les applications qui utilisent déjà les contrôles d’édition peuvent être facilement modifiées pour utiliser des contrôles RichEdit. Des messages supplémentaires et des notifications permettent aux applications d’accéder aux fonctionnalités propres aux contrôles RichEdit. Pour plus d’informations sur les contrôles d’édition, consultez [CEdit](reference/cedit-class.md).

Pour plus d’informations sur les notifications, consultez [notifications à partir d’un contrôle](notifications-from-a-rich-edit-control.md) RichEdit plus loin dans cette rubrique.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](using-cricheditctrl.md)<br/>
[Contrôles](controls-mfc.md)
