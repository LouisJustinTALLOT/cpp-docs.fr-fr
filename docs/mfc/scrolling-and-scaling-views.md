---
title: Défilement et mise à l'échelle des vues
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- scaling views [MFC]
- message handling [MFC], scroll bars in view class [MFC]
- scroll bars [MFC], messages
- scrolling views [MFC]
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
ms.openlocfilehash: 2baa89f233eb6df93cde3adbde35ba1e6d35c093
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283707"
---
# <a name="scrolling-and-scaling-views"></a>Défilement et mise à l'échelle des vues

MFC prend en charge les vues qui défilent et des vues qui sont automatiquement mis à l’échelle à la taille de la fenêtre frame qui les affiche. Classe `CScrollView` prend en charge les deux types de vues.

Pour plus d’informations sur le défilement et mise à l’échelle, consultez la classe [CScrollView](../mfc/reference/cscrollview-class.md) dans le *référence MFC*. Pour obtenir un exemple de défilement, consultez le [exemple Scribble](../visual-cpp-samples.md).

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- Défilement d’une vue

- Mise à l’échelle d’une vue

- [Coordonnées de la vue](/windows/desktop/gdi/window-coordinate-system)

##  <a name="_core_scrolling_a_view"></a> Défilement d’une vue

Souvent, la taille d’un document est supérieure à la taille de qu'affichage de sa vue. Cela peut se produire, car les données du document augmentent ou l’utilisateur réduit la fenêtre frame de la vue. Dans ce cas, la vue doit prendre en charge le défilement.

N’importe quelle vue peut gérer les messages de barre de défilement dans son `OnHScroll` et `OnVScroll` fonctions membres. Vous pouvez soit implémenter barre de défilement la gestion des messages dans ces fonctions, fait tout le travail vous-même, ou vous pouvez utiliser la `CScrollView` classe pour gérer le défilement pour vous.

`CScrollView` effectue les actions suivantes :

- Gère les tailles de fenêtre et de la fenêtre d’affichage et les modes de mappage

- Fait défiler automatiquement en réponse aux messages de la barre de défilement

Vous pouvez spécifier combien défilement pour une « page » (lorsque l’utilisateur clique dans un arbre de la barre de défilement) et une « ligne » (lorsque l’utilisateur clique dans une flèche de défilement). Planifier ces valeurs en fonction de la nature de votre vue. Par exemple, vous pouvez souhaiter faire défiler les incréments de 1 pixel pour une vue graphique mais incréments en fonction de la hauteur de ligne dans les documents de texte.

##  <a name="_core_scaling_a_view"></a> Mise à l’échelle d’une vue

Lorsque vous souhaitez que l’affichage s’ajuste automatiquement à la taille de sa fenêtre frame, vous pouvez utiliser `CScrollView` pour la mise à l’échelle au lieu du défilement. La vue logique est étirée ou rétrécie pour correspondre exactement à la zone la fenêtre client. Une vue à l’échelle n’a aucune barre de défilement.

## <a name="see-also"></a>Voir aussi

[Utilisation de vues](../mfc/using-views.md)
