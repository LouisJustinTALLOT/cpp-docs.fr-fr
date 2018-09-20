---
title: À l’aide d’une liste d’images | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4dc30d418ae57205e4566dad7f490a773321768e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391668"
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

