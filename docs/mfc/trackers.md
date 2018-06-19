---
title: Dispositifs de suivi | Documents Microsoft
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
ms.openlocfilehash: 6f0a0cc52e3a5150702af4acd293def38df758fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381535"
---
# <a name="trackers"></a>Dispositifs de suivi
Le [CRectTracker](../mfc/reference/crecttracker-class.md) classe fournit une interface utilisateur entre des éléments rectangulaires dans votre application et votre utilisateur en fournissant un ensemble de styles d’affichage. Ces styles comprennent des bordures continues, hachurées ou en pointillés ; un motif hachuré qui recouvre l’élément ; et les poignées de redimensionnement qui peuvent se trouve à l’extérieur ou à l’intérieur d’une bordure. Dispositifs de suivi sont souvent utilisés conjointement avec les éléments OLE, c'est-à-dire, les objets dérivés de `COleClientItem`. Les rectangles du dispositif de suivi donnent des indications sur l’état actuel de l’élément.  
  
 L’exemple OLE MFC [OCLIENT](../visual-cpp-samples.md) montre une interface commune à l’aide de dispositifs de suivi et des éléments du client OLE à partir du point de vue d’une application conteneur. Pour une démonstration des différents styles et les capacités d’un objet de mise hors tension, consultez l’exemple général MFC [mise hors tension](../visual-cpp-samples.md).  
  
 Pour plus d’informations sur l’implémentation de dispositifs de suivi dans votre application OLE, consultez [dispositifs de suivi : implémentation de dispositifs de suivi dans votre Application OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)  
  
## <a name="see-also"></a>Voir aussi  
 [OLE](../mfc/ole-in-mfc.md)   
 [COleClientItem, classe](../mfc/reference/coleclientitem-class.md)
