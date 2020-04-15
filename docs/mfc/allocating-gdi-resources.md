---
title: Allocation de ressources GDI
ms.date: 06/03/2019
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
ms.openlocfilehash: 149aefeade6f99c294b12bfb294cdf1addb9e5e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370849"
---
# <a name="allocating-gdi-resources"></a>Allocation de ressources GDI

Cet article explique comment allouer et libérer les objets GDI (Graphics Device Interface) Windows pour l'impression.

> [!NOTE]
> Pour plus d’informations, consultez la [documentation GDI SDK](/windows/win32/gdiplus/-gdiplus-gdi-start).

Supposons que vous avez besoin d'utiliser des polices, des stylets ou d'autres objets GDI pour l'impression, mais pas pour l'affichage à l'écran. Compte tenu de la mémoire qu'ils demandent, il n'est pas judicieux d'allouer ces objets au démarrage de l'application. Quand l'application n'imprime pas un document, cette mémoire peut être utile à d'autres tâches. Il est préférable de les allouer au début de l'impression, puis de les supprimer à la fin.

Pour allouer ces objets GDI, remplacez la fonction membre [OnBeginPrinting.](../mfc/reference/cview-class.md#onbeginprinting) Cette fonction est bien adaptée à cet objectif pour deux raisons : le cadre appelle cette fonction une fois au début de chaque travail d’impression et, contrairement à [OnPreparePrinting,](../mfc/reference/cview-class.md#onprepareprinting)cette fonction a accès à [l’objet CDC](../mfc/reference/cdc-class.md) représentant le pilote de l’appareil d’imprimante. Vous pouvez stocker ces objets pour une utilisation pendant le travail d’impression en définissant les variables des membres dans votre classe de vue qui pointent vers les objets GDI (par exemple, `CFont *` les membres, et ainsi de suite).

Pour utiliser les objets GDI que vous avez créés, sélectionnez-les dans le contexte de l’appareil d’imprimante dans la fonction membre [OnPrint.](../mfc/reference/cview-class.md#onprint) Si vous avez besoin d’objets GDI différents pour `m_nCurPage` différentes pages du document, vous pouvez examiner le membre de la structure [CPrintInfo](../mfc/reference/cprintinfo-structure.md) et sélectionner l’objet GDI en conséquence. Si vous avez besoin d'un objet GDI pour plusieurs pages consécutives, Windows vous impose de le sélectionner dans le contexte du périphérique à chaque appel de `OnPrint`.

Pour traiter ces objets GDI, remplacez la fonction membre [OnEndPrinting.](../mfc/reference/cview-class.md#onendprinting) L'infrastructure appelle cette fonction à la fin de chaque travail d'impression, ce qui vous donne la possibilité de libérer les objets GDI propres à l'impression avant que l'application revienne à d'autres tâches.

## <a name="see-also"></a>Voir aussi

[Impression](../mfc/printing.md)<br/>
[Impression par défaut](../mfc/how-default-printing-is-done.md)
