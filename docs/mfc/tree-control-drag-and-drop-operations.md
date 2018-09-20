---
title: Opérations de glisser-déplacer de contrôle d’arborescence | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b53196ded40bffd0a74f91df5ac938fc1616efa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446593"
---
# <a name="tree-control-drag-and-drop-operations"></a>Opérations de glisser-déplacer pour le contrôle d’arborescence

Un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) envoie une notification lorsque l’utilisateur commence à faire glisser un élément. Le contrôle envoie un [TVN_BEGINDRAG](/windows/desktop/Controls/tvn-begindrag) message de notification lorsque l’utilisateur commence à faire glisser un élément avec le bouton gauche de la souris et un [TVN_BEGINRDRAG](/windows/desktop/Controls/tvn-beginrdrag) message de notification lorsque l’utilisateur commence à faire glisser avec le bouton droit. Vous pouvez empêcher un contrôle d’arborescence d’envoyer des notifications en donnant le contrôle d’arborescence le style TVS_DISABLEDRAGDROP.

Vous obtenez une image à afficher pendant une opération glisser en appelant le [CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage) fonction membre. L’arborescence crée une image bitmap de glissement basée sur le nom de l’élément déplacé. Ensuite, le contrôle d’arborescence crée une liste d’images, lui ajoute l’image bitmap et retourne un pointeur vers le [CImageList](../mfc/reference/cimagelist-class.md) objet.

Vous devez fournir du code faisant glisser réellement l'élément. Cela implique généralement en utilisant les fonctions de déplacement des fonctions de liste d’image et de traitement le [WM_MOUSEMOVE](/windows/desktop/inputdev/wm-mousemove) et [WM_LBUTTONUP](/windows/desktop/inputdev/wm-lbuttonup) (ou [WM_RBUTTONUP](/windows/desktop/inputdev/wm-rbuttonup)) messages envoyés après que l’opération glisser a commencé. Pour plus d’informations sur les fonctions de liste d’images, consultez [CImageList](../mfc/reference/cimagelist-class.md) dans le *référence MFC* et [listes d’images](https://msdn.microsoft.com/library/windows/desktop/bb761389) dans le SDK Windows. Pour plus d’informations sur le déplacement d’un élément de contrôle d’arborescence, consultez [en faisant glisser l’élément d’arborescence](/windows/desktop/Controls/tree-view-controls), également dans le Kit de développement Windows.

Si les éléments d’un contrôle d’arborescence vont être des cibles d’opérations de type Glisser-déplacer, vous devez savoir quand le curseur de la souris est sur un élément cible. Vous trouverez en appelant le [HitTest](../mfc/reference/ctreectrl-class.md#hittest) fonction membre. Vous spécifiez un point et entier ou l’adresse d’un [TVHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtvhittestinfo) structure qui contient les coordonnées actuelles du curseur de la souris. Après le retour de la fonction, l’entier ou la structure contient un indicateur qui fournit l’emplacement du curseur de la souris par rapport au contrôle d’arborescence. Si le curseur est sur un élément de l’arborescence, la structure contiendra également le handle de l’élément.

Vous pouvez indiquer qu’un élément est la cible d’une opération de glisser-déplacer en appelant le [SetItem](../mfc/reference/ctreectrl-class.md#setitem) fonction membre à définir l’état sur le `TVIS_DROPHILITED` valeur. Un élément avec cet état est dessiné dans le style utilisé pour indiquer une cible de glissement-dépôt.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

