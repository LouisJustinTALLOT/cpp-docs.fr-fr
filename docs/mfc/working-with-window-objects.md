---
title: Utilisation des objets de fenêtre | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- child windows [MFC], working with
- window objects [MFC], working with
ms.assetid: f73aa254-90e3-46a9-8e9b-d78b7054a331
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 55f3eae10954ee2da1386907f88ae8b594dc8e53
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413627"
---
# <a name="working-with-window-objects"></a>Utilisation d'objets fenêtres

Utilisation des appels de windows pour les deux types d’activité :

- Gestion des messages de Windows

- Dans la fenêtre de dessin

Pour gérer les messages Windows dans n’importe quelle fenêtre, y compris vos propres fenêtres enfants, consultez [mappage des Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md) pour mapper les messages à votre classe de fenêtre C++. Puis écrire du Gestionnaire de messages fonctions membres dans votre classe.

La plupart des dessin dans une application framework se produit dans la vue, dont [OnDraw](../mfc/reference/cview-class.md#ondraw) fonction membre est appelée chaque fois que le contenu de la fenêtre doit être dessiné. Si votre fenêtre est un enfant de la vue, vous pouvez déléguer certaines de dessin de la vue à votre fenêtre enfant en demandant à `OnDraw` appelez une des fonctions de membres de votre fenêtre.

Dans tous les cas, vous devez un contexte de périphérique pour le dessin. Vous pouvez utiliser le stylet, pinceau et autres objets graphiques contenus dans le contexte de périphérique associé à votre fenêtre. Ou vous pouvez modifier ces objets pour obtenir les effets de dessins que vous avez besoin. Votre contexte de périphérique défini que vous le souhaitez, appelez membre les fonctions de classe [CDC](../mfc/reference/cdc-class.md) (classe contexte de périphérique) pour dessiner des lignes, formes et du texte ; à utiliser des couleurs ; et pour travailler avec un système de coordonnées.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Mappage et gestion des messages](../mfc/message-handling-and-mapping.md)

- [Dessin dans une vue](../mfc/drawing-in-a-view.md)

- [Contextes de périphérique](../mfc/device-contexts.md)

- [Objets graphiques](../mfc/graphic-objects.md)

## <a name="see-also"></a>Voir aussi

[Objets fenêtre](../mfc/window-objects.md)

