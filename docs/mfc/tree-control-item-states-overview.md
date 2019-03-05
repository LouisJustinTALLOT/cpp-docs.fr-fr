---
title: Vue d'ensemble des états d'élément de contrôle d'arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- states, CTreeCtrl items
- tree controls [MFC], item states overview
- CTreeCtrl class [MFC], item states
ms.assetid: 2db11ae0-0d87-499d-8c1f-5e0dbe9e94c8
ms.openlocfilehash: 57c6714073f4939ffb791a78454e9eac6342309b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264597"
---
# <a name="tree-control-item-states-overview"></a>Vue d'ensemble des états d'élément de contrôle d'arborescence

Chaque élément dans un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) a un état actuel. Par exemple, un élément peut être sélectionné, desactivé, développé, etc. Dans la plupart des cas, l'arborescence définit automatiquement l'état d'un élément de sorte à refléter toutes les actions de l'utilisateur, comme la sélection d'un élément. Toutefois, vous pouvez également définir état d’un élément à l’aide de la [SetItemState](../mfc/reference/ctreectrl-class.md#setitemstate) fonction membre et récupérer l’état actuel d’un élément à l’aide de la [GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate) fonction membre. Pour obtenir une liste complète des États des éléments, consultez [constantes de contrôle Tree-View](/windows/desktop/Controls/tree-view-control-item-states) dans le SDK Windows.

État actuel d’un élément est spécifié par le *nState* paramètre. Un contrôle d'arborescence peut modifier l'état d'un élément de sorte à refléter une action d'utilisateur, telle que sélectionner l'élément ou définir le focus sur l'élément. En outre, une application peut modifier l'état d'un élément pour désactiver ou masquer l'élément ou pour spécifier une image de superposition ou d'état.

Lorsque vous définissez ou modifiez l’état d’un élément, le *nStateMask* paramètre spécifie quel état les bits à définir et le *nState* paramètre contient les nouvelles valeurs pour ces bits. Par exemple, l’exemple suivant modifie l’état actuel d’un élément parent (spécifié par *hParentItem*) dans un `CTreeCtrl` objet (`m_treeCtrl`) à `TVIS_EXPANDPARTIAL`:

[!code-cpp[NVC_MFCControlLadenDialog#71](../mfc/codesnippet/cpp/tree-control-item-states-overview_1.cpp)]

Un autre exemple de modification d'état consisterait à définir l'image de superposition d'un élément. Pour ce faire, *nStateMask* doit inclure le `TVIS_OVERLAYMASK` valeur, et *nState* doit inclure l’index basé sur un de l’image de superposition décalée vers la gauche de huit bits en utilisant la [ INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask) macro. L'index peut correspondre à 0 pour spécifier qu'il n'y a aucune image de superposition. L’image de superposition doit avoir été ajouté à la liste de contrôle d’arborescence d’images de superposition par un appel précédent à la [CImageList::SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) (fonction). La fonction spécifie l’index de base un de l’image à ajouter ; Il s’agit de l’index utilisé avec la macro INDEXTOOVERLAYMASK. Un contrôle d’arborescence peut contenir jusqu’à quatre images de superposition.

Pour définir l’image d’état d’un élément, *nStateMask* doit inclure le `TVIS_STATEIMAGEMASK` valeur, et *nState* doit inclure l’index basé sur un de l’image d’état décalée vers la gauche de 12 bits à l’aide de la [ INDEXTOSTATEIMAGEMASK](/windows/desktop/api/commctrl/nf-commctrl-indextostateimagemask) (macro). L'index peut correspondre à 0 pour spécifier qu'il n'y a aucune image d'état. Pour plus d’informations sur les images de superposition et d’état, consultez [Image listes de contrôle d’arborescence](../mfc/tree-control-image-lists.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
