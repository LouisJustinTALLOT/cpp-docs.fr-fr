---
title: Utilisation d'une liste d'images
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: 0d9566739a15e5d216eb052a7265313850515648
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366575"
---
# <a name="using-an-image-list"></a>Utilisation d'une liste d'images

L’utilisation typique d’une liste d’images suit le modèle ci-dessous :

- Construisez un objet [CImageList](../mfc/reference/cimagelist-class.md) et appelez l’une des surcharges de sa `CImageList` fonction [Créer](../mfc/reference/cimagelist-class.md#create) pour créer une liste d’images et l’attacher à l’objet.

- Si vous n’avez pas ajouté d’images lorsque vous avez créé la liste d’images, ajoutez des images à la liste d’images en appelant la fonction membre [Add](../mfc/reference/cimagelist-class.md#add) or [Read.](../mfc/reference/cimagelist-class.md#read)

- Associez la liste d’images à un contrôle en appelant la fonction membre appropriée de ce contrôle, ou dessinez des images de la liste d’images vous-même à l’aide de la fonction de membre [Draw](../mfc/reference/cimagelist-class.md#draw) de la liste d’images.

- Peut-être permettre à l’utilisateur de faire glisser une image, en utilisant le support intégré de la liste d’images pour le dragage.

> [!NOTE]
> Si la liste d’images a été créée `CImageList` avec le **nouvel** opérateur, vous devez détruire l’objet lorsque vous en avez fini avec elle.

## <a name="see-also"></a>Voir aussi

[Utilisation de CImageList](../mfc/using-cimagelist.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
