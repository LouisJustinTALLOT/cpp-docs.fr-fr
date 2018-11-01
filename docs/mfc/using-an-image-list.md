---
title: Utilisation d'une liste d'images
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: fb0636d29d5bf72007eb440f763de0d5e1f4b581
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581244"
---
# <a name="using-an-image-list"></a>Utilisation d'une liste d'images

L’utilisation normale d’une liste d’images suit le modèle suivant :

- Construire un [CImageList](../mfc/reference/cimagelist-class.md) de l’objet et appelez une des surcharges de son [créer](../mfc/reference/cimagelist-class.md#create) (fonction) pour créer une liste d’images et l’attacher à la `CImageList` objet.

- Si vous n’avez pas ajouté les images lorsque vous avez créé la liste d’images, ajouter des images à la liste d’images en appelant le [ajouter](../mfc/reference/cimagelist-class.md#add) ou [en lecture](../mfc/reference/cimagelist-class.md#read) fonction membre.

- Associer la liste d’images à un contrôle en appelant la fonction membre approprié de ce contrôle, ou dessiner des images à partir de la liste d’images vous-même à l’aide de la liste d’images [dessiner](../mfc/reference/cimagelist-class.md#draw) fonction membre.

- Peut-être autoriser l’utilisateur à faire glisser une image, à l’aide de la prise en charge intégrée de la liste d’images pour faire glisser.

> [!NOTE]
>  Si la liste d’images a été créée avec le **nouveau** opérateur, vous devez détruire le `CImageList` de l’objet lorsque vous avez terminé avec lui.

## <a name="see-also"></a>Voir aussi

[Utilisation de CImageList](../mfc/using-cimagelist.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

