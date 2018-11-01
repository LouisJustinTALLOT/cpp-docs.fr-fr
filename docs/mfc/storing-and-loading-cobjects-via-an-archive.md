---
title: Stockage et chargement de CObjects via une archive
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
ms.openlocfilehash: 370e8202d1bd1cda04edbdbd12bd936bdf5ef7b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493689"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Stockage et chargement de CObjects via une archive

Stockage et chargement `CObject`via une archive nécessite un examen supplémentaire. Dans certains cas, vous devez appeler la `Serialize` fonction de l’objet, où le `CArchive` objet est un paramètre de la `Serialize` appel, au lieu d’utiliser le **< \<** ou **>>** opérateur de la `CArchive`. L’élément important à retenir est que le `CArchive` **>>** opérateur constructions le `CObject` en mémoire selon `CRuntimeClass` informations précédemment écrites dans le fichier par l’archive de stockage.

Par conséquent, vous utilisiez le `CArchive` **< \<** et **>>** opérateurs, par rapport à appeler `Serialize`, varie selon que vous *devez* l’archive de chargement pour reconstruire dynamiquement l’objet selon précédemment stockée `CRuntimeClass` plus d’informations. Utilisez le `Serialize` (fonction) dans les cas suivants :

- Lors de la désérialisation de l’objet, vous savez exactement de la classe de l’objet au préalable.

- Lors de la désérialisation de l’objet, vous disposez déjà de mémoire allouée pour celui-ci.

> [!CAUTION]
>  Si vous chargez l’objet en utilisant le `Serialize` (fonction), vous devez également stocker l’objet en utilisant le `Serialize` (fonction). Ne stockez pas à l’aide de la `CArchive` **<<** opérateur et charge ensuite à l’aide la `Serialize` de fonction, ou stocker à l’aide de la `Serialize` de fonction, puis les charger à l’aide de `CArchive >>` opérateur.

L’exemple suivant illustre les cas :

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

En résumé, si votre classe sérialisable définit un embedded `CObject` en tant que membre, vous devez *pas* utiliser le `CArchive` **< \<** et **>>** opérateurs pour cet objet, mais vous devez appeler la `Serialize` fonctionner à la place. En outre, si votre classe sérialisable définit un pointeur vers un `CObject` (ou un objet dérivé `CObject`) en tant que membre, mais les constructions cette autre objet dans son propre constructeur, vous devez également appeler `Serialize`.

## <a name="see-also"></a>Voir aussi

[Sérialisation : sérialisation d’un objet](../mfc/serialization-serializing-an-object.md)

