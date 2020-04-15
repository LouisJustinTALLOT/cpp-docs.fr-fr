---
title: Stockage et chargement de CObjects via une archive
ms.date: 11/04/2016
helpviewer_keywords:
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
ms.openlocfilehash: f1b59516d5bba13b6f5e006f91d8ebd560543b05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372148"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Stockage et chargement de CObjects via une archive

Le stockage `CObject`et le chargement de s via une archive nécessitent une considération supplémentaire. Dans certains cas, vous `Serialize` devez appeler la `CArchive` fonction de l’objet, lorsque l’objet est un paramètre de `Serialize` l’appel, par opposition à l’utilisation de l’ou ** < ** **>>** de l’opérateur de la `CArchive`. Le fait important à garder `CArchive` **>>** à l’esprit est que l’opérateur construit la `CObject` mémoire en fonction `CRuntimeClass` des informations précédemment écrites au fichier par l’archive de stockage.

Par conséquent, si `CArchive` ** < ** **>>** vous utilisez `Serialize`le et les opérateurs, par rapport à l’appel `CRuntimeClass` , dépend si vous avez besoin *de* l’archive de chargement pour reconstruire dynamiquement l’objet en fonction des informations précédemment stockées. Utilisez `Serialize` la fonction dans les cas suivants :

- Lorsque vous désétialisez l’objet, vous connaissez la classe exacte de l’objet à l’avance.

- Lors de la désétérialisation de l’objet, vous avez déjà la mémoire allouée pour elle.

> [!CAUTION]
> Si vous chargez `Serialize` l’objet à l’aide `Serialize` de la fonction, vous devez également stocker l’objet à l’aide de la fonction. Ne stockez pas `CArchive` **<<** l’utilisation de `Serialize` l’opérateur, `Serialize` puis chargez `CArchive >>` à l’aide de la fonction, ou stockez l’utilisation de la fonction, puis chargez à l’aide de l’opérateur.

L’exemple suivant illustre les cas :

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

En résumé, si votre classe sérialisable définit une intégration `CObject` en **>>** tant que membre, vous `Serialize` ne devriez *pas* utiliser le `CArchive` ** < ** et les opérateurs pour cet objet, mais devrait appeler la fonction à la place. En outre, si votre classe sérialisable définit un pointeur à un `CObject` (ou un objet dérivé de `CObject`) en `Serialize`tant que membre, mais construit cet autre objet dans son propre constructeur, vous devriez également appeler .

## <a name="see-also"></a>Voir aussi

[Sérialisation : sérialisation d’un objet](../mfc/serialization-serializing-an-object.md)
