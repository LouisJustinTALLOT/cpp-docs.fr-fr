---
title: Dessin dans une vue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- drawing [MFC], in views
- views [MFC], printing
- views [MFC], updating
- printing [MFC], views
- views [MFC], rendering
- printing views [MFC]
- paint messages in view class [MFC]
- device contexts, screen drawings
ms.assetid: e3761db6-0f19-4482-a4cd-ac38ef7c4d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc716800c35aa922f7912f586d6e5b8429593615
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346163"
---
# <a name="drawing-in-a-view"></a>Dessin dans une vue
La quasi-totalité de dessin dans votre application se produit dans la vue `OnDraw` fonction membre, que vous devez remplacer dans votre classe d’affichage. (L’exception est la souris de dessin, présentés dans [interprétation entrée via une vue utilisateur](../mfc/interpreting-user-input-through-a-view.md).) Votre `OnDraw` remplacer :  
  
1.  Obtient les données en appelant des fonctions membres que vous fournissez le document.  
  
2.  Affiche les données en appelant les fonctions membres d’un objet de contexte de périphérique que l’infrastructure transmet à `OnDraw`.  
  
 Lorsque les données d’un document changent d’une certaine façon, la vue doit être redessinée pour refléter les modifications. En règle générale, cela se produit lorsque l’utilisateur effectue une modification via une vue sur le document. Dans ce cas, la vue appelle du document [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) fonction membre pour avertir toutes les vues du même document se mettre à jour. `UpdateAllViews` appelle chaque vue [OnUpdate](../mfc/reference/cview-class.md#onupdate) fonction membre. L’implémentation par défaut de `OnUpdate` invalide la zone cliente de la vue. Vous pouvez substituer pour invalider les régions de la zone cliente correspondant aux parties modifiées du document.  
  
 Le `UpdateAllViews` fonction membre de classe **CDocument** et `OnUpdate` fonction membre de classe `CView` permettent de passer des informations qui décrivent les parties du document ont été modifiés. Ce mécanisme « indicateur » vous permet de limiter la zone de la vue doit redessiner. `OnUpdate` accepte deux arguments « indicateur ». La première, `lHint`, de type **LPARAM**, vous permet de transmettre toutes les données de votre choix, tandis que le second, `pHint`, de type `CObject`*, vous permet de passer un pointeur à n’importe quel objet dérivé de `CObject`.  
  
 Lorsqu’une devient non valide, Windows envoie une `WM_PAINT` message. La vue [OnPaint](../mfc/reference/cwnd-class.md#onpaint) fonction gestionnaire répond au message en créant un objet de contexte de périphérique de la classe [CPaintDC](../mfc/reference/cpaintdc-class.md) et appels de votre vue `OnDraw` fonction membre. Il est généralement inutile d’écrire une substitution `OnPaint` fonction gestionnaire.  
  
 A [contexte de périphérique](../mfc/device-contexts.md) est une structure de données de Windows qui contient des informations sur les attributs de dessin d’un périphérique tel qu’un écran ou une imprimante. Tous les appels de dessin sont effectués via un objet de contexte de périphérique. Pour dessiner sur l’écran, `OnDraw` est passé un `CPaintDC` objet. Pour dessiner sur une imprimante, il est passé un [CDC](../mfc/reference/cdc-class.md) objet définies pour l’imprimante en cours.  
  
 Tout d’abord votre code de dessin dans la vue récupère un pointeur vers le document, puis effectue des appels de dessin via le contexte de périphérique. Le simple suivant `OnDraw` exemple illustre le processus :  
  
 [!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/cpp/drawing-in-a-view_1.cpp)]  
  
 Dans cet exemple, vous définissez le `GetData` fonctionner en tant que membre de votre classe de document dérivée.  
  
 L’exemple imprime toute chaîne à partir du document, centré dans la vue. Si le `OnDraw` appel est pour le dessin de l’écran, la `CDC` objet passé dans `pDC` est un `CPaintDC` dont le constructeur a déjà été appelée `BeginPaint`. Les appels aux fonctions de dessin sont effectués via le pointeur de contexte de périphérique. Pour plus d’informations sur les contextes de périphérique et les appels de dessin, consultez la classe [CDC](../mfc/reference/cdc-class.md) dans les *référence MFC* et [utilisation des objets de la fenêtre](../mfc/working-with-window-objects.md).  
  
 Pour plus d’exemples illustrant l’écriture `OnDraw`, consultez la [exemples MFC](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de vues](../mfc/using-views.md)

