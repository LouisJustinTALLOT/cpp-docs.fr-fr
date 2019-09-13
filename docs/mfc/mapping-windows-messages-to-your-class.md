---
title: Mappage des messages Windows à votre classe
ms.date: 09/06/2019
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
- Class Wizard [MFC]
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
ms.openlocfilehash: 49d1a888b148793f82cf214637956589d6b8ff07
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907478"
---
# <a name="mapping-windows-messages-to-your-class"></a>Mappage des messages Windows à votre classe

Si vous avez besoin que votre boîte de dialogue gère les messages Windows, substituez les fonctions de gestionnaire appropriées. Pour ce faire, choisissez l’onglet **affichage de classes** dans **Explorateur de solutions**, cliquez avec le bouton droit sur la classe qui représente la boîte de dialogue, puis choisissez [Assistant classe](reference/mfc-class-wizard.md). Utilisez l’Assistant pour [mapper les messages](../mfc/reference/mapping-messages-to-functions.md) à la classe dialog. Cela écrit une entrée de table des messages pour chaque message et ajoute les fonctions membres du gestionnaire de messages à la classe. Utilisez l’éditeur de code pour écrire du code dans les gestionnaires de messages.

Vous pouvez également substituer les fonctions membres de [CDialog](../mfc/reference/cdialog-class.md) et ses classes de base, en particulier [CWnd](../mfc/reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Gestion et mappage des messages](../mfc/message-handling-and-mapping.md)

- [Fonctions membres couramment substituées](../mfc/commonly-overridden-member-functions.md)

- [Fonctions membres couramment ajoutées](../mfc/commonly-added-member-functions.md)

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](../mfc/dialog-boxes.md)<br/>
[Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)
