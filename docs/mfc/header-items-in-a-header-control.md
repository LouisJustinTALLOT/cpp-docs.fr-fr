---
title: Éléments d’en-tête dans un contrôle Header | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- header controls [MFC], header items in
- header items in header controls [MFC]
- CHeaderCtrl class [MFC], header items in
- controls [MFC], header
ms.assetid: ac79ef1f-a671-4ab2-93e9-b1aa016a48bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 21f1893861c5cb6a134cffa75806cc53eadaf059
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442368"
---
# <a name="header-items-in-a-header-control"></a>Éléments d'en-tête dans un contrôle Header

Vous avez un contrôle important sur l’apparence et le comportement des éléments d’en-tête qui composent un contrôle header ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)). Chaque élément d’en-tête peut avoir une chaîne, une image bitmap, une image à partir d’une liste d’images associée, ou une valeur 32 bits définie par l’application associée. La chaîne, une image bitmap ou une image s’affiche dans l’élément d’en-tête.

Vous pouvez personnaliser l’apparence et le contenu de nouveaux éléments lorsqu’elles sont créées par un appel [CHeaderCtrl::InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem) ou en modifiant un élément existant, avec un appel à [appelant CHeaderCtrl::GetItem](../mfc/reference/cheaderctrl-class.md#getitem) et [ CHeaderCtrl::SetItem](../mfc/reference/cheaderctrl-class.md#setitem).

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Personnaliser l’apparence de l’élément d’en-tête](../mfc/customizing-the-header-item-s-appearance.md)

- [Organisation des éléments dans le contrôle header](../mfc/ordering-items-in-the-header-control.md)

- [Prise en charge glisser-déposer pour les éléments d’en-tête](../mfc/providing-drag-and-drop-support-for-header-items.md)

- [Utilisation d’image de listes avec des contrôles header](../mfc/using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)

