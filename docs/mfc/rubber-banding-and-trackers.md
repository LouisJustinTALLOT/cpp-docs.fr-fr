---
title: Bande élastique et dispositifs de suivi | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- trackers [MFC]
- CRectTracker class [MFC], implementing trackers
- OLE objects [MFC], selecting
- rubber banding [MFC]
- WM_LBUTTONDOWN [MFC]
ms.assetid: 0d0fa64c-6418-4baf-ab7f-2d16ca039230
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2b1b5b0a49fdb59417be04864c9d1ef5341f849
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379240"
---
# <a name="rubber-banding-and-trackers"></a>Bande élastique et dispositifs de suivi
Une autre fonctionnalité fournie avec les dispositifs de suivi est la sélection « élastique », qui permet à un utilisateur de sélectionner plusieurs éléments OLE en faisant glisser un rectangle de redimensionnement autour des éléments à sélectionner. Lorsque l’utilisateur relâche le bouton gauche de la souris, les éléments dans la région sélectionnée par l’utilisateur sont sélectionnés et peuvent être manipulées par l’utilisateur. Par exemple, l’utilisateur peut faire glisser la sélection dans une autre application conteneur.  
  
 Implémentation de cette fonctionnalité nécessite du code supplémentaire dans votre application `WM_LBUTTONDOWN` fonction gestionnaire.  
  
 L’exemple de code suivant implémente la sélection élastique et les fonctionnalités supplémentaires.  
  
 [!code-cpp[NVC_MFCOClient#6](../mfc/codesnippet/cpp/rubber-banding-and-trackers_1.cpp)]  
  
 Si vous souhaitez permettre une orientation réversible du dispositif de suivi pendant élastique, vous devez appeler [CRectTracker::TrackRubberBand](../mfc/reference/crecttracker-class.md#trackrubberband) avec le troisième paramètre défini sur **TRUE**. N’oubliez pas que ce qui permet d’orientation réversible parfois met [CRectTracker::m_rect](../mfc/reference/crecttracker-class.md#m_rect) à être inversée. Ce problème peut être corrigé par un appel à [CRect::NormalizeRect](../atl-mfc-shared/reference/crect-class.md#normalizerect).  
  
 Pour plus d’informations, consultez [éléments clients du conteneur](../mfc/containers-client-items.md) et [personnalisation de la fonction glisser- déposer](../mfc/drag-and-drop-customizing.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Dispositifs de suivi : Implémentation de dispositifs de suivi dans votre Application OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)   
 [CRectTracker, classe](../mfc/reference/crecttracker-class.md)
