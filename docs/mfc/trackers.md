---
title: Traceurs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 414a7c19292e154af0b6365b766d865dca0a7dd3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439865"
---
# <a name="trackers"></a>Dispositifs de suivi

Le [CRectTracker](../mfc/reference/crecttracker-class.md) classe fournit une interface utilisateur entre des éléments rectangulaires dans votre application et votre utilisateur en fournissant un ensemble de styles d’affichage. Ces styles comprennent des bordures pleine, hachurées ou en pointillés ; un motif hachuré qui recouvre l’élément ; et les poignées de redimensionnement qui peuvent se trouve à l’extérieur ou à l’intérieur d’une bordure. Dispositifs de suivi sont souvent utilisés conjointement avec les éléments OLE, autrement dit, les objets dérivés de `COleClientItem`. Les rectangles de dispositif de suivi donnent des indications sur l’état actuel de l’élément.

L’exemple OLE MFC [OCLIENT](../visual-cpp-samples.md) montre une interface commune à l’aide de dispositifs de suivi et des éléments du client OLE à partir du point de vue d’une application conteneur. Pour une démonstration des différents styles et les capacités d’un objet de mise hors tension, consultez l’exemple général MFC [TRACKER](../visual-cpp-samples.md).

Pour plus d’informations sur l’implémentation de dispositifs de suivi dans votre application OLE, consultez [dispositifs de suivi : implémentation de dispositifs de suivi dans votre Application OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)

## <a name="see-also"></a>Voir aussi

[OLE](../mfc/ole-in-mfc.md)<br/>
[COleClientItem, classe](../mfc/reference/coleclientitem-class.md)
