---
title: Fermeture de la boîte de dialogue
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: fe57c5603f1b0e9ea0b6fb9e6ea8d80bec961f6e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448111"
---
# <a name="closing-the-dialog-box"></a>Fermeture de la boîte de dialogue

Une boîte de dialogue modale se ferme lorsque l’utilisateur choisit l’un de ses boutons, généralement le bouton OK ou annuler. En choisissant le bouton OK ou Annuler entraîne Windows envoyer l’objet de la boîte de dialogue un **BN_CLICKED** message de notification de contrôle avec le bouton ID de l’élément, soit **IDOK** ou **IDCANCEL**. `CDialog` Fournit des fonctions de gestionnaire par défaut pour ces messages : `OnOK` et `OnCancel`. L’appel de gestionnaires par défaut le `EndDialog` fonction membre pour fermer la boîte de dialogue. Vous pouvez également appeler `EndDialog` à partir de votre propre code. Pour plus d’informations, consultez le [EndDialog](../mfc/reference/cdialog-class.md#enddialog) fonction membre de classe `CDialog` dans le *référence MFC*.

Pour réorganiser pour clôture et suppression d’une boîte de dialogue non modale, vous devez substituer `PostNcDestroy` et appeler le **supprimer** opérateur sur le **cela** pointeur. [Destruction de la boîte de dialogue](../mfc/destroying-the-dialog-box.md) explique ce qui se passe ensuite.

## <a name="see-also"></a>Voir aussi

[Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)

