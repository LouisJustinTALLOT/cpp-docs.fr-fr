---
title: Utilisation de listes d'images avec des contrôles Header
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
ms.openlocfilehash: 8002c16d1cdf5e0683b642001409b6da9c260660
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366472"
---
# <a name="using-image-lists-with-header-controls"></a>Utilisation de listes d'images avec des contrôles Header

Les éléments d’en-tête ont la possibilité d’afficher une image à l’intérieur d’un élément d’en-tête. Cette image, stockée dans une liste d’images associée, est de 16 x 16 pixels et a les mêmes caractéristiques que les images d’icône utilisées dans un contrôle de vue de liste. Afin d’implémenter ce comportement avec succès, vous devez d’abord créer et initialiser la liste d’images, associer la liste avec le contrôle de l’en-tête, puis modifier les attributs de l’élément d’en-tête qui affichera l’image.

La procédure suivante illustre les détails, à l’aide d’un pointeur à un contrôle de la tête (`m_pHdrCtrl`) et un pointeur à une liste d’images (`m_pHdrImages`).

### <a name="to-display-an-image-in-a-header-item"></a>Pour afficher une image dans un élément d’en-tête

1. Construire une nouvelle liste d’images (ou utiliser un objet existant de liste d’images) à l’aide du constructeur [CImageList,](../mfc/reference/cimagelist-class.md) en stockant le pointeur résultant.

1. Initialiser le nouvel objet de liste d’images en appelant [CImageList::Créer](../mfc/reference/cimagelist-class.md#create). Le code suivant est un exemple de cet appel.

   [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]

1. Ajoutez les images pour chaque élément d’en-tête. Le code suivant ajoute deux images prédéfinies.

   [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]

1. Associez la liste d’images au contrôle de l’en-tête avec un appel à [CHeaderCtrl::SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist).

1. Modifier l’élément d’en-tête pour afficher une image à partir de la liste d’images associée. L’exemple suivant attribue la `m_phdrImages`première image, de `m_pHdrCtrl`, à la première en-tête, .

   [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]

Pour obtenir des informations détaillées sur les valeurs de paramètres utilisées, consultez le [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)pertinent .

> [!NOTE]
> Il est possible d’avoir plusieurs contrôles à l’aide de la même liste d’images. Par exemple, dans un contrôle de vue de liste standard, il pourrait y avoir une liste d’images (de 16 x 16 pixels d’images) utilisée à la fois par la petite vue d’icône d’un contrôle de vue de liste et les éléments d’en-tête du contrôle de vue de liste.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)
