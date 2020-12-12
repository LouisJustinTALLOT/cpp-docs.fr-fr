---
description: 'En savoir plus sur : récupération des données de l’objet Dialog'
title: Récupérer des données d'un objet Dialog
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], retrieving user data
- dialog box data [MFC]
- data [MFC], retrieving
- GetDlgItemText method [MFC]
- SetDlgItemText method [MFC]
- SetWindowText method [MFC]
- dialog box data [MFC], retrieving
- retrieving data [MFC]
- user input [MFC], retrieving from MFC dialog boxes
- capturing user input [MFC]
- dialog box controls [MFC], initializing values
- DDX (dialog data exchange) [MFC]
- MFC dialog boxes [MFC], retrieving user input
- data retrieval [MFC], dialog boxes
- data [MFC], dialog boxes
- DDX (dialog data exchange) [MFC], about DDX
- DDX (dialog data exchange) [MFC], retrieving data from Dialog object
- GetWindowText method [MFC]
ms.assetid: bdca2b61-6b53-4c2e-b426-8712c7a38ec0
ms.openlocfilehash: 823006b7b892c8e6476d007eb5cc13fb1386458e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218041"
---
# <a name="retrieving-data-from-the-dialog-object"></a>Récupérer des données d'un objet Dialog

L’infrastructure offre un moyen simple d’initialiser les valeurs des contrôles dans une boîte de dialogue et de récupérer des valeurs à partir des contrôles. L’approche manuelle plus fastidieuse consiste à appeler des fonctions telles que les `SetDlgItemText` `GetDlgItemText` fonctions membres et de la classe `CWnd` , qui s’appliquent aux fenêtres de contrôle. Avec ces fonctions, vous accédez à chaque contrôle individuellement pour définir ou recevoir sa valeur, en appelant des fonctions telles que `SetWindowText` et `GetWindowText` . L’approche de l’infrastructure automatise l’initialisation et la récupération.

L’échange de données de boîtes de dialogue (DDX) vous permet d’échanger des données entre les contrôles dans la boîte de dialogue et les variables de membre de l’objet de boîte de dialogue plus facilement. Cet échange fonctionne de deux manières. Pour initialiser les contrôles dans la boîte de dialogue, vous pouvez définir les valeurs des membres de données dans l’objet Dialog, et l’infrastructure transférera les valeurs vers les contrôles avant que la boîte de dialogue ne s’affiche. Ensuite, vous pouvez à tout moment mettre à jour les membres de données de boîte de dialogue avec des données entrées par l’utilisateur. À ce stade, vous pouvez utiliser les données en faisant référence aux variables de membre de données.

Vous pouvez également organiser les valeurs des contrôles de boîte de dialogue à valider automatiquement avec la validation des données de boîte de dialogue (DDV).

DDX et DDV sont expliqués plus en détail dans [échange et validation de données de boîtes de dialogue](../mfc/dialog-data-exchange-and-validation.md).

Pour une boîte de dialogue modale, vous pouvez récupérer toutes les données entrées par l’utilisateur quand `DoModal` retourne IDOK, mais avant que l’objet de boîte de dialogue soit détruit. Pour une boîte de dialogue non modale, vous pouvez récupérer des données de l’objet de boîte de dialogue à tout moment en appelant `UpdateData` avec l’argument **true** , puis en accédant aux variables de membre de la classe de boîte de dialogue. Ce sujet est abordé plus en détail dans [échange et validation de données de boîtes de dialogue](../mfc/dialog-data-exchange-and-validation.md).

## <a name="see-also"></a>Voir aussi

[Utilisation des boîtes de dialogue dans MFC](../mfc/life-cycle-of-a-dialog-box.md)
