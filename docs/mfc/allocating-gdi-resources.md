---
title: Allocation de ressources GDI
ms.date: 06/03/2019
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
ms.openlocfilehash: adfd8b19f683b82eec213890c8e1345e070ff3ec
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504632"
---
# <a name="allocating-gdi-resources"></a>Allocation de ressources GDI

Cet article explique comment allouer et libérer les objets GDI (Graphics Device Interface) Windows pour l'impression.

> [!NOTE]
>  Pour plus d’informations, consultez le [documentation du SDK GDI +](/windows/desktop/gdiplus/-gdiplus-gdi-start).

Supposons que vous avez besoin d'utiliser des polices, des stylets ou d'autres objets GDI pour l'impression, mais pas pour l'affichage à l'écran. Compte tenu de la mémoire qu'ils demandent, il n'est pas judicieux d'allouer ces objets au démarrage de l'application. Quand l'application n'imprime pas un document, cette mémoire peut être utile à d'autres tâches. Il est préférable de les allouer au début de l'impression, puis de les supprimer à la fin.

Pour allouer ces objets GDI, substituez le [OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting) fonction membre. Cette fonction est parfaitement adaptée à cet effet pour deux raisons : l’infrastructure appelle cette fonction une fois au début de chaque travail d’impression et, contrairement à [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting), cette fonction a accès à la [CDC](../mfc/reference/cdc-class.md) objet représentant le pilote de périphérique d’imprimante. Vous pouvez stocker ces objets pour une utilisation pendant le travail d’impression en définissant des variables membres dans votre classe d’affichage qui pointent vers les objets GDI (par exemple, `CFont *` membres et ainsi de suite).

Pour utiliser les objets GDI que vous avez créés, sélectionnez-les dans le contexte de périphérique d’imprimante dans le [OnPrint](../mfc/reference/cview-class.md#onprint) fonction membre. Si vous avez besoin d’autres objets GDI pour les différentes pages du document, vous pouvez examiner le `m_nCurPage` membre de la [CPrintInfo](../mfc/reference/cprintinfo-structure.md) structurer et sélectionnez l’objet GDI en conséquence. Si vous avez besoin d'un objet GDI pour plusieurs pages consécutives, Windows vous impose de le sélectionner dans le contexte du périphérique à chaque appel de `OnPrint`.

Pour supprimer ces objets GDI, substituez le [OnEndPrinting](../mfc/reference/cview-class.md#onendprinting) fonction membre. L'infrastructure appelle cette fonction à la fin de chaque travail d'impression, ce qui vous donne la possibilité de libérer les objets GDI propres à l'impression avant que l'application revienne à d'autres tâches.

## <a name="see-also"></a>Voir aussi

[Impression](../mfc/printing.md)<br/>
[Impression par défaut](../mfc/how-default-printing-is-done.md)
