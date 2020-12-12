---
description: En savoir plus sur les éléments d’en-tête dans un contrôle header
title: Éléments d'en-tête dans un contrôle Header
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], header items in
- header items in header controls [MFC]
- CHeaderCtrl class [MFC], header items in
- controls [MFC], header
ms.assetid: ac79ef1f-a671-4ab2-93e9-b1aa016a48bf
ms.openlocfilehash: 4b91ef1395d814b89ff12234b0aa8f2d674512ab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172854"
---
# <a name="header-items-in-a-header-control"></a>Éléments d'en-tête dans un contrôle Header

Vous disposez d’un contrôle considérable sur l’apparence et le comportement des éléments d’en-tête qui composent un contrôle header ([CHeaderCtrl](reference/cheaderctrl-class.md)). Chaque élément d’en-tête peut avoir une chaîne, une image bitmap, une image d’une liste d’images associée ou une valeur 32 bits définie par l’application qui lui est associée. La chaîne, la bitmap ou l’image s’affiche dans l’élément d’en-tête.

Vous pouvez personnaliser l’apparence et le contenu de nouveaux éléments quand ils sont créés en appelant [CHeaderCtrl :: InsertItem](reference/cheaderctrl-class.md#insertitem) ou en modifiant un élément existant, à l’aide d’un appel à [CHeaderCtrl :: GetItem](reference/cheaderctrl-class.md#getitem) et [CHeaderCtrl :: SetItem](reference/cheaderctrl-class.md#setitem).

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Personnalisation de l’apparence de l’élément d’en-tête](customizing-the-header-item-s-appearance.md)

- [Organisation des éléments dans le contrôle d’en-tête](ordering-items-in-the-header-control.md)

- [Prise en charge du glisser-déplacer pour les éléments d’en-tête](providing-drag-and-drop-support-for-header-items.md)

- [Utilisation de listes d'images avec des contrôles d’en-tête](using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](using-cheaderctrl.md)
