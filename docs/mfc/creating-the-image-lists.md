---
title: Création des listes d'images
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 844bfe71f7b03f299f57b0fd4558b7e9eacf67c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242235"
---
# <a name="creating-the-image-lists"></a>Création des listes d'images

Création de listes d’images est identique que vous utilisiez [CListView](../mfc/reference/clistview-class.md) ou [CListCtrl](../mfc/reference/clistctrl-class.md).

> [!NOTE]
>  Vous seulement devez listes d’images si votre contrôle de liste inclut le `LVS_ICON` style.

Utilisez la classe `CImageList` pour créer un ou plusieurs listes d’images (pour les icônes en taille réelle, les petites icônes et les États). Consultez [CImageList](../mfc/reference/cimagelist-class.md)et consultez [List View Image Lists](/windows/desktop/Controls/using-list-view-controls) dans le SDK Windows.

Appelez [CListCtrl::SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) pour chaque liste d’images ; passer un pointeur vers le texte approprié `CImageList` objet.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
