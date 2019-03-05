---
title: Manipulation de listes d'images
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], manipulating
- lists [MFC], image
- CImageList class [MFC], manipulating
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
ms.openlocfilehash: 1e86961980c91ade47a3d6510dec5c04ac36cffb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304845"
---
# <a name="manipulating-image-lists"></a>Manipulation de listes d'images

Le [remplacer](../mfc/reference/cimagelist-class.md#replace) fonction membre remplace une image dans une liste d’images ([CImageList](../mfc/reference/cimagelist-class.md)) avec une nouvelle image. Cette fonction est également utile si vous avez besoin d’augmenter dynamiquement le nombre d’images dans un objet de liste d’images. Le [fonction SetImageCount](../mfc/reference/cimagelist-class.md#setimagecount) fonction modifie de manière dynamique le nombre d’images stockées dans la liste d’images. Si vous augmentez la taille de la liste d’images, appelez `Replace` pour ajouter des images pour les nouveaux emplacements. Si vous diminuez la taille de la liste d’images, les images au-delà de la nouvelle taille sont libérées.

Le [supprimer](../mfc/reference/cimagelist-class.md#remove) fonction membre supprime une image à partir d’une liste d’images. Le [copie](../mfc/reference/cimagelist-class.md#copy) fonction membre peut copier ou permuter des images dans une liste d’images. Cette fonction vous permet d’indiquer si l’image source doit être copié à l’index de destination ou les images de la source et de destination doivent être échangées.

Pour créer une liste d’images en fusionnant deux listes d’images, utilisez la surcharge appropriée de la [créer](../mfc/reference/cimagelist-class.md#create) fonction membre. Cette surcharge de `Create` fusions répertorie de la première image de l’image existante, stockage de l’image résultante dans un nouvel objet de liste d’images. La nouvelle image est créée en dessinant la deuxième image en toute transparence sur la première. Le masque pour la nouvelle image est le résultat d’une opération OR logique sur les bits des masques pour les deux images existantes.

Cette opération est répétée jusqu'à ce que toutes les images sont fusionnées et ajoutées au nouvel objet de liste d’images.

Vous pouvez écrire les informations d’image dans une archive en appelant le [écrire](../mfc/reference/cimagelist-class.md#write) fonction membre, puis les lire en appelant le [en lecture](../mfc/reference/cimagelist-class.md#read) fonction membre.

Le [fonctions membres GetSafeHandle](../mfc/reference/cimagelist-class.md#getsafehandle), [Attach](../mfc/reference/cimagelist-class.md#attach), et [détachement](../mfc/reference/cimagelist-class.md#detach) les fonctions de membre permettent de manipuler le handle de la liste d’images attachée à la `CImageList` objet, tandis que le [DeleteImageList](../mfc/reference/cimagelist-class.md#deleteimagelist) fonction membre supprime de la liste d’images sans détruire la `CImageList` objet.

## <a name="see-also"></a>Voir aussi

[Utilisation de CImageList](../mfc/using-cimagelist.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
