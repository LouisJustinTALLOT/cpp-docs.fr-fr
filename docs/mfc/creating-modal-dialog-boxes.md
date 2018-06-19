---
title: Création de boîtes de dialogue modales | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2a8bc947dbaf9cecc680f3cdbd8e6b429d2bcd5f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342427"
---
# <a name="creating-modal-dialog-boxes"></a>Création de boîtes de dialogue modales
Pour créer une boîte de dialogue modale, appelez une des deux constructeurs publics déclarés dans [CDialog](../mfc/reference/cdialog-class.md). Ensuite, appelez l’objet de boîte de dialogue [DoModal](../mfc/reference/cdialog-class.md#domodal) fonction membre pour afficher la boîte de dialogue et gérer l’interaction avec elle jusqu'à ce que l’utilisateur choisisse OK ou sur Annuler. Cette gestion par `DoModal` est ce qui rend la boîte de dialogue modale. Pour les boîtes de dialogue modales, `DoModal` charge la ressource de boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)

