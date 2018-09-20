---
title: Rôle de la vue dans l’impression | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- views [MFC], printing
- OnDraw method [MFC], and printing
- printing [MFC], OnDraw method [MFC]
- printing [MFC], views
- CView class [MFC], role in printing
- printing views [MFC]
ms.assetid: 8d4a3c8e-1fce-4edc-b608-94cb5f3e487e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c78756ea84df66b77f71d8f8ad8d0b9dfa1a6c9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377524"
---
# <a name="role-of-the-view-in-printing"></a>Rôle de la vue dans l'impression

Votre vue joue également deux rôles importants dans l’impression de son document associé.

La vue :

- Utilise le même [OnDraw](../mfc/reference/cview-class.md#ondraw) code pour dessiner sur l’imprimante que pour dessiner sur l’écran.

- Gère les diviser le document en pages pour l’impression.

Pour plus d’informations sur l’impression et sur le rôle de la vue dans l’impression, consultez [l’impression et Aperçu avant impression](../mfc/printing-and-print-preview.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de vues](../mfc/using-views.md)

