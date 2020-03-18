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
ms.openlocfilehash: 368421a86d6ff6fc70455edd0ea9a32e05645007
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446367"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Stockage et chargement de CObjects via une archive

Le stockage et le chargement de `CObject`s via une archive nécessitent une attention particulière. Dans certains cas, vous devez appeler la fonction `Serialize` de l’objet, où l’objet `CArchive` est un paramètre de l’appel `Serialize`, par opposition à l’utilisation de l’opérateur **<\<** ou **>>** de l' `CArchive`. Il est important de garder à l’esprit que l’opérateur `CArchive` **>>** construit le `CObject` en mémoire en fonction des informations `CRuntimeClass` précédemment écrites dans le fichier par l’archive de stockage.

Par conséquent, si vous utilisez les opérateurs `CArchive` **<\<** et **>>** , par opposition à l’appel de `Serialize`, varie selon que vous *avez besoin* de l’archive de chargement pour reconstruire dynamiquement l’objet en fonction des informations de `CRuntimeClass` précédemment stockées. Utilisez la fonction `Serialize` dans les cas suivants :

- Lors de la désérialisation de l’objet, vous connaissez à l’avance la classe exacte de l’objet.

- Lors de la désérialisation de l’objet, vous disposez déjà de la mémoire allouée pour celui-ci.

> [!CAUTION]
>  Si vous chargez l’objet à l’aide de la fonction `Serialize`, vous devez également stocker l’objet à l’aide de la fonction `Serialize`. Ne stockez pas à l’aide de l’opérateur `CArchive` **<<** puis chargez à l’aide de la fonction `Serialize`, ou stockez à l’aide de la fonction `Serialize`, puis chargez à l’aide de l’opérateur `CArchive >>`.

L’exemple suivant illustre les cas :

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

En résumé, si votre classe sérialisable définit un `CObject` incorporé en tant que membre, vous ne devez *pas* utiliser les opérateurs `CArchive` **<\<** et **>>** pour cet objet, mais vous devez appeler la fonction `Serialize` à la place. En outre, si votre classe sérialisable définit un pointeur vers une `CObject` (ou un objet dérivé de `CObject`) en tant que membre, mais construit cet autre objet dans son propre constructeur, vous devez également appeler `Serialize`.

## <a name="see-also"></a>Voir aussi

[Sérialisation : sérialisation d’un objet](../mfc/serialization-serializing-an-object.md)
