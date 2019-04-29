---
title: Fermeture de la boîte de dialogue
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: 07e4159eccde1fab89d4a5ffadee4e6d11fc20f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326844"
---
# <a name="closing-the-dialog-box"></a>Fermeture de la boîte de dialogue

Une boîte de dialogue modale se ferme lorsque l’utilisateur choisit l’un de ses boutons, généralement le bouton OK ou annuler. En choisissant le bouton OK ou Annuler entraîne Windows envoyer l’objet de la boîte de dialogue un **BN_CLICKED** message de notification de contrôle avec le bouton ID de l’élément, soit **IDOK** ou **IDCANCEL**. `CDialog` Fournit des fonctions de gestionnaire par défaut pour ces messages : `OnOK` et `OnCancel`. L’appel de gestionnaires par défaut le `EndDialog` fonction membre pour fermer la boîte de dialogue. Vous pouvez également appeler `EndDialog` à partir de votre propre code. Pour plus d’informations, consultez le [EndDialog](../mfc/reference/cdialog-class.md#enddialog) fonction membre de classe `CDialog` dans le *référence MFC*.

Pour réorganiser pour clôture et suppression d’une boîte de dialogue non modale, vous devez substituer `PostNcDestroy` et appeler le **supprimer** opérateur sur le **cela** pointeur. [Destruction de la boîte de dialogue](../mfc/destroying-the-dialog-box.md) explique ce qui se passe ensuite.

## <a name="see-also"></a>Voir aussi

[Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)
