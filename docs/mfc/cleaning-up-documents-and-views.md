---
title: Nettoyage des documents et vues
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 1357a02379a848af23a6f78dee29e5b6adc1efcc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653893"
---
# <a name="cleaning-up-documents-and-views"></a>Nettoyage des documents et vues

Lors de la fermeture d’un document, le framework appelle d’abord son [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) fonction membre. Si vous avez alloué de la mémoire dans le tas au cours de l’utilisation du document, `DeleteContents` est le meilleur endroit pour la libérer.

> [!NOTE]
>  Vous ne devez pas libérer les données de document dans le destructeur du document. Dans le cas d’une application SDI, l’objet de document peut être réutilisé.

Vous pouvez remplacer le destructeur d’une vue pour libérer toute mémoire allouée sur le tas.

## <a name="see-also"></a>Voir aussi

[Initialisation et nettoyage des documents et vues](../mfc/initializing-and-cleaning-up-documents-and-views.md)

