---
title: Validation de données de boîtes de dialogue
ms.date: 11/04/2016
helpviewer_keywords:
- validating data [MFC], message boxes
- data validation [MFC], dialog boxes
- dialog boxes [MFC], validating data
- validating data [MFC], dialog box data entry
- DDV (dialog data validation) [MFC]
- data validation [MFC], message boxes
ms.assetid: f070c309-2044-4ff2-8c92-1ec1ea84af58
ms.openlocfilehash: c89ed82b148062ddb64fa85eaabda12f44e59895
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685770"
---
# <a name="dialog-data-validation"></a>Validation de données de boîtes de dialogue

Vous pouvez spécifier la validation en plus de l’échange de données en appelant des fonctions DDV, comme indiqué dans l’exemple dans [échange de données de boîtes de dialogue](../mfc/dialog-data-exchange.md). L’appel `DDV_MaxChars` dans l’exemple confirme que la chaîne entrée dans le contrôle de zone de texte ne dépasse pas 20 caractères. La fonction DDV avertit généralement l’utilisateur avec une boîte de message si la validation échoue et place le focus sur le contrôle incriminé afin que l’utilisateur puisse à nouveau entrer les données. Une fonction DDV pour un contrôle donné doit être appelée immédiatement après la fonction DDX pour le même contrôle.

Vous pouvez également définir vos propres routines DDX et DDV personnalisées. Pour plus d’informations sur cet aspect et d’autres aspects de DDX et DDV, consultez la [note technique MFC 26](../mfc/tn026-ddx-and-ddv-routines.md).

L' [Assistant Ajout de variable membre](../ide/add-member-variable-wizard.md) écrira tous les appels DDX et DDV dans le mappage de données pour vous.

## <a name="see-also"></a>Voir aussi

[Échange et validation de données de boîtes de dialogue](../mfc/dialog-data-exchange-and-validation.md)<br/>
[Utilisation des boîtes de dialogue dans MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Échange de données de boîtes de dialogue](../mfc/dialog-data-exchange.md)
