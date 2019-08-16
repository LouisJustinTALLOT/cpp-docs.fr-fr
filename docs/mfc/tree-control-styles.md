---
title: Styles de contrôle d’arborescence
ms.date: 11/04/2016
f1_keywords:
- TVS_SINGLEEXPAND
- TVS_LINESATROOT
- TVS_HASBUTTONS
- TVS_NOTOOLTIPS
- TVS_HASLINES
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
ms.openlocfilehash: f5f28025d0349e9bcd95aba50d4110d304fed376
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510938"
---
# <a name="tree-control-styles"></a>Styles de contrôle d’arborescence

Les styles de contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) régissent les aspects de l’apparence d’un contrôle d’arborescence. Vous définissez les styles initiaux lorsque vous créez le contrôle d’arborescence. Vous pouvez récupérer et modifier les styles après avoir créé le contrôle d’arborescence à l’aide des fonctions Windows [GetWindowLong](/windows/win32/api/winuser/nf-winuser-getwindowlongw) et [SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw) , en spécifiant **GWL_STYLE** pour le paramètre *nIndex* . Pour obtenir la liste complète des styles, consultez [styles de fenêtre de contrôle d’arborescence](/windows/win32/Controls/tree-view-control-window-styles) dans le SDK Windows.

Le style **TVS_HASLINES** améliore la représentation graphique d’une hiérarchie de contrôle d’arborescence en dessinant des lignes qui lient des éléments enfants à leur élément parent correspondant. Ce style ne lie pas les éléments à la racine de la hiérarchie. Pour ce faire, vous devez combiner les styles **TVS_HASLINES** et **TVS_LINESATROOT** .

L‘utilisateur peut développer ou réduire la liste des éléments enfants d‘un élément parent en double-cliquant sur l‘élément parent. Un contrôle d’arborescence qui a le style **TVS_SINGLEEXPAND** provoque le développement de l’élément sélectionné et l’élément désélectionné pour être réduit. Si vous utilisez la souris pour cliquer une fois sur l’élément sélectionné et que cet élément est fermé, il sera développé. Si vous cliquez une fois sur l‘élément sélectionné quand il est ouvert, il sera réduit.

Un contrôle d’arborescence qui a le style **TVS_HASBUTTONS** ajoute un bouton à gauche de chaque élément parent. L'utilisateur peut cliquer sur le bouton pour développer ou réduire les éléments enfants au lieu de double-cliquer sur l'élément parent. **TVS_HASBUTTONS** n’ajoute pas de boutons aux éléments situés à la racine de la hiérarchie. Pour ce faire, vous devez combiner **TVS_HASLINES**, **TVS_LINESATROOT**et **TVS_HASBUTTONS**.

Le style **TVS_EDITLABELS** permet à l’utilisateur de modifier les étiquettes des éléments de contrôle d’arborescence. Pour plus d’informations sur la modification des étiquettes, consultez Modification des étiquettes de [contrôle d’arborescence](../mfc/tree-control-label-editing.md) plus loin dans cette rubrique.

Le style **TVS_NOTOOLTIPS** désactive la fonctionnalité d’info-bulle automatique des contrôles d’arborescence. Cette fonctionnalité affiche automatiquement une info-bulle, qui contient le titre de l’élément sous le curseur de la souris, si le titre entier n’est pas actuellement visible.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
