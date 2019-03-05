---
title: Création de boîtes de dialogue modales
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: 5de6eeb616f32c7b8829d827988a972e41658530
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304962"
---
# <a name="creating-modal-dialog-boxes"></a>Création de boîtes de dialogue modales

Pour créer une boîte de dialogue modale, appelez une des deux constructeurs publics déclarés dans [CDialog](../mfc/reference/cdialog-class.md). Ensuite, appelez l’objet de boîte de dialogue [DoModal](../mfc/reference/cdialog-class.md#domodal) fonction membre pour afficher la boîte de dialogue et gérer l’interaction avec elle jusqu'à ce que l’utilisateur choisisse OK ou annuler. Cette gestion par `DoModal` est ce qui rend la boîte de dialogue modale. Pour les boîtes de dialogue modales, `DoModal` charge la ressource de boîte de dialogue.

## <a name="see-also"></a>Voir aussi

[Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)
