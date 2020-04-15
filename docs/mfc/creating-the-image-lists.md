---
title: Création des listes d'images
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 440ab6fdfe7663557f6c6a6607e617c793d26674
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371577"
---
# <a name="creating-the-image-lists"></a>Création des listes d'images

La création de listes d’images est la même que vous utilisiez [CListView](../mfc/reference/clistview-class.md) ou [CListCtrl](../mfc/reference/clistctrl-class.md).

> [!NOTE]
> Vous n’avez besoin que de `LVS_ICON` listes d’images si votre contrôle de liste inclut le style.

Utilisez `CImageList` la classe pour créer une ou plusieurs listes d’images (pour les icônes pleine grandeur, les petites icônes et les états). Voir [CImageList](../mfc/reference/cimagelist-class.md), et voir [Liste Afficher les listes d’images](/windows/win32/Controls/using-list-view-controls) dans le SDK Windows.

Appelez [CListCtrl::SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) pour chaque liste d’images; passer un pointeur `CImageList` à l’objet approprié.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
