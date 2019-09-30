---
title: Création de boîtes de dialogue non modales
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
ms.openlocfilehash: 7da6d82257d1407dfcf4d6d3c15cdadbb8c0fa30
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685664"
---
# <a name="creating-modeless-dialog-boxes"></a>Création de boîtes de dialogue non modales

Pour une boîte de dialogue non modale, vous devez fournir votre propre constructeur public dans votre classe de boîte de dialogue. Pour créer une boîte de dialogue non modale, appelez votre constructeur public, puis appelez la fonction membre [Create](../mfc/reference/cdialog-class.md#create) de l’objet Dialog pour charger la ressource de boîte de dialogue. Vous pouvez appeler **Create** pendant ou après l’appel de constructeur. Si la propriété de la ressource de boîte de dialogue est **WS_VISIBLE**, la boîte de dialogue apparaît immédiatement. Si ce n’est pas le cas, vous devez appeler sa fonction membre [ShowWindow](../mfc/reference/cwnd-class.md#showwindow) .

## <a name="see-also"></a>Voir aussi

[Utilisation des boîtes de dialogue dans MFC](../mfc/life-cycle-of-a-dialog-box.md)
