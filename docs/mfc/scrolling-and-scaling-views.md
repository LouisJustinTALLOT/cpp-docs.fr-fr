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
ms.openlocfilehash: 7064880c5ceef8e7dc3e35bb7ef5bc700b0842d2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511231"
---
# <a name="scrolling-and-scaling-views"></a>Défilement et mise à l'échelle des vues

MFC prend en charge les vues qui défilent et les vues qui sont mises à l’échelle automatiquement à la taille de la fenêtre frame qui les affiche. La `CScrollView` classe prend en charge les deux types de vues.

Pour plus d’informations sur le défilement et la mise à l’échelle, consultez la classe [CScrollView](../mfc/reference/cscrollview-class.md) dans la *référence MFC*. Pour obtenir un exemple de défilement, consultez l' [exemple SCRIBBLE](../overview/visual-cpp-samples.md).

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- Défilement d’une vue

- Mise à l’échelle d’une vue

- [Afficher les coordonnées](/windows/win32/gdi/window-coordinate-system)

##  <a name="_core_scrolling_a_view"></a>Défilement d’une vue

Souvent, la taille d’un document est supérieure à la taille que sa vue peut afficher. Cela peut se produire lorsque les données du document augmentent ou lorsque l’utilisateur réduit la fenêtre qui encadre la vue. Dans ce cas, la vue doit prendre en charge le défilement.

Toute vue peut gérer les messages de la barre de `OnHScroll` défilement `OnVScroll` dans ses fonctions membres et. Vous pouvez implémenter la gestion des messages de la barre de défilement dans ces fonctions, en faisant tout le travail vous- `CScrollView` même, ou vous pouvez utiliser la classe pour gérer le défilement pour vous.

`CScrollView` effectue les actions suivantes :

- Gère les tailles et les modes de mappage des fenêtres et des Viewports

- Fait défiler automatiquement en réponse aux messages de la barre de défilement

Vous pouvez spécifier la quantité de défilement pour une «page» (quand l’utilisateur clique dans un arbre de barre de défilement) et une «ligne» (lorsque l’utilisateur clique sur une flèche de défilement). Planifiez ces valeurs pour les adapter à la nature de votre vue. Par exemple, vous souhaiterez peut-être faire défiler des incréments de 1 pixel pour une vue graphique, mais par incréments en fonction de la hauteur de ligne dans les documents texte.

##  <a name="_core_scaling_a_view"></a>Mise à l’échelle d’une vue

Lorsque vous souhaitez que la vue s’ajuste automatiquement à la taille de sa fenêtre frame, `CScrollView` vous pouvez utiliser pour la mise à l’échelle au lieu de la faire défiler. La vue logique est étirée ou rétrécie pour s’adapter exactement à la zone cliente de la fenêtre. Une vue mise à l’échelle n’a pas de barres de défilement.

## <a name="see-also"></a>Voir aussi

[Utilisation de vues](../mfc/using-views.md)
