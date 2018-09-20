---
title: Nettoyage des Documents et vues | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4325b0de10861fc76ee9ab816376f40ba0ba587
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437415"
---
# <a name="cleaning-up-documents-and-views"></a>Nettoyage des documents et vues

Lors de la fermeture d’un document, le framework appelle d’abord son [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) fonction membre. Si vous avez alloué de la mémoire dans le tas au cours de l’utilisation du document, `DeleteContents` est le meilleur endroit pour la libérer.

> [!NOTE]
>  Vous ne devez pas libérer les données de document dans le destructeur du document. Dans le cas d’une application SDI, l’objet de document peut être réutilisé.

Vous pouvez remplacer le destructeur d’une vue pour libérer toute mémoire allouée sur le tas.

## <a name="see-also"></a>Voir aussi

[Initialisation et nettoyage des documents et vues](../mfc/initializing-and-cleaning-up-documents-and-views.md)

