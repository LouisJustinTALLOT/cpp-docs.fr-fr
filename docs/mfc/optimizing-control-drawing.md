---
title: Optimisation du contrôle de dessin | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 29ff985d-9bf5-4678-b62d-aad12def75fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8103e1e342756f9b715c1a0959ed256403e130bf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351292"
---
# <a name="optimizing-control-drawing"></a>Optimisation du contrôle de dessin
Lorsqu’un contrôle est demandé à dessiner lui-même dans un contexte de périphérique de fourni par le conteneur, en général, sélectionne les objets GDI (par exemple, des stylets, pinceaux et polices) dans le contexte de périphérique, effectue les opérations de dessin et restaure les objets GDI précédents. Si le conteneur comporte plusieurs contrôles qui doivent être dessinés dans le même contexte de périphérique, et chaque contrôle sélectionne les objets GDI, qu'il a besoin, temps peuvent être enregistré si les contrôles ne restaurent pas individuellement les objets sélectionnés précédemment. Une fois que tous les contrôles sont dessinés, le conteneur peut restaurer automatiquement les objets d’origine.  
  
 Pour détecter si un conteneur prend en charge cette technique, un contrôle peut appeler le [fonction membre COleControl::IsOptimizedDraw](../mfc/reference/colecontrol-class.md#isoptimizeddraw) fonction membre. Si cette fonction retourne **TRUE**, le contrôle peut ignorer l’étape normale de restauration des objets précédemment sélectionnés.  
  
 Prenons un contrôle qui est les suivantes (non optimisés) `OnDraw` (fonction) :  
  
 [!code-cpp[NVC_MFC_AxOpt#15](../mfc/codesnippet/cpp/optimizing-control-drawing_1.cpp)]  
  
 Le stylet et le pinceau dans cet exemple sont des variables locales, ce qui signifie que leurs destructeurs sont appelés quand ils sont hors de portée (lorsque le `OnDraw` fonction se termine). Les destructeurs va tenter de supprimer les objets GDI correspondants. Mais ils ne doivent pas être supprimés si vous envisagez de les laisser sélectionnés dans le contexte de périphérique lors du retour de `OnDraw`.  
  
 Pour empêcher le [CPen](../mfc/reference/cpen-class.md) et [CBrush](../mfc/reference/cbrush-class.md) les objets d’être détruits lorsque `OnDraw` se termine, les stocker dans des variables de membre au lieu de variables locales. Dans la déclaration de classe du contrôle, ajoutez les déclarations de deux nouvelles variables membres :  
  
 [!code-cpp[NVC_MFC_AxOpt#16](../mfc/codesnippet/cpp/optimizing-control-drawing_2.h)]  
[!code-cpp[NVC_MFC_AxOpt#17](../mfc/codesnippet/cpp/optimizing-control-drawing_3.h)]  
  
 Ensuite, la `OnDraw` fonction peut être réécrit comme suit :  
  
 [!code-cpp[NVC_MFC_AxOpt#18](../mfc/codesnippet/cpp/optimizing-control-drawing_4.cpp)]  
  
 Cette approche évite la création du stylet et de pinceau chaque fois `OnDraw` est appelée. L’amélioration de la vitesse se fait au prix de la gestion des données d’instance supplémentaires.  
  
 Si la propriété ForeColor ou BackColor est modifiée, le stylet ou un pinceau doit être créé à nouveau. Pour ce faire, vous devez remplacer le [fonctions membres OnForeColorChanged](../mfc/reference/colecontrol-class.md#onforecolorchanged) et [OnBackColorChanged](../mfc/reference/colecontrol-class.md#onbackcolorchanged) fonctions membres :  
  
 [!code-cpp[NVC_MFC_AxOpt#19](../mfc/codesnippet/cpp/optimizing-control-drawing_5.cpp)]  
  
 Enfin, pour éliminer inutiles `SelectObject` des appels, modifier `OnDraw` comme suit :  
  
 [!code-cpp[NVC_MFC_AxOpt#20](../mfc/codesnippet/cpp/optimizing-control-drawing_6.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC : optimisation](../mfc/mfc-activex-controls-optimization.md)   
 [COleControl (classe)](../mfc/reference/colecontrol-class.md)   
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Assistant contrôle ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md)   
 [Contrôles ActiveX MFC : peinture d’un contrôle ActiveX](../mfc/mfc-activex-controls-painting-an-activex-control.md)

