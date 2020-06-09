---
title: Nettoyage des documents et vues
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 8cb6e9337b69daf78286f57898c9badf513c7921
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626522"
---
# <a name="cleaning-up-documents-and-views"></a>Nettoyage des documents et vues

Lors de la fermeture d’un document, l’infrastructure appelle d’abord sa fonction membre [DeleteContents](reference/cdocument-class.md#deletecontents) . Si vous avez alloué de la mémoire sur le tas au cours de l’opération du document, `DeleteContents` est le meilleur endroit pour le libérer.

> [!NOTE]
> Vous ne devez pas désallouer des données de document dans le destructeur du document. Dans le cas d’une application SDI, l’objet document peut être réutilisé.

Vous pouvez substituer le destructeur d’une vue pour libérer la mémoire que vous avez allouée sur le tas.

## <a name="see-also"></a>Voir aussi

[Initialisation et nettoyage des documents et vues](initializing-and-cleaning-up-documents-and-views.md)
