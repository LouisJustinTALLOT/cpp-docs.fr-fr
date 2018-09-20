---
title: Prise en charge du glisser-déplacer pour les éléments d’en-tête | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b2eaa5040d34a442868a8fa6cb9f2aae08b0a6f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407697"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Prise en charge du glisser-déposer pour les éléments d’en-tête

Pour fournir la prise en charge du glisser-déplacer pour les éléments d’en-tête, spécifiez le style HDS_DRAGDROP. Prise en charge de glisser-déplacer des éléments d’en-tête donne à l’utilisateur la possibilité de réorganiser les éléments d’un contrôle d’en-tête. Le comportement par défaut fournit une image translucide de l’élément d’en-tête qui est glissé et un indicateur visuel de la nouvelle position, si l’élément d’en-tête est supprimée.

Avec des fonctionnalités communes glisser-déplacer, vous pouvez étendre le comportement de glisser-déplacer par défaut en gérant les notifications standard et HDN_ENDDRAG. Vous pouvez également personnaliser l’apparence de l’image glisser en substituant le [fonction membre CHeaderCtrl::CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) fonction membre.

> [!NOTE]
>  Si vous fournissez la prise en charge du glisser-déplacer pour un contrôle header incorporé dans un contrôle de liste, consultez la section de Style étendu dans le [modification des Styles de contrôle liste](../mfc/changing-list-control-styles.md) rubrique.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)

