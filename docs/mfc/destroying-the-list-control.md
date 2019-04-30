---
title: Destruction du contrôle de liste
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
ms.openlocfilehash: 963da9e6db2f0fe063dee1ca19ab23f545ed5e76
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392883"
---
# <a name="destroying-the-list-control"></a>Destruction du contrôle de liste

Si vous incorporez votre [CListCtrl](../mfc/reference/clistctrl-class.md) de l’objet en tant que données membre d’une classe de vue ou de la boîte de dialogue, il est détruit lorsque son propriétaire est détruit. Si vous utilisez un [CListView](../mfc/reference/clistview-class.md), l’infrastructure détruit le contrôle lorsqu’il détruit la vue.

Si vous réorganisez pour certaines de vos données de liste à stocker dans l’application plutôt que le contrôle de liste, vous devez faire en sorte que sa désallocation. Pour plus d’informations, consultez [éléments de rappel et masque de rappel](/windows/desktop/Controls/using-list-view-controls) dans le SDK Windows.

En outre, vous êtes responsable de la désallocation des listes d’images vous avez créé et associé à l’objet de contrôle de liste.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
