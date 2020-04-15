---
title: Nettoyage des documents et vues
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 06ff60a2cf6245f64e80d899c13a8444558fcf0b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374623"
---
# <a name="cleaning-up-documents-and-views"></a>Nettoyage des documents et vues

Lorsqu’un document se termine, le cadre appelle d’abord sa fonction de membre [DeleteContents.](../mfc/reference/cdocument-class.md#deletecontents) Si vous avez alloué une mémoire sur le tas au `DeleteContents` cours de l’opération du document, est le meilleur endroit pour traiter.

> [!NOTE]
> Vous ne devez pas traiter les données de documents dans le destructeur du document. Dans le cas d’une application SDI, l’objet du document peut être réutilisé.

Vous pouvez remplacer le destructeur d’une vue pour traiter n’importe quel souvenir que vous avez alloué sur le tas.

## <a name="see-also"></a>Voir aussi

[Initialisation et nettoyage des documents et vues](../mfc/initializing-and-cleaning-up-documents-and-views.md)
