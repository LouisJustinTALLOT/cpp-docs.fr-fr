---
title: Styles de contrôle d’arborescence | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TVS_SINGLEEXPAND
- TVS_LINESATROOT
- TVS_HASBUTTONS
- TVS_NOTOOLTIPS
- TVS_HASLINES
dev_langs:
- C++
helpviewer_keywords:
- TVS_LINESATROOT [MFC]
- styles [MFC], CTreeCtrl
- styles [MFC], tree control
- TVS_HASLINES
- TVS_SINGLEEXPAND
- CTreeCtrl class [MFC], styles
- TVS_EDITLABELS [MFC]
- TVS_NOTOOLTIPS [MFC]
- TVS_HASBUTTONS [MFC]
- tree controls [MFC], styles
ms.assetid: f43faebd-a355-479e-888a-bf0673d5e1b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef7c24fb321594c64afe45e1902676f43afd3e9b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412665"
---
# <a name="tree-control-styles"></a>Styles de contrôle d’arborescence

Contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) styles régissent les aspects de l’apparence d’un contrôle d’arborescence. Vous définissez les styles initiaux lorsque vous créez le contrôle d’arborescence. Vous pouvez extraire et modifier les styles après avoir créé le contrôle d’arborescence à l’aide de la [GetWindowLong](/windows/desktop/api/winuser/nf-winuser-getwindowlonga) et [SetWindowLong](/windows/desktop/api/winuser/nf-winuser-setwindowlonga) des fonctions de Windows, en spécifiant **GWL_STYLE** pour le *nIndex* paramètre. Pour obtenir une liste complète des styles, consultez [Styles de fenêtre du contrôle arborescence vue](/windows/desktop/Controls/tree-view-control-window-styles) dans le SDK Windows.

Le **TVS_HASLINES** style améliore la représentation graphique de la hiérarchie d’un contrôle d’arborescence en traçant des lignes qui lient les éléments enfants à l’élément parent correspondant. Ce style ne lie pas les éléments à la racine de la hiérarchie. Pour ce faire, vous devez combiner les **TVS_HASLINES** et **TVS_LINESATROOT** styles.

L’utilisateur peut développer ou réduire la liste des éléments enfants d’un élément parent en double-cliquant sur l’élément parent. Un contrôle d’arborescence qui a le **TVS_SINGLEEXPAND** style provoque l’élément sélectionné pour développer et l’élément en cours non sélectionné. Si vous utilisez la souris pour cliquer une fois sur l’élément sélectionné et que cet élément est fermé, il sera développé. Si vous cliquez une fois sur l‘élément sélectionné quand il est ouvert, il sera réduit.

Un contrôle d’arborescence qui a le **TVS_HASBUTTONS** style ajoute un bouton à gauche de chaque élément parent. L’utilisateur peut cliquer sur le bouton pour développer ou réduire les éléments enfants au lieu de double-cliquer sur l’élément parent. **TVS_HASBUTTONS** n’ajoute pas de boutons aux éléments à la racine de la hiérarchie. Pour ce faire, vous devez combiner **TVS_HASLINES**, **TVS_LINESATROOT**, et **TVS_HASBUTTONS**.

Le **TVS_EDITLABELS** style permet à l’utilisateur de modifier les étiquettes des éléments de contrôle d’arborescence. Pour plus d’informations sur la modification des étiquettes, consultez [modification d’arborescence de contrôle étiquette](../mfc/tree-control-label-editing.md) plus loin dans cette rubrique.

Le **TVS_NOTOOLTIPS** style désactive la fonctionnalité d’info-bulle automatique des outils de contrôles d’arborescence. Cette fonctionnalité affiche automatiquement une info-bulle, qui contient le titre de l’élément sous le curseur de la souris, si le titre entier n’est pas actuellement visible.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

