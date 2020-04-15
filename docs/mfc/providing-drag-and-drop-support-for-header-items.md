---
title: Prise en charge du glisser-déplacer pour les éléments d'en-tête
ms.date: 11/04/2016
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
ms.openlocfilehash: 8dfaabf3da62c216d3da662f59c57b63e695d9ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371161"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Prise en charge du glisser-déplacer pour les éléments d'en-tête

Pour fournir un support de drag-and-drop pour les éléments d’en-tête, spécifiez le style HDS_DRAGDROP. Le support drag-and-drop pour les éléments d’en-tête donne à l’utilisateur la possibilité de réorganiser les éléments d’en-tête d’un contrôle d’en-tête. Le comportement par défaut fournit une image de traînée semitransparent de l’élément d’en-tête étant traîné et un indicateur visuel de la nouvelle position, si l’élément d’en-tête est abandonné.

Comme avec la fonctionnalité de drag-and-drop commune, vous pouvez étendre le comportement par défaut de drag-and-drop en manipulant les notifications HDN_BEGINDRAG et HDN_ENDDRAG. Vous pouvez également personnaliser l’apparence de l’image de traînée en remplaçant la fonction de membre [CHeaderCtrl::CreateDragImage.](../mfc/reference/cheaderctrl-class.md#createdragimage)

> [!NOTE]
> Si vous fournissez un support de drag-and-drop pour un contrôle d’en-tête intégré dans un contrôle de liste, consultez la section Style étendu dans le sujet [Changing List Control Styles.](../mfc/changing-list-control-styles.md)

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)
