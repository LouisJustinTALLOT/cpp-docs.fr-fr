---
title: Vue d'ensemble des états d'élément de contrôle d'arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- states, CTreeCtrl items
- tree controls [MFC], item states overview
- CTreeCtrl class [MFC], item states
ms.assetid: 2db11ae0-0d87-499d-8c1f-5e0dbe9e94c8
ms.openlocfilehash: bbeabf69f174fcf172808ff71f07ed05f1dc9675
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511037"
---
# <a name="tree-control-item-states-overview"></a>Vue d'ensemble des états d'élément de contrôle d'arborescence

Chaque élément d’un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) a un état actuel. Par exemple, un élément peut être sélectionné, desactivé, développé, etc. Dans la plupart des cas, l'arborescence définit automatiquement l'état d'un élément de sorte à refléter toutes les actions de l'utilisateur, comme la sélection d'un élément. Toutefois, vous pouvez également définir l’état d’un élément à l’aide de la fonction membre [SetItemState](../mfc/reference/ctreectrl-class.md#setitemstate) et récupérer l’état actuel d’un élément à l’aide de la fonction membre [GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate) . Pour obtenir la liste complète des États des éléments, consultez constantes de [contrôle d’arborescence](/windows/win32/Controls/tree-view-control-item-states) dans le SDK Windows.

L’état actuel d’un élément est spécifié par le paramètre *nState* . Un contrôle d'arborescence peut modifier l'état d'un élément de sorte à refléter une action d'utilisateur, telle que sélectionner l'élément ou définir le focus sur l'élément. En outre, une application peut modifier l'état d'un élément pour désactiver ou masquer l'élément ou pour spécifier une image de superposition ou d'état.

Lorsque vous spécifiez ou modifiez l’état d’un élément, le paramètre *nStateMask* spécifie les bits d’État à définir, et le paramètre *nState* contient les nouvelles valeurs pour ces bits. Par exemple, l’exemple suivant modifie l’état actuel d’un élément parent (spécifié par *hParentItem*) dans un `CTreeCtrl` `TVIS_EXPANDPARTIAL`objet (`m_treeCtrl`) en:

[!code-cpp[NVC_MFCControlLadenDialog#71](../mfc/codesnippet/cpp/tree-control-item-states-overview_1.cpp)]

Un autre exemple de modification d'état consisterait à définir l'image de superposition d'un élément. Pour ce faire, *nStateMask* doit inclure la `TVIS_OVERLAYMASK` valeur et *nState* doit inclure l’index de base un de l’image de superposition décalée vers la gauche de huit bits à l’aide de la macro [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask) . L'index peut correspondre à 0 pour spécifier qu'il n'y a aucune image de superposition. L’image de superposition doit avoir été ajoutée à la liste des images de superposition du contrôle d’arborescence par un appel précédent à la fonction [CImageList:: SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) . La fonction spécifie l’index de base un de l’image à ajouter; Il s’agit de l’index utilisé avec la macro INDEXTOOVERLAYMASK. Un contrôle d’arborescence peut contenir jusqu’à quatre images de superposition.

Pour définir l’image d’état d’un élément, *nStateMask* doit `TVIS_STATEIMAGEMASK` inclure la valeur et *nState* doit inclure l’index de base un de l’image d’État déplacée à gauche de 12 bits à l’aide de la macro [INDEXTOSTATEIMAGEMASK](/windows/win32/api/commctrl/nf-commctrl-indextostateimagemask) . L'index peut correspondre à 0 pour spécifier qu'il n'y a aucune image d'état. Pour plus d’informations sur les images de superposition et d’État, consultez [listes d’images de contrôle d’arborescence](../mfc/tree-control-image-lists.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
