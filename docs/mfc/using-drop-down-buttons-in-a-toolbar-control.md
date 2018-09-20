---
title: À l’aide des boutons de liste déroulante dans un contrôle de barre d’outils | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TBN_DROPDOWN
- TBSTYLE_EX_DRAWDDARROWS
dev_langs:
- C++
helpviewer_keywords:
- CToolBarCtrl class [MFC], drop-down buttons
- toolbars [MFC], drop-down buttons
- drop-down buttons in toolbars
- TBSTYLE_EX_DRAWDDARROWS
- TBN_DROPDOWN notification [MFC]
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac8b8c9f4460995aaab6a9d415202c2a965a6e9a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389041"
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>Utilisation de boutons de liste déroulante dans un contrôle ToolBar

En plus de boutons de commande standards, une barre d’outils peut également avoir des boutons de liste déroulante. Un bouton de liste déroulante est généralement indiqué par la présence d’une flèche bas attachée.

> [!NOTE]
>  La flèche bas attachée s’affiche uniquement si le style étendu de TBSTYLE_EX_DRAWDDARROWS a été définie.

Lorsque l’utilisateur clique sur cette flèche (ou le bouton si aucune flèche n’est présent), un message de notification TBN_DROPDOWN est envoyé au parent du contrôle de barre d’outils. Vous pouvez ensuite gérer cette notification et afficher un menu contextuel ; semblable à celui d’Internet Explorer.

La procédure suivante illustre comment implémenter un bouton de barre d’outils de la liste déroulante avec un menu contextuel :

### <a name="to-implement-a-drop-down-button"></a>Pour implémenter un bouton de liste déroulante

1. Une fois votre `CToolBarCtrl` objet a été créé, définissez le style TBSTYLE_EX_DRAWDDARROWS, en utilisant le code suivant :

     [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]

1. Définissez le style TBSTYLE_DROPDOWN pour tout nouveau ([InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton) ou [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) ou existant ([SetButtonInfo](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)) boutons qui seront des boutons de liste déroulante. L’exemple suivant illustre la modification d’un bouton existant dans un `CToolBarCtrl` objet :

     [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]

1. Ajouter un gestionnaire TBN_DROPDOWN à la classe parente de l’objet de barre d’outils.

     [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]

1. Dans le nouveau gestionnaire, afficher le menu contextuel approprié. Le code suivant illustre une méthode :

     [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

