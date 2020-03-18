---
title: Utilisation de CImageList
ms.date: 11/04/2016
helpviewer_keywords:
- image list control
- CImageList class [MFC], using
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
ms.openlocfilehash: 09fd0e95ce2981afbebbfe10d87b26f88a7b5e13
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447227"
---
# <a name="using-cimagelist"></a>Utilisation de CImageList

Une liste d’images, représentée par la classe [CImageList](../mfc/reference/cimagelist-class.md), est une collection d’images de même taille, dont chacune peut être référencée par son index. Les listes d’images permettent de gérer efficacement de grands ensembles d’icônes ou de bitmaps. Les listes d’images ne sont pas elles-mêmes des contrôles dans la mesure où elles ne sont pas Windows. Toutefois, ils sont utilisés avec plusieurs types différents de contrôles, notamment les contrôles de liste ([CListCtrl](../mfc/reference/clistctrl-class.md)), les contrôles d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) et les contrôles d’onglet ([CTabCtrl](../mfc/reference/ctabctrl-class.md)).

Toutes les images d’une liste d’images sont contenues dans une seule bitmap de grande largeur au format de l’appareil d’écran. Une liste d’images peut également inclure une bitmap monochrome qui contient des masques utilisés pour dessiner des images en toute transparence (style d’icône). `CImageList` fournit des fonctions membres qui vous permettent de dessiner des images, de créer et de détruire des listes d’images, d’ajouter et de supprimer des images, de remplacer des images, de fusionner des images et de faire glisser des images.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Types de listes d’images](../mfc/types-of-image-lists.md)

- [Utilisation d’une liste d’images](../mfc/using-an-image-list.md)

- [Manipulation de listes d’images](../mfc/manipulating-image-lists.md)

- [Dessin d’images à partir d’une liste d’images](../mfc/drawing-images-from-an-image-list.md)

- [Superpositions d’images dans les listes d’images](../mfc/image-overlays-in-image-lists.md)

- [Faire glisser des images à partir d’une liste d’images](../mfc/dragging-images-from-an-image-list.md)

- [Informations relatives aux images dans les listes d’images](../mfc/image-information-in-image-lists.md)

## <a name="see-also"></a>Voir aussi

[Contrôles](../mfc/controls-mfc.md)
