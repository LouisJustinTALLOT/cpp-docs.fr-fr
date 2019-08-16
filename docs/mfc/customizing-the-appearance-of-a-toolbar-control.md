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
ms.openlocfilehash: 590f0dce6c50ee6d0ca30c4c68e21787563bd686
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508730"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>Personnalisation de l'apparence d'un contrôle ToolBar

La `CToolBarCtrl` classe fournit de nombreux styles qui affectent l’apparence (et parfois, le comportement) de l’objet Toolbar. Modifiez l’objet Toolbar en définissant `dwCtrlStyle` le paramètre de `CToolBarCtrl::Create` la fonction `CToolBar::CreateEx`membre (ou), lorsque vous créez le contrôle ToolBar pour la première fois.

Les styles suivants affectent l’aspect «3D» des boutons de la barre d’outils et le positionnement du texte du bouton:

- **TBSTYLE_FLAT** Crée une barre d’outils plate dans laquelle la barre d’outils et les boutons sont transparents. Le texte du bouton s’affiche sous bitmaps du bouton. Quand ce style est utilisé, le bouton situé sous le curseur est automatiquement mis en surbrillance.

- **TBSTYLE_TRANSPARENT** Crée une barre d’outils transparente. Dans une barre d’outils transparente, la barre d’outils est transparente, mais les boutons ne le sont pas. Le texte du bouton s’affiche sous bitmaps du bouton.

- **TBSTYLE_LIST** Place le texte du bouton à droite des bitmaps de bouton.

> [!NOTE]
>  Pour éviter les problèmes de redessin, les styles **TBSTYLE_FLAT** et **TBSTYLE_TRANSPARENT** doivent être définis avant que l’objet Toolbar soit visible.

Les styles suivants déterminent si la barre d’outils permet à un utilisateur de repositionner des boutons individuels dans un objet de barre d’outils à l’aide de la fonction glisser-déplacer:

- **TBSTYLE_ALTDRAG** Permet aux utilisateurs de modifier la position d’un bouton de barre d’outils en le faisant glisser tout en maintenant la touche ALT enfoncée. Si ce style n’est pas spécifié, l’utilisateur doit maintenir la touche Maj enfoncée tout en faisant glisser un bouton.

    > [!NOTE]
    >  Le style **CCS_ADJUSTABLE** doit être spécifié pour permettre le glissement des boutons de la barre d’outils.

- **TBSTYLE_REGISTERDROP** Génère des messages de notification **TBN_GETOBJECT** pour demander des objets cible de déplacement lorsque le pointeur de la souris passe sur les boutons de la barre d’outils.

Les autres styles affectent les aspects visuels et invisuels de l’objet Toolbar:

- **TBSTYLE_WRAPABLE** Crée une barre d’outils qui peut comporter plusieurs lignes de boutons. Les boutons de barre d’outils peuvent «habiller» à la ligne suivante quand la barre d’outils devient trop étroite pour inclure tous les boutons sur la même ligne. L’encapsulation se produit sur les limites de séparation et de non-groupe.

- **TBSTYLE_CUSTOMERASE** Génère des messages de notification **NM_CUSTOMDRAW** lors du traitement des messages **WM_ERASEBKGND** .

- **TBSTYLE_TOOLTIPS** Crée un contrôle d’info-bulle qu’une application peut utiliser pour afficher le texte descriptif des boutons dans la barre d’outils.

Pour obtenir la liste complète des styles de barre d’outils et des styles étendus, consultez styles de barre d’outils et styles de [bouton](/windows/win32/Controls/toolbar-control-and-button-styles) et styles étendus de [barre d’outils](/windows/win32/Controls/toolbar-extended-styles) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
