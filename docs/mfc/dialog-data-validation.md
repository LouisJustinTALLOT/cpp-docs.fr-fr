---
description: 'En savoir plus sur : validation des données de boîte de dialogue'
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
ms.openlocfilehash: 0e90aa54130a59b48058928f56d9d36644d5142b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261357"
---
# <a name="dialog-data-validation"></a>Validation de données de boîtes de dialogue

Vous pouvez spécifier la validation en plus de l’échange de données en appelant des fonctions DDV, comme indiqué dans l’exemple dans [échange de données de boîtes de dialogue](dialog-data-exchange.md). L' `DDV_MaxChars` appel dans l’exemple valide que la chaîne entrée dans le contrôle de zone de texte ne dépasse pas 20 caractères. La fonction DDV avertit généralement l’utilisateur avec une boîte de message si la validation échoue et place le focus sur le contrôle incriminé afin que l’utilisateur puisse à nouveau entrer les données. Une fonction DDV pour un contrôle donné doit être appelée immédiatement après la fonction DDX pour le même contrôle.

Vous pouvez également définir vos propres routines DDX et DDV personnalisées. Pour plus d’informations sur cet aspect et d’autres aspects de DDX et DDV, consultez la [note technique MFC 26](tn026-ddx-and-ddv-routines.md).

L' [Assistant Ajout de variable membre](../ide/adding-a-member-variable-visual-cpp.md#add-member-variable-wizard) écrira tous les appels DDX et DDV dans le mappage de données pour vous.

## <a name="see-also"></a>Voir aussi

[Échange et validation des données de boîte de dialogue](dialog-data-exchange-and-validation.md)<br/>
[Utilisation des boîtes de dialogue dans MFC](life-cycle-of-a-dialog-box.md)<br/>
[Échange de données de boîtes de dialogue](dialog-data-exchange.md)
