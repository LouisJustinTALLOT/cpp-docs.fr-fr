---
description: 'En savoir plus sur : utilisation de listes d’images avec des contrôles Header'
title: Utilisation de listes d'images avec des contrôles Header
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
ms.openlocfilehash: 549f54c9fae7e0e0a63c726f4b75d2adeb38eef8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322729"
---
# <a name="using-image-lists-with-header-controls"></a>Utilisation de listes d'images avec des contrôles Header

Les éléments d’en-tête ont la capacité d’afficher une image dans un élément d’en-tête. Cette image, stockée dans une liste d’images associée, est de 16 x 16 pixels et a les mêmes caractéristiques que les images d’icône utilisées dans un contrôle List View. Pour pouvoir implémenter ce comportement avec succès, vous devez d’abord créer et initialiser la liste d’images, associer la liste au contrôle header, puis modifier les attributs de l’élément d’en-tête qui affichera l’image.

La procédure suivante illustre les détails, à l’aide d’un pointeur vers un contrôle header ( `m_pHdrCtrl` ) et d’un pointeur vers une liste d’images ( `m_pHdrImages` ).

### <a name="to-display-an-image-in-a-header-item"></a>Pour afficher une image dans un élément d’en-tête

1. Construisez une nouvelle liste d’images (ou utilisez un objet de liste d’images existant) à l’aide du constructeur [CImageList](../mfc/reference/cimagelist-class.md) , en stockant le pointeur résultant.

1. Initialisez le nouvel objet de liste d’images en appelant [CImageList :: Create](../mfc/reference/cimagelist-class.md#create). Le code suivant est un exemple de cet appel.

   [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]

1. Ajoutez les images pour chaque élément d’en-tête. Le code suivant ajoute deux images prédéfinies.

   [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]

1. Associez la liste d’images au contrôle header avec un appel à [CHeaderCtrl :: SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist).

1. Modifiez l’élément d’en-tête pour afficher une image à partir de la liste d’images associée. L’exemple suivant affecte la première image, du `m_phdrImages` , au premier élément d’en-tête, `m_pHdrCtrl` .

   [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]

Pour plus d’informations sur les valeurs de paramètre utilisées, consultez le [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)pertinent.

> [!NOTE]
> Il est possible d’avoir plusieurs contrôles utilisant la même liste d’images. Par exemple, dans un contrôle List View standard, il peut y avoir une liste d’images (d’images de 16 x 16 pixels) qui est utilisée par la petite vue icône d’un contrôle List View et les éléments d’en-tête du contrôle List View.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)
