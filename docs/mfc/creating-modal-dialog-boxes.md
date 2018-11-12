---
title: Création de boîtes de dialogue modales
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: eb9aab7e8579fbbbfdf5d0f2dca9b6e6abea0066
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657337"
---
# <a name="creating-modal-dialog-boxes"></a>Création de boîtes de dialogue modales

Pour créer une boîte de dialogue modale, appelez une des deux constructeurs publics déclarés dans [CDialog](../mfc/reference/cdialog-class.md). Ensuite, appelez l’objet de boîte de dialogue [DoModal](../mfc/reference/cdialog-class.md#domodal) fonction membre pour afficher la boîte de dialogue et gérer l’interaction avec elle jusqu'à ce que l’utilisateur choisisse OK ou annuler. Cette gestion par `DoModal` est ce qui rend la boîte de dialogue modale. Pour les boîtes de dialogue modales, `DoModal` charge la ressource de boîte de dialogue.

## <a name="see-also"></a>Voir aussi

[Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)

