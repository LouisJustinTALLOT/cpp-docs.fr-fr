---
title: 'Sérialisation : Sérialisation d’un objet'
ms.date: 11/04/2016
helpviewer_keywords:
- serializing objects [MFC]
- serialization [MFC], objects
- objects [MFC], serializing
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
ms.openlocfilehash: 5c1106f180c587894283575a82a88e9e18b5c01a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290489"
---
# <a name="serialization-serializing-an-object"></a>Sérialisation : Sérialisation d’un objet

L’article [sérialisation : Définir une classe sérialisable](../mfc/serialization-making-a-serializable-class.md) montre comment rendre une classe sérialisable. Une fois que vous avez une classe sérialisable, vous pouvez sérialiser des objets de cette classe vers et à partir d’un fichier via un [CArchive](../mfc/reference/carchive-class.md) objet. Cet article explique :

- [Est un objet CArchive](../mfc/what-is-a-carchive-object.md).

- [Deux façons de créer un objet CArchive](../mfc/two-ways-to-create-a-carchive-object.md).

- [Comment utiliser CArchive <\< et >> opérateurs](../mfc/using-the-carchive-output-and-input-operators.md).

- [Stockage et chargement de CObjects via une archive](../mfc/storing-and-loading-cobjects-via-an-archive.md).

Vous pouvez laisser le framework de créer l’archive de votre document sérialisable ou de créer explicitement le `CArchive` vous-même l’objet. Vous pouvez transférer des données entre un fichier et l’objet sérialisable à l’aide de la <\< et >> opérateurs pour `CArchive` ou, dans certains cas, en appelant le `Serialize` fonction d’un `CObject`-classe dérivée.

## <a name="see-also"></a>Voir aussi

[Sérialisation](../mfc/serialization-in-mfc.md)
