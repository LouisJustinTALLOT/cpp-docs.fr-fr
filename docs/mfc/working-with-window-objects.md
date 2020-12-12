---
description: 'En savoir plus sur : utilisation des objets de fenêtre'
title: Utilisation d'objets fenêtres
ms.date: 11/04/2016
helpviewer_keywords:
- child windows [MFC], working with
- window objects [MFC], working with
ms.assetid: f73aa254-90e3-46a9-8e9b-d78b7054a331
ms.openlocfilehash: 4a8c6f2c40eadbfe53aa79683bea29847adf684f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172585"
---
# <a name="working-with-window-objects"></a>Utilisation d'objets fenêtres

Utilisation d’appels Windows pour deux types d’activité :

- Gestion des messages Windows

- Dessin dans la fenêtre

Pour gérer les messages Windows dans n’importe quelle fenêtre, y compris vos propres fenêtres enfants, consultez [mappage de messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md) pour mapper les messages à votre classe de fenêtre C++. Écrivez ensuite les fonctions membres du gestionnaire de messages dans votre classe.

La plupart des dessins dans une application de Framework se produisent dans la vue, dont la fonction membre [OnDraw](../mfc/reference/cview-class.md#ondraw) est appelée chaque fois que le contenu de la fenêtre doit être dessiné. Si votre fenêtre est un enfant de la vue, vous pouvez déléguer une partie du dessin de la vue à votre fenêtre enfant en `OnDraw` appelant l’une des fonctions membres de votre fenêtre.

Dans tous les cas, vous aurez besoin d’un contexte de périphérique pour le dessin. Vous pouvez utiliser le stylet, le pinceau et les autres objets graphiques contenus dans le contexte de périphérique associé à votre fenêtre. Vous pouvez aussi modifier ces objets pour récupérer les effets de dessin dont vous avez besoin. Une fois votre contexte de périphérique configuré comme vous le souhaitez, appelez les fonctions membres de la classe [CDC](../mfc/reference/cdc-class.md) (classe de contexte de périphérique) pour dessiner des lignes, des formes et du texte. pour utiliser des couleurs ; et pour utiliser un système de coordonnées.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Gestion et mappage des messages](../mfc/message-handling-and-mapping.md)

- [Dessiner dans un affichage](../mfc/drawing-in-a-view.md)

- [Contextes de périphérique](../mfc/device-contexts.md)

- [Objets graphiques](../mfc/graphic-objects.md)

## <a name="see-also"></a>Voir aussi

[Objets de fenêtre](../mfc/window-objects.md)
