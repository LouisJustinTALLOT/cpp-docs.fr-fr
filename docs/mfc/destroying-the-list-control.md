---
title: Destruction du contrôle de liste
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
ms.openlocfilehash: d128a613a2a4cb595f362f843a5ae2eba830e538
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621900"
---
# <a name="destroying-the-list-control"></a>Destruction du contrôle de liste

Si vous incorporez votre objet [CListCtrl](reference/clistctrl-class.md) en tant que membre de données d’une classe d’affichage ou de boîte de dialogue, il est détruit lorsque son propriétaire est détruit. Si vous utilisez un [CListView](reference/clistview-class.md), le Framework détruit le contrôle lorsqu’il détruit la vue.

Si vous configurez une partie de vos données de liste pour qu’elles soient stockées dans l’application plutôt que dans le contrôle de liste, vous devez disposer de sa désallocation. Pour plus d’informations, consultez [éléments de rappel et masque de rappel](/windows/win32/Controls/using-list-view-controls) dans le SDK Windows.

En outre, vous êtes responsable de la désallocation des listes d’images que vous avez créées et associées à l’objet de contrôle de liste.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](using-clistctrl.md)<br/>
[Commandes](controls-mfc.md)
