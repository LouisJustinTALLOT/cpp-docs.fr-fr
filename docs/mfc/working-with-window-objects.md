---
title: "Utilisation des objets de la fenêtre | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- child windows [MFC], working with
- window objects [MFC], working with
ms.assetid: f73aa254-90e3-46a9-8e9b-d78b7054a331
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1eb8622c18a9b9539388ad2b3162916288cb28af
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="working-with-window-objects"></a>Utilisation d'objets fenêtres
Utilisation des appels de windows pour les deux types d’activité :  
  
-   Gestion des messages Windows  
  
-   Dessin dans la fenêtre  
  
 Pour traiter les messages Windows dans n’importe quelle fenêtre, y compris vos propres fenêtres enfants, consultez [mappage de Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md) pour mapper les messages à votre classe de fenêtre C++. Puis, écrivez Gestionnaire de messages des fonctions membres dans votre classe.  
  
 La plupart de dessin dans une infrastructure d’application se produit dans la vue, dont [OnDraw](../mfc/reference/cview-class.md#ondraw) fonction membre est appelée chaque fois que le contenu de la fenêtre doit être dessiné. Si votre fenêtre est un enfant de la vue, vous pouvez déléguer certaines de dessin de la vue à votre fenêtre enfant en ayant `OnDraw` appeler l’une des fonctions de membre de votre fenêtre.  
  
 Dans tous les cas, vous devez un contexte de périphérique pour le dessin. Vous pouvez utiliser le stylet, pinceau et autres objets graphiques contenus dans le contexte de périphérique associé à votre fenêtre. Ou vous pouvez modifier ces objets pour obtenir les effets de dessin que vous avez besoin. Avec votre contexte de périphérique défini comme vous le souhaitez, appeler fonctions membres de classe [CDC](../mfc/reference/cdc-class.md) (classe contexte de périphérique) pour dessiner des lignes, des formes et du texte ; pour utiliser des couleurs ; et pour travailler avec un système de coordonnées.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Mappage et la gestion des messages](../mfc/message-handling-and-mapping.md)  
  
-   [Dessin dans une vue](../mfc/drawing-in-a-view.md)  
  
-   [Contextes de périphérique](../mfc/device-contexts.md)  
  
-   [Objets graphiques](../mfc/graphic-objects.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Objets fenêtre](../mfc/window-objects.md)

