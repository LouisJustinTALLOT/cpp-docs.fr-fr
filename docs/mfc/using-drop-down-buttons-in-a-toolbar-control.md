---
description: 'En savoir plus sur : utilisation de boutons Drop-Down dans un contrôle ToolBar'
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
ms.openlocfilehash: a37f39397f6b6f66bed1ad1d2fbd9530b55f3d7b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154459"
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>Utilisation de boutons de liste déroulante dans un contrôle ToolBar

Outre les boutons de commande standard, une barre d’outils peut également comporter des boutons déroulants. Un bouton déroulant est généralement indiqué par la présence d’une flèche vers le bas attaché.

> [!NOTE]
> La flèche vers le bas attaché s’affiche uniquement si le style étendu TBSTYLE_EX_DRAWDDARROWS a été défini.

Quand l’utilisateur clique sur cette flèche (ou sur le bouton lui-même, si aucune flèche n’est présente), un TBN_DROPDOWN message de notification est envoyé au parent du contrôle ToolBar. Vous pouvez ensuite gérer cette notification et afficher un menu contextuel. similaire au comportement d’Internet Explorer.

La procédure suivante montre comment implémenter un bouton déroulant de barre d’outils avec un menu contextuel :

### <a name="to-implement-a-drop-down-button"></a>Pour implémenter un bouton déroulant

1. Une fois que votre `CToolBarCtrl` objet a été créé, définissez le style de TBSTYLE_EX_DRAWDDARROWS à l’aide du code suivant :

   [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]

1. Définissez le style de TBSTYLE_DROPDOWN pour les boutons nouveaux ([InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton) ou [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) ou existants ([SetButtonInfo](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)) qui seront des boutons déroulants. L’exemple suivant illustre la modification d’un bouton existant dans un `CToolBarCtrl` objet :

   [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]

1. Ajoutez un gestionnaire de TBN_DROPDOWN à la classe parente de l’objet Toolbar.

   [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]

1. Dans le nouveau gestionnaire, affichez le menu contextuel approprié. Le code suivant illustre une méthode :

   [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
