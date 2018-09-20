---
title: Fermeture de la boîte de dialogue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e9ad4b8af63b68912c232767bf1fd14070fda261
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409049"
---
# <a name="closing-the-dialog-box"></a>Fermeture de la boîte de dialogue

Une boîte de dialogue modale se ferme lorsque l’utilisateur choisit l’un de ses boutons, généralement le bouton OK ou annuler. En choisissant le bouton OK ou Annuler entraîne Windows envoyer l’objet de la boîte de dialogue un **BN_CLICKED** message de notification de contrôle avec le bouton ID de l’élément, soit **IDOK** ou **IDCANCEL**. `CDialog` Fournit des fonctions de gestionnaire par défaut pour ces messages : `OnOK` et `OnCancel`. L’appel de gestionnaires par défaut le `EndDialog` fonction membre pour fermer la boîte de dialogue. Vous pouvez également appeler `EndDialog` à partir de votre propre code. Pour plus d’informations, consultez le [EndDialog](../mfc/reference/cdialog-class.md#enddialog) fonction membre de classe `CDialog` dans le *référence MFC*.

Pour réorganiser pour clôture et suppression d’une boîte de dialogue non modale, vous devez substituer `PostNcDestroy` et appeler le **supprimer** opérateur sur le **cela** pointeur. [Destruction de la boîte de dialogue](../mfc/destroying-the-dialog-box.md) explique ce qui se passe ensuite.

## <a name="see-also"></a>Voir aussi

[Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)

