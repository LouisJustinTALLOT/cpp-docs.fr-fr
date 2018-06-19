---
title: Destruction du contrôle de liste | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: edb26671ba775cfa7daf98d39c7eccc9fd4111bd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343280"
---
# <a name="destroying-the-list-control"></a>Destruction du contrôle de liste
Si vous incorporez votre [CListCtrl](../mfc/reference/clistctrl-class.md) de l’objet en un membre de données d’une classe de vue ou de la boîte de dialogue, il est détruit lorsque son propriétaire est détruit. Si vous utilisez un [CListView](../mfc/reference/clistview-class.md), l’infrastructure détruit le contrôle lorsqu’elle détruit l’affichage.  
  
 Si vous réorganisez pour certaines de vos données de liste à stocker dans l’application plutôt que le contrôle de liste, vous devrez prévoir leur désallocation. Pour plus d’informations, consultez [éléments de rappel et masque de rappel](http://msdn.microsoft.com/library/windows/desktop/bb774736) dans le Kit de développement logiciel Windows.  
  
 En outre, vous êtes responsable de la désallocation des listes d’images vous avez créé et associé à l’objet de contrôle de liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CListCtrl](../mfc/using-clistctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

