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
ms.openlocfilehash: cef9941cccd49ca61f0a93472636656f7241a61e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383813"
---
# <a name="dialog-data-validation"></a>Validation de données de boîtes de dialogue

Vous pouvez spécifier la validation en plus de l’échange de données en appelant les fonctions DDV, comme indiqué dans l’exemple de [échange de données de boîtes de dialogue](../mfc/dialog-data-exchange.md). Le `DDV_MaxChars` appel dans l’exemple valide le fait que la chaîne entrée dans le contrôle de zone de texte n’est pas plue de 20 caractères. La fonction DDV avertit en général, l’utilisateur avec une boîte de message si la validation échoue et place le focus sur le contrôle incriminé afin de l’utilisateur peut entrer à nouveau les données. Une fonction DDV pour un contrôle donné doit être appelée immédiatement après la fonction DDX pour le même contrôle.

Vous pouvez également définir vos propres routines DDX et DDV personnalisées. Pour plus d’informations sur cela et d’autres aspects de DDX et DDV, consultez [MFC Technical Note 26](../mfc/tn026-ddx-and-ddv-routines.md).

Le [Assistant Ajout de Variable membre](../ide/add-member-variable-wizard.md) écrira tous le DDX et DDV appelle dans le mappage de données pour vous.

## <a name="see-also"></a>Voir aussi

[Échange et validation de données de boîtes de dialogue](../mfc/dialog-data-exchange-and-validation.md)<br/>
[Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Échange de données de boîtes de dialogue](../mfc/dialog-data-exchange.md)
