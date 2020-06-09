---
title: Création des listes d'images
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: bbba01a6a8e08ea53e164656733aa06e03dd87a7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625950"
---
# <a name="creating-the-image-lists"></a>Création des listes d'images

La création de listes d’images est identique que vous utilisiez [CListView](reference/clistview-class.md) ou [CListCtrl](reference/clistctrl-class.md).

> [!NOTE]
> Vous avez uniquement besoin de listes d’images si votre contrôle de liste comprend le `LVS_ICON` style.

Utilisez la classe `CImageList` pour créer une ou plusieurs listes d’images (pour les icônes en taille réelle, les petites icônes et les États). Consultez [CImageList](reference/cimagelist-class.md)et consultez [listes d’images en mode liste](/windows/win32/Controls/using-list-view-controls) dans le SDK Windows.

Appeler [CListCtrl :: SetImageList](reference/clistctrl-class.md#setimagelist) pour chaque liste d’images ; passer un pointeur vers l' `CImageList` objet approprié.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](using-clistctrl.md)<br/>
[Commandes](controls-mfc.md)
