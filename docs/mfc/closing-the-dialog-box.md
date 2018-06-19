---
title: Fermeture de la boîte de dialogue | Documents Microsoft
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
ms.openlocfilehash: c800c204fd09057585064397d459f92c9ded272d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341743"
---
# <a name="closing-the-dialog-box"></a>Fermeture de la boîte de dialogue
Boîte de dialogue modale se ferme lorsque l’utilisateur choisit un de ses boutons, généralement le bouton OK ou annuler. En choisissant le bouton OK ou sur Annuler provoque Windows envoyer l’objet de la boîte de dialogue un **BN_CLICKED** message de notification de contrôle avec le bouton ID de l’élément, soit **IDOK** ou **IDCANCEL**. `CDialog` Fournit des fonctions de gestionnaire par défaut pour ces messages : `OnOK` et `OnCancel`. Les gestionnaires par défaut appellent la `EndDialog` fonction membre pour fermer la boîte de dialogue. Vous pouvez également appeler `EndDialog` à partir de votre propre code. Pour plus d’informations, consultez la [EndDialog](../mfc/reference/cdialog-class.md#enddialog) fonction membre de classe `CDialog` dans les *référence MFC*.  
  
 Pour réorganiser pour la fermeture et la suppression d’une boîte de dialogue non modale, vous devez substituer `PostNcDestroy` et appeler le **supprimer** opérateur sur le **cela** pointeur. [Destruction de la boîte de dialogue](../mfc/destroying-the-dialog-box.md) explique les étapes suivantes.  
  
## <a name="see-also"></a>Voir aussi  
 [Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)

