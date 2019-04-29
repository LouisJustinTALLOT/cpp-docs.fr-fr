---
title: Prise en charge du glisser-déplacer pour les éléments d'en-tête
ms.date: 11/04/2016
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
ms.openlocfilehash: f30ad029742a01280abda85cbd1a81104d01d8cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297032"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Prise en charge du glisser-déplacer pour les éléments d'en-tête

Pour fournir la prise en charge du glisser-déplacer pour les éléments d’en-tête, spécifiez le style HDS_DRAGDROP. Prise en charge de glisser-déplacer des éléments d’en-tête donne à l’utilisateur la possibilité de réorganiser les éléments d’un contrôle d’en-tête. Le comportement par défaut fournit une image translucide de l’élément d’en-tête qui est glissé et un indicateur visuel de la nouvelle position, si l’élément d’en-tête est supprimée.

Avec des fonctionnalités communes glisser-déplacer, vous pouvez étendre le comportement de glisser-déplacer par défaut en gérant les notifications standard et HDN_ENDDRAG. Vous pouvez également personnaliser l’apparence de l’image glisser en substituant le [fonction membre CHeaderCtrl::CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) fonction membre.

> [!NOTE]
>  Si vous fournissez la prise en charge du glisser-déplacer pour un contrôle header incorporé dans un contrôle de liste, consultez la section de Style étendu dans le [modification des Styles de contrôle liste](../mfc/changing-list-control-styles.md) rubrique.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)
