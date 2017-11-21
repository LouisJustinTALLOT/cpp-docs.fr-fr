---
title: "Création de boîtes de dialogue non modale | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7c5a701f42b2707b957753c1f8a22640c7818d72
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="creating-modeless-dialog-boxes"></a>Création de boîtes de dialogue non modales
Pour une boîte de dialogue non modale, vous devez fournir votre propre constructeur public dans votre classe de boîte de dialogue. Pour créer une boîte de dialogue non modale, appelez votre constructeur public, puis l’objet de boîte de dialogue [créer](../mfc/reference/cdialog-class.md#create) fonction membre pour charger la ressource de boîte de dialogue. Vous pouvez appeler **créer** pendant ou après l’appel de constructeur. Si la ressource de boîte de dialogue a la propriété **WS_VISIBLE**, la boîte de dialogue apparaît immédiatement. Si non, vous devez appeler sa [ShowWindow](../mfc/reference/cwnd-class.md#showwindow) fonction membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)

