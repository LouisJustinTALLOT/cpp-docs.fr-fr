---
title: Défilement et mise à l’échelle des vues | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handlers [MFC]
- scaling views [MFC]
- message handling [MFC], scroll bars in view class [MFC]
- scroll bars [MFC], messages
- scrolling views [MFC]
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9758c63562a19d6b9e458fd434108a92bbc8576
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379266"
---
# <a name="scrolling-and-scaling-views"></a>Défilement et mise à l'échelle des vues
MFC prend en charge les vues qui défilent et des vues qui sont automatiquement mis à l’échelle à la taille de la fenêtre frame qui les affiche. Classe `CScrollView` prend en charge les deux types de vues.  
  
 Pour plus d’informations sur le défilement et mise à l’échelle, consultez la classe [CScrollView](../mfc/reference/cscrollview-class.md) dans les *référence MFC*. Pour obtenir un exemple de défilement, consultez le [exemple Scribble](../visual-cpp-samples.md).  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   Défilement d’une vue  
  
-   Mise à l’échelle d’une vue  
  
-   [Coordonnées de la vue](http://msdn.microsoft.com/library/windows/desktop/dd145205)  
  
##  <a name="_core_scrolling_a_view"></a> Défilement d’une vue  
 Souvent, la taille d’un document est supérieure à la taille de qu'affichage de sa vue. Cela peut se produire, car les données du document augmentent ou l’utilisateur réduit la fenêtre frame de la vue. Dans ce cas, la vue doit prendre en charge le défilement.  
  
 N’importe quelle vue peut gérer des messages de barre de défilement dans son `OnHScroll` et `OnVScroll` fonctions membres. Vous pouvez soit implémenter ScrollBar la gestion des messages dans ces fonctions, faites tout le travail vous-même, ou vous pouvez utiliser la `CScrollView` classe pour gérer le défilement pour vous.  
  
 `CScrollView` effectue les actions suivantes :  
  
-   Gère les tailles de fenêtre et la fenêtre d’affichage et les modes de mappage  
  
-   Fait défiler automatiquement en réponse aux messages de la barre de défilement  
  
 Vous pouvez spécifier combien défilement pour une « page » (lorsque l’utilisateur clique dans un arbre de la barre de défilement) et une « ligne » (lorsque l’utilisateur clique sur une flèche de défilement). Planifier ces valeurs en fonction de la nature de votre affichage. Par exemple, vous pouvez souhaiter faire défiler les incréments de 1 pixel pour une vue graphique mais incréments en fonction de la hauteur de ligne dans les documents de texte.  
  
##  <a name="_core_scaling_a_view"></a> Mise à l’échelle d’une vue  
 Lorsque vous souhaitez que l’affichage s’ajuste automatiquement à la taille de la fenêtre frame, vous pouvez utiliser `CScrollView` pour la mise à l’échelle au lieu de défilement. La vue logique est étirée ou rétrécie pour correspondre exactement à zone cliente de la fenêtre. Une vue à l’échelle n’a aucune barre de défilement.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de vues](../mfc/using-views.md)

