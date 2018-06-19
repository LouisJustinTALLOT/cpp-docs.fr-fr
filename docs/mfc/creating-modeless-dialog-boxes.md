---
title: Création de boîtes de dialogue non modale | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2055312c7418b14c9b274649db8faa297554257e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340991"
---
# <a name="creating-modeless-dialog-boxes"></a>Création de boîtes de dialogue non modales
Pour une boîte de dialogue non modale, vous devez fournir votre propre constructeur public dans votre classe de boîte de dialogue. Pour créer une boîte de dialogue non modale, appelez votre constructeur public, puis l’objet de boîte de dialogue [créer](../mfc/reference/cdialog-class.md#create) fonction membre pour charger la ressource de boîte de dialogue. Vous pouvez appeler **créer** pendant ou après l’appel de constructeur. Si la ressource de boîte de dialogue a la propriété **WS_VISIBLE**, la boîte de dialogue apparaît immédiatement. Si non, vous devez appeler sa [ShowWindow](../mfc/reference/cwnd-class.md#showwindow) fonction membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)

