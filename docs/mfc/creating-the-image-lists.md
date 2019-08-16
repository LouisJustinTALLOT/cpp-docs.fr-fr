---
title: Création des listes d'images
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 6687b62b70103894d957a21019008e8781385feb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508782"
---
# <a name="creating-the-image-lists"></a>Création des listes d'images

La création de listes d’images est identique que vous utilisiez [CListView](../mfc/reference/clistview-class.md) ou [CListCtrl](../mfc/reference/clistctrl-class.md).

> [!NOTE]
>  Vous avez uniquement besoin de listes d’images si votre contrôle `LVS_ICON` de liste comprend le style.

Utilisez la `CImageList` classe pour créer une ou plusieurs listes d’images (pour les icônes en taille réelle, les petites icônes et les États). Consultez [CImageList](../mfc/reference/cimagelist-class.md)et consultez [listes d’images en mode liste](/windows/win32/Controls/using-list-view-controls) dans le SDK Windows.

Appeler [CListCtrl:: SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) pour chaque liste d’images; passer un pointeur vers l’objet `CImageList` approprié.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
