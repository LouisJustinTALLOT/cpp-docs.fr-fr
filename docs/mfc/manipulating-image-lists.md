---
description: 'En savoir plus sur : manipulation des listes d’images'
title: Manipulation de listes d'images
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], manipulating
- lists [MFC], image
- CImageList class [MFC], manipulating
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
ms.openlocfilehash: dc2b136e1aed5266ea7cc910cf10839f59dfcf00
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281130"
---
# <a name="manipulating-image-lists"></a>Manipulation de listes d'images

La fonction membre [Replace](reference/cimagelist-class.md#replace) remplace une image dans une liste d’images ([CImageList](reference/cimagelist-class.md)) par une nouvelle image. Cette fonction est également utile si vous devez augmenter dynamiquement le nombre d’images dans un objet de liste d’images. La fonction [SetImageCount](reference/cimagelist-class.md#setimagecount) modifie dynamiquement le nombre d’images stockées dans la liste d’images. Si vous augmentez la taille de la liste d’images, appelez `Replace` pour ajouter des images aux nouveaux emplacements d’images. Si vous réduisez la taille de la liste d’images, les images situées au-delà de la nouvelle taille sont libérées.

La fonction membre [Remove](reference/cimagelist-class.md#remove) supprime une image d’une liste d’images. La fonction membre de [copie](reference/cimagelist-class.md#copy) peut copier ou échanger des images dans une liste d’images. Cette fonction vous permet d’indiquer si l’image source doit être copiée vers l’index de destination ou si les images source et de destination doivent être permutées.

Pour créer une nouvelle liste d’images en fusionnant deux listes d’images, utilisez la surcharge appropriée de la fonction membre [Create](reference/cimagelist-class.md#create) . Cette surcharge `Create` fusionne la première image des listes d’images existantes, en stockant l’image résultante dans un nouvel objet de liste d’images. La nouvelle image est créée en dessinant la deuxième image de manière transparente sur la première. Le masque de la nouvelle image résulte de l’exécution d’une opération OR logique sur les bits des masques pour les deux images existantes.

Cette opération est répétée jusqu’à ce que toutes les images soient fusionnées et ajoutées au nouvel objet de liste d’images.

Vous pouvez écrire les informations sur l’image dans une archive en appelant la fonction membre [Write](reference/cimagelist-class.md#write) , puis la relire en appelant la fonction membre [Read](reference/cimagelist-class.md#read) .

Les fonctions membres [GetSafeHandle](reference/cimagelist-class.md#getsafehandle), [Attach](reference/cimagelist-class.md#attach)et [Detach](reference/cimagelist-class.md#detach) vous permettent de manipuler le handle de la liste d’images jointe à l' `CImageList` objet, tandis que la fonction membre [DeleteImageList](reference/cimagelist-class.md#deleteimagelist) supprime la liste d’images sans détruire l' `CImageList` objet.

## <a name="see-also"></a>Voir aussi

[Utilisation de CImageList](using-cimagelist.md)<br/>
[Contrôles](controls-mfc.md)
