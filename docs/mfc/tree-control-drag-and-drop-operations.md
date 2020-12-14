---
description: 'En savoir plus sur : opérations de glisser-déplacer pour le contrôle d’arborescence'
title: Opérations de glisser-déposer pour le contrôle d’arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
ms.openlocfilehash: 000255ad4aa6801cbe27676603a3f42d0abbef30
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264178"
---
# <a name="tree-control-drag-and-drop-operations"></a>Opérations de glisser-déposer pour le contrôle d’arborescence

Un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) envoie une notification lorsque l’utilisateur commence à faire glisser un élément. Le contrôle envoie un message de notification [TVN_BEGINDRAG](/windows/win32/Controls/tvn-begindrag) lorsque l’utilisateur commence à faire glisser un élément avec le bouton gauche de la souris et un message de notification [TVN_BEGINRDRAG](/windows/win32/Controls/tvn-beginrdrag) lorsque l’utilisateur commence à faire glisser le bouton droit. Vous pouvez empêcher un contrôle d’arborescence d’envoyer des notifications en lui attribuant le style TVS_DISABLEDRAGDROP.

Vous obtenez une image à afficher pendant une opération glisser en appelant la fonction membre [CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage) . L’arborescence crée une image bitmap de glissement basée sur le nom de l’élément déplacé. Ensuite, le contrôle d’arborescence crée une liste d’images, y ajoute le bitmap et retourne un pointeur vers l’objet [CImageList](../mfc/reference/cimagelist-class.md) .

Vous devez fournir du code faisant glisser réellement l'élément. Cela implique généralement l’utilisation des fonctionnalités de glissement des fonctions de liste d’images et le traitement des messages [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) et [WM_LBUTTONUP](/windows/win32/inputdev/wm-lbuttonup) (ou [WM_RBUTTONUP](/windows/win32/inputdev/wm-rbuttonup)) envoyés après le début de l’opération glisser. Pour plus d’informations sur les fonctions de liste d’images, consultez [CImageList](../mfc/reference/cimagelist-class.md) dans les [listes](/windows/win32/controls/image-lists) de référence et d’image *MFC* dans la SDK Windows. Pour plus d’informations sur le glissement d’un élément de contrôle d’arborescence, consultez [la rubrique déplacement de l’élément d’arborescence](/windows/win32/Controls/tree-view-controls), également dans la SDK Windows.

Si les éléments d’un contrôle d’arborescence vont être des cibles d’opérations de type Glisser-déposer, vous devez savoir quand le curseur de la souris est sur un élément cible. Vous pouvez le trouver en appelant la fonction membre [HitTest](../mfc/reference/ctreectrl-class.md#hittest) . Vous spécifiez un point et un entier, ou l’adresse d’une structure [TVHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-tvhittestinfo) qui contient les coordonnées actuelles du curseur de la souris. Après le retour de la fonction, l’entier ou la structure contient un indicateur qui fournit l’emplacement du curseur de la souris par rapport au contrôle d’arborescence. Si le curseur est sur un élément de l’arborescence, la structure contiendra également le handle de l’élément.

Vous pouvez indiquer qu’un élément est la cible d’une opération de glisser-déplacer en appelant la fonction membre [SetItem](../mfc/reference/ctreectrl-class.md#setitem) pour définir l’État sur la `TVIS_DROPHILITED` valeur. Un élément avec cet état est dessiné dans le style utilisé pour indiquer une cible de glissement-déplacement.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
