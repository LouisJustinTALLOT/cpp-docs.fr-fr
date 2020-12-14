---
description: 'En savoir plus sur : les traceurs'
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
ms.openlocfilehash: e82766ecfabf2b5ebb0147b9f2c462f3b4460869
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264245"
---
# <a name="trackers"></a>Dispositifs de suivi

La classe [CRectTracker](../mfc/reference/crecttracker-class.md) fournit une interface utilisateur entre les éléments rectangulaires de votre application et votre utilisateur en fournissant divers styles d’affichage. Ces styles incluent des bordures pleines, hachurées ou en pointillés ; modèle hachuré qui couvre l’élément ; et redimensionnez les poignées qui peuvent se trouver à l’extérieur ou à l’intérieur d’une bordure. Les suivis sont souvent utilisés conjointement avec les éléments OLE, autrement dit, les objets dérivés de `COleClientItem` . Les rectangles du dispositif de suivi donnent des indications visuelles sur l’état actuel de l’élément.

L’exemple MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) illustre une interface commune utilisant des dispositifs de suivi et des éléments de client OLE du point de vue d’une application de conteneur. Pour une démonstration des différents styles et capacités d’un objet Tracker, consultez l’exemple de [suivi](../overview/visual-cpp-samples.md)général MFC.

Pour plus d’informations sur l’implémentation de dispositifs de suivi dans votre application OLE, consultez [traceurs : implémentation de dispositifs de suivi dans votre application OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)

## <a name="see-also"></a>Voir aussi

[OLE](../mfc/ole-in-mfc.md)<br/>
[COleClientItem (classe)](../mfc/reference/coleclientitem-class.md)
