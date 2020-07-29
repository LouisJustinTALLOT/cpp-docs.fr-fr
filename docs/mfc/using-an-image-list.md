---
title: Utilisation d'une liste d'images
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: 710831ea8ef6b52292ba3e8eb84a69575c6c7508
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226826"
---
# <a name="using-an-image-list"></a>Utilisation d'une liste d'images

L’utilisation classique d’une liste d’images suit le modèle ci-dessous :

- Construisez un objet [CImageList](../mfc/reference/cimagelist-class.md) et appelez l’une des surcharges de sa fonction [Create](../mfc/reference/cimagelist-class.md#create) pour créer une liste d’images et l’attacher à l' `CImageList` objet.

- Si vous n’avez pas ajouté d’images lorsque vous avez créé la liste d’images, ajoutez des images à la liste d’images en appelant la fonction membre [Add](../mfc/reference/cimagelist-class.md#add) ou [Read](../mfc/reference/cimagelist-class.md#read) .

- Associez la liste d’images à un contrôle en appelant la fonction membre appropriée de ce contrôle, ou dessinez des images à partir de la liste d’images vous-même à l’aide de la fonction membre de [dessin](../mfc/reference/cimagelist-class.md#draw) de la liste d’images.

- Autorisez éventuellement l’utilisateur à faire glisser une image à l’aide de la prise en charge intégrée de la liste d’images pour la faire glisser.

> [!NOTE]
> Si la liste d’images a été créée avec l' **`new`** opérateur, vous devez détruire l' `CImageList` objet une fois que vous avez fini de l’utiliser.

## <a name="see-also"></a>Voir aussi

[Utilisation de CImageList](../mfc/using-cimagelist.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
