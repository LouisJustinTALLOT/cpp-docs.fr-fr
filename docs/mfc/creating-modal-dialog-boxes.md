---
title: Création de boîtes de dialogue modales
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: ed0fe3b7ef8aeddea01f573bfe8e1c01a6b5b443
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685677"
---
# <a name="creating-modal-dialog-boxes"></a>Création de boîtes de dialogue modales

Pour créer une boîte de dialogue modale, appelez l’un des deux constructeurs publics déclarés dans [CDialog](../mfc/reference/cdialog-class.md). Ensuite, appelez la fonction membre [DoModal](../mfc/reference/cdialog-class.md#domodal) de l’objet Dialog pour afficher la boîte de dialogue et gérer l’interaction avec celle-ci jusqu’à ce que l’utilisateur choisisse OK ou annuler. Cette gestion par `DoModal` est ce qui rend la boîte de dialogue modale. Pour les boîtes de dialogue modales, `DoModal` charge la ressource de boîte de dialogue.

## <a name="see-also"></a>Voir aussi

[Utilisation des boîtes de dialogue dans MFC](../mfc/life-cycle-of-a-dialog-box.md)
