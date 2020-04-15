---
title: Personnalisation de l'apparence d'un contrôle ToolBar
ms.date: 11/04/2016
f1_keywords:
- TBSTYLE_
helpviewer_keywords:
- flat toolbars
- CToolBar class [MFC], styles
- transparent toolbars
- TBSTYLE_ styles [MFC]
- CToolBarCtrl class [MFC], object styles
- toolbar controls [MFC], style
ms.assetid: fd0a73db-7ad1-4fe4-889b-02c3980f49e8
ms.openlocfilehash: 9f4f9d90113d5074555d1b0cc411f854abc67fe5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377460"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>Personnalisation de l'apparence d'un contrôle ToolBar

La `CToolBarCtrl` classe fournit de nombreux styles qui affectent l’apparence (et, à l’occasion, le comportement) de l’objet de la barre d’outils. Modifier l’objet de `dwCtrlStyle` la barre `CToolBarCtrl::Create` d’outils en définissant le paramètre de la fonction membre (ou) `CToolBar::CreateEx`lorsque vous créez pour la première fois le contrôle de la barre d’outils.

Les styles suivants affectent l’aspect "3D" des boutons de la barre d’outils et le placement du texte du bouton :

- **TBSTYLE_FLAT** Crée une barre d’outils plate où la barre d’outils et les boutons sont transparents. Le texte du bouton apparaît sous bitmaps bouton. Lorsque ce style est utilisé, le bouton sous le curseur est automatiquement mis en surbrillance.

- **TBSTYLE_TRANSPARENT** Crée une barre d’outils transparente. Dans une barre d’outils transparente, la barre d’outils est transparente, mais les boutons ne le sont pas. Le texte du bouton apparaît sous bitmaps bouton.

- **TBSTYLE_LIST** Place le texte du bouton à droite des bitmaps bouton.

> [!NOTE]
> Pour éviter les problèmes de repeindre, les styles **TBSTYLE_FLAT** et **TBSTYLE_TRANSPARENT** doivent être réglés avant que l’objet de la barre d’outils soit visible.

Les styles suivants déterminent si la barre d’outils permet à un utilisateur de repositionner les boutons individuels dans un objet de barre d’outils à l’aide de la traînée et de la chute :

- **TBSTYLE_ALTDRAG** Permet aux utilisateurs de changer la position d’un bouton de barre d’outils en la faisant glisser tout en maintenant ALT. Si ce style n’est pas spécifié, l’utilisateur doit retenir SHIFT tout en faisant glisser un bouton.

    > [!NOTE]
    >  Le style **CCS_ADJUSTABLE** doit être spécifié pour permettre de traînéer les boutons de la barre d’outils.

- **TBSTYLE_REGISTERDROP** Génère **des** messages de notification TBN_GETOBJECT pour demander largage d’objets cibles lorsque le pointeur de la souris passe sur les boutons de la barre d’outils.

Les styles restants affectent les aspects visuels et non visuels de l’objet de la barre d’outils :

- **TBSTYLE_WRAPABLE** Crée une barre d’outils qui peut avoir plusieurs lignes de boutons. Les boutons de la barre d’outils peuvent « s’envelopper » jusqu’à la ligne suivante lorsque la barre d’outils devient trop étroite pour inclure tous les boutons sur la même ligne. L’emballage se produit sur les limites de séparation et de nongroupe.

- **TBSTYLE_CUSTOMERASE** Génère des messages de notification **NM_CUSTOMDRAW** lorsqu’il traite **WM_ERASEBKGND** messages.

- **TBSTYLE_TOOLTIPS** Crée un contrôle de pointe d’outil qu’une application peut utiliser pour afficher du texte descriptif pour les boutons de la barre d’outils.

Pour une liste complète des styles de barres d’outils et des styles étendus, voir [Toolbar Control et Button Styles](/windows/win32/Controls/toolbar-control-and-button-styles) et [Toolbar Extended Styles](/windows/win32/Controls/toolbar-extended-styles) dans le Windows SDK.

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
