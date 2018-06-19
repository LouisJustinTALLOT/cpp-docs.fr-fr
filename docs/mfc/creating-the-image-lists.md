---
title: Création de listes d’images | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e5f5ac8396c32e56e4c0f2f951f45bb33714822
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341523"
---
# <a name="creating-the-image-lists"></a>Création des listes d'images
Création de listes d’images est le même que vous utilisiez [CListView](../mfc/reference/clistview-class.md) ou [CListCtrl](../mfc/reference/clistctrl-class.md).  
  
> [!NOTE]
>  Vous seulement devez listes d’images si votre contrôle de liste comprend le `LVS_ICON` style.  
  
 Utilisez la classe `CImageList` pour créer un ou plusieurs listes d’images (pour les grandes icônes, les petites icônes et les États). Consultez [CImageList](../mfc/reference/cimagelist-class.md)et consultez [liste de listes d’images d’affichage](http://msdn.microsoft.com/library/windows/desktop/bb774736) dans le Kit de développement logiciel Windows.  
  
 Appelez [CListCtrl::SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) pour chaque liste d’images ; passer un pointeur vers le `CImageList` objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CListCtrl](../mfc/using-clistctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

