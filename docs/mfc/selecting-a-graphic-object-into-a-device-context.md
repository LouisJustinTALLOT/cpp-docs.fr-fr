---
description: 'En savoir plus sur : sélection d’un objet graphique dans un contexte de périphérique'
title: Sélection d'un objet graphique dans un contexte de périphérique
ms.date: 11/04/2016
helpviewer_keywords:
- graphic objects [MFC], selecting into device context
- SelectObject method [MFC]
- GDI objects [MFC], device contexts
- lifetime, graphic objects [MFC]
- device contexts, selecting graphic objects into
- device contexts, graphic objects [MFC]
ms.assetid: cf54a330-63ef-421f-83eb-90ec7bd82eef
ms.openlocfilehash: cc2aabbcb1614fc77e5eadf9e6fba13ba377a4c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217677"
---
# <a name="selecting-a-graphic-object-into-a-device-context"></a>Sélection d'un objet graphique dans un contexte de périphérique

Cette rubrique s’applique à l’utilisation d’objets graphiques dans le contexte de périphérique d’une fenêtre. Après avoir [créé un objet de dessin](../mfc/one-stage-and-two-stage-construction-of-objects.md), vous devez le sélectionner dans le contexte de périphérique à la place de l’objet par défaut qui y est stocké :

[!code-cpp[NVC_MFCDocViewSDI#7](../mfc/codesnippet/cpp/selecting-a-graphic-object-into-a-device-context_1.cpp)]

## <a name="lifetime-of-graphic-objects"></a>Durée de vie des objets graphiques

L’objet graphique retourné par [SelectObject](../mfc/reference/cdc-class.md#selectobject) est « Temporary ». Autrement dit, il sera supprimé par la fonction membre [OnIdle](../mfc/reference/cwinapp-class.md#onidle) de la classe lors de `CWinApp` la prochaine durée d’inactivité du programme. Tant que vous utilisez l’objet retourné par `SelectObject` dans une fonction unique sans retourner le contrôle à la boucle de message principale, vous n’avez aucun problème.

### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Objets graphiques](../mfc/graphic-objects.md)

- [Construction d'objets graphiques en une ou deux étapes](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Contextes de périphérique](../mfc/device-contexts.md)

- [Dessin dans une vue](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>Voir aussi

[Objets graphiques](../mfc/graphic-objects.md)
