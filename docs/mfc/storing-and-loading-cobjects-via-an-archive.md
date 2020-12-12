---
description: 'En savoir plus sur : stockage et chargement de CObjects via une archive'
title: Stockage et chargement de CObjects via une archive
ms.date: 11/04/2016
helpviewer_keywords:
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
ms.openlocfilehash: c84c507fc556268eea526c1350211fd4b82f54fe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216559"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Stockage et chargement de CObjects via une archive

Le stockage et le chargement des `CObject` s via une archive nécessitent une attention particulière. Dans certains cas, vous devez appeler la `Serialize` fonction de l’objet, où l' `CArchive` objet est un paramètre de l' `Serialize` appel, par opposition à l’utilisation **<\<** or **>>** de l’opérateur de `CArchive` . Le fait de garder à l’esprit est que l' `CArchive` **>>** opérateur construit le `CObject` en mémoire en fonction des `CRuntimeClass` informations précédemment écrites dans le fichier par l’archive de stockage.

Par conséquent, l’utilisation des `CArchive` **<\<** and **>>** opérateurs, par opposition à l’appel de `Serialize` , varie selon que vous *avez besoin* de l’archive de chargement pour reconstruire dynamiquement l’objet en fonction des informations précédemment stockées `CRuntimeClass` . Utilisez la `Serialize` fonction dans les cas suivants :

- Lors de la désérialisation de l’objet, vous connaissez à l’avance la classe exacte de l’objet.

- Lors de la désérialisation de l’objet, vous disposez déjà de la mémoire allouée pour celui-ci.

> [!CAUTION]
> Si vous chargez l’objet à l’aide de la `Serialize` fonction, vous devez également stocker l’objet à l’aide de la `Serialize` fonction. Ne stockez pas l' `CArchive` **<<** opérateur, puis chargez à l’aide de la `Serialize` fonction, ou stockez à l’aide de la fonction, puis `Serialize` chargez à l’aide de l' `CArchive >>` opérateur.

L’exemple suivant illustre les cas :

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

En résumé, si votre classe sérialisable définit une incorporée `CObject` en tant que membre, vous ne devez *pas* utiliser les `CArchive` **<\<** and **>>** opérateurs pour cet objet, mais vous devez appeler la fonction à la `Serialize` place. En outre, si votre classe sérialisable définit un pointeur vers un `CObject` (ou un objet dérivé de `CObject` ) en tant que membre, mais construit cet autre objet dans son propre constructeur, vous devez également appeler `Serialize` .

## <a name="see-also"></a>Voir aussi

[Sérialisation : sérialisation d’un objet](../mfc/serialization-serializing-an-object.md)
