---
title: Récupération des données à partir de l’objet de la boîte de dialogue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3055468c04bba7c9cb999d0a642c0819524ff7e7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391408"
---
# <a name="retrieving-data-from-the-dialog-object"></a>Récupérer des données d'un objet Dialog

Le framework fournit un moyen simple pour initialiser les valeurs des contrôles dans une boîte de dialogue et pour récupérer les valeurs des contrôles. L’approche manuelle plus laborieuse consiste à appeler des fonctions telles que la `SetDlgItemText` et `GetDlgItemText` fonctions membres de classe `CWnd`, qui s’appliquent aux fenêtres de contrôle. Avec ces fonctions, vous accéder à chaque contrôle individuellement afin de définir ou obtenir sa valeur, appeler des fonctions telles que `SetWindowText` et `GetWindowText`. Approche de l’infrastructure automatise l’initialisation et la récupération.

Échange de données de boîtes de dialogue (DDX) vous permet d’échanger des données entre les contrôles dans les boîte de dialogue et les variables membres dans l’objet de la boîte de dialogue plus facilement. Cet échange fonctionne dans les deux sens. Pour initialiser les contrôles dans la boîte de dialogue, vous pouvez définir les valeurs des membres de données dans l’objet de la boîte de dialogue et le framework transférera les valeurs pour les contrôles avant de la boîte de dialogue s’affiche. Puis vous pouvez à tout moment mettre à jour les membres de données de boîte de dialogue avec les données entrées par l’utilisateur. À ce stade, vous pouvez utiliser les données en faisant référence aux variables de membre de données.

Vous pouvez également organiser les valeurs des contrôles de boîte de dialogue d’être validés automatiquement avec la validation de données de boîtes de dialogue (DDV).

DDX et DDV sont expliqués plus en détail dans [échange de données de boîtes de dialogue et la Validation](../mfc/dialog-data-exchange-and-validation.md).

Pour une boîte de dialogue modale, vous pouvez récupérer des données de l’utilisateur a entré lorsque `DoModal` retourne IDOK mais avant de la boîte de dialogue est détruit. Pour une boîte de dialogue non modale, vous pouvez récupérer des données à partir de l’objet de la boîte de dialogue à tout moment en appelant `UpdateData` avec l’argument **TRUE** et ensuite l’accès aux variables de membre de classe de boîte de dialogue. Ce sujet est abordé plus en détail dans [échange de données de boîtes de dialogue et la Validation](../mfc/dialog-data-exchange-and-validation.md).

## <a name="see-also"></a>Voir aussi

[Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)

