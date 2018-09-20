---
title: Sélection d’un objet graphique dans un contexte de périphérique | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- graphic objects [MFC], selecting into device context
- SelectObject method [MFC]
- GDI objects [MFC], device contexts
- lifetime, graphic objects [MFC]
- device contexts, selecting graphic objects into
- device contexts, graphic objects [MFC]
ms.assetid: cf54a330-63ef-421f-83eb-90ec7bd82eef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 406c4e7cd87b350f9317022dcf1821fa92ddf4af
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427665"
---
# <a name="selecting-a-graphic-object-into-a-device-context"></a>Sélection d'un objet graphique dans un contexte de périphérique

Cette rubrique s’applique à l’aide d’objets graphiques dans le contexte de périphérique d’une fenêtre. Après avoir [créer un objet de dessin](../mfc/one-stage-and-two-stage-construction-of-objects.md), vous devez le sélectionner dans le contexte de périphérique à la place de l’objet par défaut qu’il contient :

[!code-cpp[NVC_MFCDocViewSDI#7](../mfc/codesnippet/cpp/selecting-a-graphic-object-into-a-device-context_1.cpp)]

## <a name="lifetime-of-graphic-objects"></a>Durée de vie des objets graphiques

L’objet de graphique retourné par [SelectObject](../mfc/reference/cdc-class.md#selectobject) est « temporaire ». Autrement dit, il sera supprimé par le [OnIdle](../mfc/reference/cwinapp-class.md#onidle) fonction membre de classe `CWinApp` l’heure de la prochaine fois que le programme obtient inactif. Tant que vous utilisez l’objet retourné par `SelectObject` dans une fonction unique sans retourner le contrôle à la boucle de messages principale, vous n’aurez aucun problème.

### <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Objets graphiques](../mfc/graphic-objects.md)

- [Construction d’objets graphiques en une et en deux étapes](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Contextes de périphérique](../mfc/device-contexts.md)

- [Dessin dans une vue](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>Voir aussi

[Objets graphiques](../mfc/graphic-objects.md)

