---
description: 'En savoir plus sur : fermeture de la boîte de dialogue'
title: Fermeture de la boîte de dialogue
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: 4e60bdfb1ecb6968996d6c657f0c667ad2686a56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338369"
---
# <a name="closing-the-dialog-box"></a>Fermeture de la boîte de dialogue

Une boîte de dialogue modale se ferme lorsque l’utilisateur choisit l’un de ses boutons, généralement le bouton OK ou annuler. Si vous choisissez le bouton OK ou annuler, Windows envoie l’objet de boîte de dialogue à un **BN_CLICKED** message de notification de contrôle avec l’ID du bouton, **IDOK** ou **IDCANCEL**. `CDialog` fournit des fonctions de gestionnaire par défaut pour ces messages : `OnOK` et `OnCancel` . Les gestionnaires par défaut appellent la `EndDialog` fonction membre pour fermer la fenêtre de dialogue. Vous pouvez également appeler `EndDialog` à partir de votre propre code. Pour plus d’informations, consultez la fonction membre [EndDialog](reference/cdialog-class.md#enddialog) de `CDialog` la classe dans la *référence MFC*.

Pour organiser la fermeture et la suppression d’une boîte de dialogue non modale, substituez `PostNcDestroy` et appelez l' **`delete`** opérateur sur le **`this`** pointeur. [La destruction de la boîte de dialogue](destroying-the-dialog-box.md) explique ce qui se passe ensuite.

## <a name="see-also"></a>Voir aussi

[Utilisation des boîtes de dialogue dans MFC](life-cycle-of-a-dialog-box.md)
