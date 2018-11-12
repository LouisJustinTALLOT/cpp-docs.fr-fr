---
title: Prise en charge du glisser-déposer pour les éléments d’en-tête
ms.date: 11/04/2016
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
ms.openlocfilehash: 21ff14982baac93fac1cf3ee441353c079f4f760
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602967"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Prise en charge du glisser-déposer pour les éléments d’en-tête

Pour fournir la prise en charge du glisser-déplacer pour les éléments d’en-tête, spécifiez le style HDS_DRAGDROP. Prise en charge de glisser-déplacer des éléments d’en-tête donne à l’utilisateur la possibilité de réorganiser les éléments d’un contrôle d’en-tête. Le comportement par défaut fournit une image translucide de l’élément d’en-tête qui est glissé et un indicateur visuel de la nouvelle position, si l’élément d’en-tête est supprimée.

Avec des fonctionnalités communes glisser-déplacer, vous pouvez étendre le comportement de glisser-déplacer par défaut en gérant les notifications standard et HDN_ENDDRAG. Vous pouvez également personnaliser l’apparence de l’image glisser en substituant le [fonction membre CHeaderCtrl::CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) fonction membre.

> [!NOTE]
>  Si vous fournissez la prise en charge du glisser-déplacer pour un contrôle header incorporé dans un contrôle de liste, consultez la section de Style étendu dans le [modification des Styles de contrôle liste](../mfc/changing-list-control-styles.md) rubrique.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)

