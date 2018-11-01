---
title: Dispositifs de suivi
ms.date: 11/04/2016
helpviewer_keywords:
- trackers [MFC]
- OLE applications [MFC], trackers
- applications [OLE], trackers
- tracking OLE items [MFC]
- OLE containers [MFC], trackers
- CDC class [MFC], trackers
- CRectTracker class [MFC], implementing trackers
- OLE server applications [MFC], trackers
ms.assetid: dcd09399-6637-4621-80e5-d12670429787
ms.openlocfilehash: 74e70f989d3803b11f05150f9b55c6dfe79ed876
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481950"
---
# <a name="trackers"></a>Dispositifs de suivi

Le [CRectTracker](../mfc/reference/crecttracker-class.md) classe fournit une interface utilisateur entre des éléments rectangulaires dans votre application et votre utilisateur en fournissant un ensemble de styles d’affichage. Ces styles comprennent des bordures pleine, hachurées ou en pointillés ; un motif hachuré qui recouvre l’élément ; et les poignées de redimensionnement qui peuvent se trouve à l’extérieur ou à l’intérieur d’une bordure. Dispositifs de suivi sont souvent utilisés conjointement avec les éléments OLE, autrement dit, les objets dérivés de `COleClientItem`. Les rectangles de dispositif de suivi donnent des indications sur l’état actuel de l’élément.

L’exemple OLE MFC [OCLIENT](../visual-cpp-samples.md) montre une interface commune à l’aide de dispositifs de suivi et des éléments du client OLE à partir du point de vue d’une application conteneur. Pour une démonstration des différents styles et les capacités d’un objet de mise hors tension, consultez l’exemple général MFC [TRACKER](../visual-cpp-samples.md).

Pour plus d’informations sur l’implémentation de dispositifs de suivi dans votre application OLE, consultez [dispositifs de suivi : implémentation de dispositifs de suivi dans votre Application OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)

## <a name="see-also"></a>Voir aussi

[OLE](../mfc/ole-in-mfc.md)<br/>
[COleClientItem, classe](../mfc/reference/coleclientitem-class.md)
