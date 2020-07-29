---
title: Fermeture de la boîte de dialogue
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: ef6cdaeb4cb0d7537cda980a1d2c483c53c8dc9d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217972"
---
# <a name="closing-the-dialog-box"></a>Fermeture de la boîte de dialogue

Une boîte de dialogue modale se ferme lorsque l’utilisateur choisit l’un de ses boutons, généralement le bouton OK ou annuler. Si vous choisissez le bouton OK ou annuler, Windows envoie l’objet de boîte de dialogue à un **BN_CLICKED** message de notification de contrôle avec l’ID du bouton, **IDOK** ou **IDCANCEL**. `CDialog`fournit des fonctions de gestionnaire par défaut pour ces messages : `OnOK` et `OnCancel` . Les gestionnaires par défaut appellent la `EndDialog` fonction membre pour fermer la fenêtre de dialogue. Vous pouvez également appeler `EndDialog` à partir de votre propre code. Pour plus d’informations, consultez la fonction membre [EndDialog](reference/cdialog-class.md#enddialog) de `CDialog` la classe dans la *référence MFC*.

Pour organiser la fermeture et la suppression d’une boîte de dialogue non modale, substituez `PostNcDestroy` et appelez l' **`delete`** opérateur sur le **`this`** pointeur. [La destruction de la boîte de dialogue](destroying-the-dialog-box.md) explique ce qui se passe ensuite.

## <a name="see-also"></a>Voir aussi

[Utilisation des boîtes de dialogue dans MFC](life-cycle-of-a-dialog-box.md)
