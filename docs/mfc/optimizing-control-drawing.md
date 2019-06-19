---
title: Optimisation du contrôle de dessin
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 29ff985d-9bf5-4678-b62d-aad12def75fb
ms.openlocfilehash: 354ec1678747be57d387673f2611d526df8dfb47
ms.sourcegitcommit: 0ad35b26e405bbde17dc0bd0141e72f78f0a38fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67194736"
---
# <a name="optimizing-control-drawing"></a>Optimisation du contrôle de dessin

Lorsqu’un contrôle reçoit l’instruction de se dessiner lui-même dans un contexte de périphérique fourni au conteneur, en général, sélectionne les objets GDI (par exemple, les stylets, pinceaux et polices) dans le contexte de périphérique, effectue les opérations de dessin et restaure les objets GDI précédents. Si le conteneur comporte plusieurs contrôles qui doivent être dessinés dans le même contexte de périphérique, et chaque contrôle sélectionne les objets GDI qu'il requiert, temps peuvent être enregistré si les contrôles ne restaurent pas individuellement les objets précédemment sélectionnés. Une fois que tous les contrôles sont dessinés, le conteneur peut restaurer automatiquement les objets d’origine.

Pour détecter si un conteneur prend en charge cette technique, un contrôle peut appeler le [fonction membre COleControl::IsOptimizedDraw](../mfc/reference/colecontrol-class.md#isoptimizeddraw) fonction membre. Si cette fonction retourne **TRUE**, le contrôle peut ignorer l’étape normale de restauration des objets précédemment sélectionnés.

Considérez un contrôle qui a ce qui suit (non optimisé) `OnDraw` (fonction) :

[!code-cpp[NVC_MFC_AxOpt#15](../mfc/codesnippet/cpp/optimizing-control-drawing_1.cpp)]

Le stylet et le pinceau dans cet exemple sont des variables locales, ce qui signifie que leurs destructeurs sont appelées quand ils sont hors de portée (lorsque le `OnDraw` fonction se termine). Les destructeurs tente de supprimer les objets GDI correspondants. Mais ne doivent pas être supprimées si vous envisagez de les laisser sélectionnés dans le contexte de périphérique après le retour de `OnDraw`.

Pour empêcher le [CPen](../mfc/reference/cpen-class.md) et [CBrush](../mfc/reference/cbrush-class.md) objets d’être détruits lorsque `OnDraw` se termine, les stocker dans des variables de membre au lieu de variables locales. Dans la déclaration de classe du contrôle, ajoutez les déclarations de deux nouvelles variables de membre :

[!code-cpp[NVC_MFC_AxOpt#16](../mfc/codesnippet/cpp/optimizing-control-drawing_2.h)]
[!code-cpp[NVC_MFC_AxOpt#17](../mfc/codesnippet/cpp/optimizing-control-drawing_3.h)]

Ensuite, le `OnDraw` fonction peut être réécrit comme suit :

[!code-cpp[NVC_MFC_AxOpt#18](../mfc/codesnippet/cpp/optimizing-control-drawing_4.cpp)]

Cette approche évite la création du stylo et pinceau chaque fois `OnDraw` est appelée. L’amélioration de la vitesse vient au détriment de la gestion des données d’instance supplémentaires.

Si la propriété ForeColor ou BackColor change, le stylet ou un pinceau doit être recréée. Pour ce faire, vous devez remplacer le [fonctions membres OnForeColorChanged](../mfc/reference/colecontrol-class.md#onforecolorchanged) et [OnBackColorChanged](../mfc/reference/colecontrol-class.md#onbackcolorchanged) fonctions membres :

[!code-cpp[NVC_MFC_AxOpt#19](../mfc/codesnippet/cpp/optimizing-control-drawing_5.cpp)]

Enfin, pour éliminer inutiles `SelectObject` appels, modifier `OnDraw` comme suit :

[!code-cpp[NVC_MFC_AxOpt#20](../mfc/codesnippet/cpp/optimizing-control-drawing_6.cpp)]

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC : Optimisation](../mfc/mfc-activex-controls-optimization.md)<br/>
[COleControl, classe](../mfc/reference/colecontrol-class.md)<br/>
[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Contrôle ActiveX MFC, Assistant](../mfc/reference/mfc-activex-control-wizard.md)<br/>
[Contrôles ActiveX MFC : Peinture d’un contrôle ActiveX](../mfc/mfc-activex-controls-painting-an-activex-control.md)
