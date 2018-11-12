---
title: Mappage des messages Windows à votre classe
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
ms.openlocfilehash: 37c0f61f4d38e3e152d9dd508c9487782ebdf81a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630458"
---
# <a name="mapping-windows-messages-to-your-class"></a>Mappage des messages Windows à votre classe

Si vous avez besoin de votre boîte de dialogue pour gérer les messages Windows, remplacez les fonctions de gestionnaire approprié. Pour ce faire, utilisez la fenêtre des propriétés [mapper les messages](../mfc/reference/mapping-messages-to-functions.md) à la classe de boîte de dialogue. Il écrit une entrée de table des messages pour chaque message et ajoute les fonctions membres de gestionnaire de messages à la classe. Utilisez l’éditeur de code source Visual C++ pour écrire du code dans les gestionnaires de messages.

Vous pouvez également remplacer les fonctions membres de [CDialog](../mfc/reference/cdialog-class.md) et ses classes de base, en particulier [CWnd](../mfc/reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Mappage et gestion des messages](../mfc/message-handling-and-mapping.md)

- [Fonctions membres couramment substituées](../mfc/commonly-overridden-member-functions.md)

- [Fonctions membres couramment ajoutées](../mfc/commonly-added-member-functions.md)

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](../mfc/dialog-boxes.md)<br/>
[Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)

