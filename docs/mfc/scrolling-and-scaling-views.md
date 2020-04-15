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
ms.openlocfilehash: 366f0e2953e5190f80a2877804bff2fc7dbbd520
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372786"
---
# <a name="scrolling-and-scaling-views"></a>Défilement et mise à l'échelle des vues

MFC prend en charge les vues qui font défiler et les vues qui sont automatiquement réduites à la taille de la fenêtre de cadre qui les affiche. La `CScrollView` classe prend en charge les deux types de points de vue.

Pour plus d’informations sur le défilement et la mise à l’échelle, voir classe [CScrollView](../mfc/reference/cscrollview-class.md) dans la *référence MFC*. Pour un exemple de défilement, voir [l’échantillon Scribble](../overview/visual-cpp-samples.md).

## <a name="what-do-you-want-to-know-more-about"></a>Qu’est-ce que vous voulez savoir plus sur

- Faire défiler une vue

- Mise à l’échelle d’une vue

- [Afficher les coordonnées](/windows/win32/gdi/window-coordinate-system)

## <a name="scrolling-a-view"></a><a name="_core_scrolling_a_view"></a>Faire défiler une vue

Fréquemment, la taille d’un document est supérieure à la taille que sa vue peut afficher. Cela peut se produire parce que les données du document augmente ou que l’utilisateur rétrécit la fenêtre qui encadre la vue. Dans de tels cas, la vue doit prendre en charge le défilement.

N’importe quelle vue peut `OnHScroll` gérer `OnVScroll` des messages à barres de défilement dans ses fonctions et membres. Vous pouvez soit implémenter la manipulation de messages à barres de `CScrollView` défilement dans ces fonctions, en faisant tout le travail vous-même, ou vous pouvez utiliser la classe pour gérer le défilement pour vous.

La fonction `CScrollView` effectue les actions suivantes :

- Gère la taille des fenêtres et des viewports et les modes de cartographie

- Faites défiler automatiquement en réponse aux messages à barres de défilement

Vous pouvez spécifier la quantité à faire défiler pour une "page" (lorsque l’utilisateur clique dans un arbre à barres de défilement) et une "ligne" (lorsque l’utilisateur clique dans une flèche de défilement). Planifiez ces valeurs en fonction de la nature de votre point de vue. Par exemple, vous pouvez faire défiler par incréments de 1 pixel pour une vue graphique, mais par incréments basés sur la hauteur de la ligne dans les documents texte.

## <a name="scaling-a-view"></a><a name="_core_scaling_a_view"></a>Mise à l’échelle d’une vue

Lorsque vous voulez que la vue s’adapte automatiquement `CScrollView` à la taille de sa fenêtre de cadre, vous pouvez utiliser pour la mise à l’échelle au lieu de défiler. La vue logique est étirée ou réduite pour s’adapter exactement à la zone cliente de la fenêtre. Une vue à l’échelle n’a pas de barres de défilement.

## <a name="see-also"></a>Voir aussi

[Utilisation des vues](../mfc/using-views.md)
