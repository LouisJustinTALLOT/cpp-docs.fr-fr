---
title: Utilisation de listes d'images avec des contrôles Header
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
ms.openlocfilehash: 3d9a4a0c655fa46c15d8c4d9b2b4e90cd34c2937
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411537"
---
# <a name="using-image-lists-with-header-controls"></a>Utilisation de listes d'images avec des contrôles Header

Éléments d’en-tête ont la possibilité d’afficher une image dans un élément d’en-tête. Cette image, stockée dans une liste d’images associées, est de 16 x 16 pixels et a les mêmes caractéristiques que les images d’icône utilisés dans un contrôle list view. Pour implémenter ce comportement avec succès, vous devez tout d’abord créer et initialiser la liste d’images, associez la liste de contrôle header et puis modifier les attributs de l’élément d’en-tête qui affiche l’image.

La procédure suivante illustre les détails, à l’aide d’un pointeur vers un contrôle header (`m_pHdrCtrl`) et un pointeur vers une liste d’images (`m_pHdrImages`).

### <a name="to-display-an-image-in-a-header-item"></a>Pour afficher une image dans un élément d’en-tête

1. Construire une liste d’images (ou utilisez un objet de liste d’images existant) à l’aide de la [CImageList](../mfc/reference/cimagelist-class.md) constructeur, en stockant le pointeur résultant.

1. Initialiser le nouvel objet de liste d’images en appelant [CImageList::Create](../mfc/reference/cimagelist-class.md#create). Le code suivant est un exemple de cet appel.

   [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]

1. Ajouter les images pour chaque élément d’en-tête. Le code suivant ajoute deux images prédéfinies.

   [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]

1. Associer la liste d’images avec le contrôle d’en-tête avec un appel à [CHeaderCtrl::SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist).

1. Modifier l’élément d’en-tête pour afficher une image à partir de la liste d’images associée. L’exemple suivant assigne la première image à partir de `m_phdrImages`, pour le premier élément d’en-tête, `m_pHdrCtrl`.

   [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]

Pour plus d’informations sur les valeurs de paramètre utilisées, consultez les informations pertinentes [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md).

> [!NOTE]
>  Il est possible d’avoir plusieurs contrôles à l’aide de la même liste d’images. Par exemple, dans un contrôle list view standard, il peut être une liste d’images (des images de 16 x 16 pixels) utilisée par la vue petite icône d’un contrôle list view et les éléments du contrôle list view.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)
