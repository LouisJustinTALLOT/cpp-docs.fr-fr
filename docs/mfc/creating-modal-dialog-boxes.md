---
title: Création de boîtes de dialogue modales
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: ed7cc94982a46e542a5174d4d46b8013cc84ffa4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622979"
---
# <a name="creating-modal-dialog-boxes"></a>Création de boîtes de dialogue modales

Pour créer une boîte de dialogue modale, appelez l’un des deux constructeurs publics déclarés dans [CDialog](reference/cdialog-class.md). Ensuite, appelez la fonction membre [DoModal](reference/cdialog-class.md#domodal) de l’objet Dialog pour afficher la boîte de dialogue et gérer l’interaction avec celle-ci jusqu’à ce que l’utilisateur choisisse OK ou annuler. Cette gestion par `DoModal` est celle qui rend la boîte de dialogue modale. Pour les boîtes de dialogue modales, `DoModal` charge la ressource de boîte de dialogue.

## <a name="see-also"></a>Voir aussi

[Utilisation des boîtes de dialogue dans MFC](life-cycle-of-a-dialog-box.md)
