---
title: Création de boîtes de dialogue non modales
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
ms.openlocfilehash: 71cca82e667ddbf5cfc4c2abb5880cd69c7fafae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388486"
---
# <a name="creating-modeless-dialog-boxes"></a>Création de boîtes de dialogue non modales

Pour une boîte de dialogue non modale, vous devez fournir votre propre constructeur public dans votre classe de boîte de dialogue. Pour créer une boîte de dialogue non modale, appelez votre constructeur public, puis l’objet de boîte de dialogue [créer](../mfc/reference/cdialog-class.md#create) fonction membre pour charger la ressource de boîte de dialogue. Vous pouvez appeler **créer** pendant ou après l’appel de constructeur. Si la ressource de boîte de dialogue a la propriété **WS_VISIBLE**, la boîte de dialogue apparaît immédiatement. Si non, vous devez appeler sa [ShowWindow](../mfc/reference/cwnd-class.md#showwindow) fonction membre.

## <a name="see-also"></a>Voir aussi

[Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)
