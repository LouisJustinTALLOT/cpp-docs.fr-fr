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
ms.openlocfilehash: b71eb0e5d46a790b01ec12f12043af783bdfcf27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62181631"
---
# <a name="trackers"></a>Dispositifs de suivi

Le [CRectTracker](../mfc/reference/crecttracker-class.md) classe fournit une interface utilisateur entre des éléments rectangulaires dans votre application et votre utilisateur en fournissant un ensemble de styles d’affichage. Ces styles comprennent des bordures pleine, hachurées ou en pointillés ; un motif hachuré qui recouvre l’élément ; et les poignées de redimensionnement qui peuvent se trouve à l’extérieur ou à l’intérieur d’une bordure. Dispositifs de suivi sont souvent utilisés conjointement avec les éléments OLE, autrement dit, les objets dérivés de `COleClientItem`. Les rectangles de dispositif de suivi donnent des indications sur l’état actuel de l’élément.

L’exemple OLE MFC [OCLIENT](../overview/visual-cpp-samples.md) montre une interface commune à l’aide de dispositifs de suivi et des éléments du client OLE à partir du point de vue d’une application conteneur. Pour une démonstration des différents styles et les capacités d’un objet de mise hors tension, consultez l’exemple général MFC [TRACKER](../overview/visual-cpp-samples.md).

Pour plus d’informations sur l’implémentation de dispositifs de suivi dans votre application OLE, consultez [dispositifs de suivi : Implémentation de dispositifs de suivi dans votre application OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)

## <a name="see-also"></a>Voir aussi

[OLE](../mfc/ole-in-mfc.md)<br/>
[COleClientItem, classe](../mfc/reference/coleclientitem-class.md)
