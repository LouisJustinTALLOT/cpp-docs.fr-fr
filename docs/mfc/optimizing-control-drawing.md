---
description: 'En savoir plus sur : optimisation du dessin de contrôle'
title: Optimisation du contrôle de dessin
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 29ff985d-9bf5-4678-b62d-aad12def75fb
ms.openlocfilehash: 93e948d4a572f4e02c8676b2af1b6f8943004f26
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331807"
---
# <a name="optimizing-control-drawing"></a>Optimisation du contrôle de dessin

Lorsqu’un contrôle est chargé de se dessiner lui-même dans un contexte de périphérique fourni par un conteneur, il sélectionne généralement les objets GDI (tels que les stylets, les pinceaux et les polices) dans le contexte de périphérique, effectue ses opérations de dessin et restaure les objets GDI précédents. Si le conteneur a plusieurs contrôles qui doivent être dessinés dans le même contexte de périphérique et que chaque contrôle sélectionne les objets GDI dont il a besoin, l’heure peut être enregistrée si les contrôles ne restaurent pas individuellement les objets sélectionnés précédemment. Une fois que tous les contrôles ont été dessinés, le conteneur peut restaurer automatiquement les objets d’origine.

Pour détecter si un conteneur prend en charge cette technique, un contrôle peut appeler la fonction membre [COleControl :: IsOptimizedDraw](reference/colecontrol-class.md#isoptimizeddraw) . Si cette fonction retourne la **valeur true**, le contrôle peut ignorer l’étape normale de restauration des objets sélectionnés précédemment.

Prenons l’exemple d’un contrôle qui a la fonction (non optimisée) suivante `OnDraw` :

[!code-cpp[NVC_MFC_AxOpt#15](codesnippet/cpp/optimizing-control-drawing_1.cpp)]

Le stylet et le pinceau dans cet exemple sont des variables locales, ce qui signifie que leurs destructeurs sont appelés lorsqu’ils passent hors de portée (lorsque la `OnDraw` fonction se termine). Les destructeurs essaient de supprimer les objets GDI correspondants. Mais elles ne doivent pas être supprimées si vous envisagez de les conserver dans le contexte de périphérique lors du retour de `OnDraw` .

Pour empêcher que les objets [CPen](reference/cpen-class.md) et [CBrush](reference/cbrush-class.md) ne soient détruits lorsque se `OnDraw` termine, stockez-les dans des variables membres au lieu de variables locales. Dans la déclaration de classe du contrôle, ajoutez des déclarations pour deux nouvelles variables membres :

[!code-cpp[NVC_MFC_AxOpt#16](codesnippet/cpp/optimizing-control-drawing_2.h)]
[!code-cpp[NVC_MFC_AxOpt#17](codesnippet/cpp/optimizing-control-drawing_3.h)]

Ensuite, la `OnDraw` fonction peut être réécrite comme suit :

[!code-cpp[NVC_MFC_AxOpt#18](codesnippet/cpp/optimizing-control-drawing_4.cpp)]

Cette approche évite la création du stylet et du pinceau chaque fois que `OnDraw` est appelé. L’amélioration de la vitesse est le coût de la maintenance des données d’instance supplémentaires.

Si la propriété ForeColor ou BackColor change, le stylet ou le pinceau doit être recréé. Pour ce faire, remplacez les fonctions membres [OnForeColorChanged](reference/colecontrol-class.md#onforecolorchanged) et [OnBackColorChanged](reference/colecontrol-class.md#onbackcolorchanged) :

[!code-cpp[NVC_MFC_AxOpt#19](codesnippet/cpp/optimizing-control-drawing_5.cpp)]

Enfin, pour éliminer `SelectObject` les appels inutiles, modifiez `OnDraw` comme suit :

[!code-cpp[NVC_MFC_AxOpt#20](codesnippet/cpp/optimizing-control-drawing_6.cpp)]

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC : optimisation](mfc-activex-controls-optimization.md)<br/>
[Classe COleControl](reference/colecontrol-class.md)<br/>
[Contrôles ActiveX MFC](mfc-activex-controls.md)<br/>
[Assistant contrôle ActiveX MFC](reference/mfc-activex-control-wizard.md)<br/>
[Contrôles ActiveX MFC : peinture d’un contrôle ActiveX](mfc-activex-controls-painting-an-activex-control.md)
