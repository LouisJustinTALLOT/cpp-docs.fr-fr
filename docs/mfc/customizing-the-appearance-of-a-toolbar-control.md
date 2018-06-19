---
title: Personnalisation de l’apparence d’un contrôle de barre d’outils | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TBSTYLE_
dev_langs:
- C++
helpviewer_keywords:
- flat toolbars
- CToolBar class [MFC], styles
- transparent toolbars
- TBSTYLE_ styles [MFC]
- CToolBarCtrl class [MFC], object styles
- toolbar controls [MFC], style
ms.assetid: fd0a73db-7ad1-4fe4-889b-02c3980f49e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 96ec459e1c956c805991f2e37d22b8260f0ffdf2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343692"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>Personnalisation de l'apparence d'un contrôle ToolBar
Classe `CToolBarCtrl` propose de nombreux styles qui affectent l’apparence (et, parfois, le comportement) de l’objet de barre d’outils. Modifier l’objet de barre d’outils en définissant le `dwCtrlStyle` paramètre de la `CToolBarCtrl::Create` (ou `CToolBar::CreateEx`) fonction membre, lorsque vous créez le contrôle de barre d’outils.  
  
 Les styles suivants affectent l’aspect « 3D » des boutons de barre d’outils et le positionnement du texte du bouton :  
  
-   **TBSTYLE_FLAT** crée une barre d’outils plate où la barre d’outils et les boutons sont transparents. Texte du bouton s’affiche sous les bitmaps des boutons. Lorsque ce style est utilisé, le bouton situé sous le curseur est automatiquement mis en surbrillance.  
  
-   **TBSTYLE_TRANSPARENT** crée une barre d’outils transparente. Dans une barre d’outils transparente, la barre d’outils est transparente, mais les boutons ne sont pas. Texte du bouton s’affiche sous les bitmaps des boutons.  
  
-   **TBSTYLE_LIST** emplacements bouton à droite de bitmaps des boutons de texte.  
  
> [!NOTE]
>  Pour éviter les problèmes de mise à jour, le **TBSTYLE_FLAT** et **TBSTYLE_TRANSPARENT** styles doivent être définis avant que l’objet de barre d’outils est visible.  
  
 Les styles suivants déterminent si la barre d’outils permet à un utilisateur repositionner des boutons individuels au sein d’un objet de barre d’outils à l’aide de glisser-déplacer :  
  
-   **TBSTYLE_ALTDRAG** permet aux utilisateurs de modifier la position d’un bouton de barre d’outils en le faisant glisser tout en maintenant la touche ALT ENFONCÉE. Si ce style n’est pas spécifié, l’utilisateur doit maintenir la touche MAJ ENFONCÉE tout en faisant glisser un bouton.  
  
    > [!NOTE]
    >  Le `CCS_ADJUSTABLE` style doit être spécifié pour activer les boutons de barre d’outils pour la faire glisser.  
  
-   **TBSTYLE_REGISTERDROP** génère **TBN_GETOBJECT** notification messages de demande de supprimer les objets cible lorsque le pointeur de la souris passe au-dessus des boutons de barre d’outils.  
  
 Les autres styles affectent les aspects visuels et de l’objet de barre d’outils :  
  
-   `TBSTYLE_WRAPABLE` Crée une barre d’outils qui peut avoir plusieurs lignes de boutons. Boutons de barre d’outils peut « encapsuler » à la ligne suivante lorsque la barre d’outils devienne trop étroite pour inclure tous les boutons sur la même ligne. Retour à la ligne se produit sur des séparateurs et.  
  
-   **TBSTYLE_CUSTOMERASE** génère **NM_CUSTOMDRAW** lorsqu’il traite les messages de notification `WM_ERASEBKGND` messages.  
  
-   `TBSTYLE_TOOLTIPS` Crée un contrôle d’info-bulle qu’une application peut utiliser pour afficher un texte descriptif pour les boutons dans la barre d’outils.  
  
 Pour obtenir une liste complète des styles de barre d’outils et des styles étendus, consultez [contrôle de barre d’outils et les Styles de bouton](http://msdn.microsoft.com/library/windows/desktop/bb760439) et [Styles étendus de barre d’outils](http://msdn.microsoft.com/library/windows/desktop/bb760430) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

