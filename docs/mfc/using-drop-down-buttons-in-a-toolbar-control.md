---
title: Utilisation de boutons de liste déroulante dans un contrôle ToolBar
ms.date: 11/04/2016
f1_keywords:
- TBN_DROPDOWN
- TBSTYLE_EX_DRAWDDARROWS
helpviewer_keywords:
- CToolBarCtrl class [MFC], drop-down buttons
- toolbars [MFC], drop-down buttons
- drop-down buttons in toolbars
- TBSTYLE_EX_DRAWDDARROWS
- TBN_DROPDOWN notification [MFC]
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
ms.openlocfilehash: 0bc4df4c07ec4b8bc5b488925cbb140609302186
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365065"
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>Utilisation de boutons de liste déroulante dans un contrôle ToolBar

En plus des boutons poussoirs standard, une barre d’outils peut également avoir des boutons de chute. Un bouton de chute est généralement indiqué par la présence d’une flèche attachée vers le bas.

> [!NOTE]
> La flèche vers le bas attachée n’apparaîtra que si le style étendu TBSTYLE_EX_DRAWDDARROWS a été défini.

Lorsque l’utilisateur clique sur cette flèche (ou le bouton lui-même, si aucune flèche n’est présente), un message de notification TBN_DROPDOWN est envoyé au parent du contrôle de la barre d’outils. Vous pouvez ensuite gérer cette notification et afficher un menu pop-up; similaire au comportement d’Internet Explorer.

La procédure suivante illustre comment implémenter un bouton de barre d’outils déroulant avec un menu pop-up :

### <a name="to-implement-a-drop-down-button"></a>Pour implémenter un bouton de baisse

1. Une `CToolBarCtrl` fois que votre objet a été créé, définissez le style TBSTYLE_EX_DRAWDDARROWS, en utilisant le code suivant :

   [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]

1. Réglez le style TBSTYLE_DROPDOWN pour tous les nouveaux boutons ([InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton) ou [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) ou existants ([SetButtonInfo)](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)qui seront des boutons de chute. L’exemple suivant montre la modification `CToolBarCtrl` d’un bouton existant dans un objet :

   [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]

1. Ajoutez un gestionnaire de TBN_DROPDOWN à la classe mère de l’objet de la barre d’outils.

   [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]

1. Dans le nouveau gestionnaire, affichez le menu popup approprié. Le code suivant démontre une méthode :

   [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
