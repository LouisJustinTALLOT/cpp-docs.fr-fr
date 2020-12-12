---
description: 'En savoir plus sur : sérialisation : sérialisation d’un objet'
title: "Sérialisation : sérialisation d'un objet"
ms.date: 11/04/2016
helpviewer_keywords:
- serializing objects [MFC]
- serialization [MFC], objects
- objects [MFC], serializing
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
ms.openlocfilehash: ec0782f7faa0d6400f40013925f4a53495a76c7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217470"
---
# <a name="serialization-serializing-an-object"></a>Sérialisation : sérialisation d'un objet

La sérialisation de l’article [: la création d’une classe sérialisable](../mfc/serialization-making-a-serializable-class.md) montre comment rendre une classe sérialisable. Une fois que vous avez une classe sérialisable, vous pouvez sérialiser les objets de cette classe vers et à partir d’un fichier à l’aide d’un objet [CArchive](../mfc/reference/carchive-class.md) . Cet article explique les éléments suivants :

- [Ce qu’est un objet CArchive](../mfc/what-is-a-carchive-object.md).

- [Deux méthodes pour créer un CArchive](../mfc/two-ways-to-create-a-carchive-object.md).

- [Comment utiliser les \< and > opérateurs de> CArchive <](../mfc/using-the-carchive-output-and-input-operators.md).

- [Stockage et chargement de CObjects via une archive](../mfc/storing-and-loading-cobjects-via-an-archive.md).

Vous pouvez laisser l’infrastructure créer l’Archive pour votre document sérialisable ou créer vous-même l’objet de manière explicite `CArchive` . Vous pouvez transférer des données entre un fichier et votre objet sérialisable à l’aide des \< and > opérateurs <> pour `CArchive` ou, dans certains cas, en appelant la `Serialize` fonction d’une `CObject` classe dérivée de.

## <a name="see-also"></a>Voir aussi

[Sérialisation](../mfc/serialization-in-mfc.md)
