---
title: Fermeture de la boîte de dialogue
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: 48ea954552b3ea9aa7193a47fc2a66d731312d77
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685372"
---
# <a name="closing-the-dialog-box"></a>Fermeture de la boîte de dialogue

Une boîte de dialogue modale se ferme lorsque l’utilisateur choisit l’un de ses boutons, généralement le bouton OK ou annuler. Si vous choisissez le bouton OK ou annuler, Windows envoie l’objet de boîte de dialogue à un message de notification de contrôle **BN_CLICKED** avec l’ID du bouton, **IDOK** ou **IDCANCEL**. `CDialog` fournit des fonctions de gestionnaire par défaut pour ces messages : `OnOK` et `OnCancel`. Les gestionnaires par défaut appellent la fonction membre `EndDialog` pour fermer la fenêtre de dialogue. Vous pouvez également appeler `EndDialog` à partir de votre propre code. Pour plus d’informations, consultez la fonction membre [EndDialog](../mfc/reference/cdialog-class.md#enddialog) de la classe `CDialog` dans la *référence MFC*.

Pour organiser la fermeture et la suppression d’une boîte de dialogue non modale, substituez `PostNcDestroy` et appelez l’opérateur **Delete** sur le pointeur **This** . [La destruction de la boîte de dialogue](../mfc/destroying-the-dialog-box.md) explique ce qui se passe ensuite.

## <a name="see-also"></a>Voir aussi

[Utilisation des boîtes de dialogue dans MFC](../mfc/life-cycle-of-a-dialog-box.md)
