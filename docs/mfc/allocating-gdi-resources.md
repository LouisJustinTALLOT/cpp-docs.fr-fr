---
description: 'En savoir plus sur : allouer des ressources GDI'
title: Allocation de ressources GDI
ms.date: 06/03/2019
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
ms.openlocfilehash: 348f1ca1eadc22dfc8ca6faa6c31bb2f8d81e51e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176806"
---
# <a name="allocating-gdi-resources"></a>Allocation de ressources GDI

Cet article explique comment allouer et libérer les objets GDI (Graphics Device Interface) Windows pour l'impression.

> [!NOTE]
> Pour plus d’informations, consultez la [documentation du kit de développement logiciel (SDK) GDI+](/windows/win32/gdiplus/-gdiplus-gdi-start).

Supposons que vous avez besoin d'utiliser des polices, des stylets ou d'autres objets GDI pour l'impression, mais pas pour l'affichage à l'écran. Compte tenu de la mémoire qu'ils demandent, il n'est pas judicieux d'allouer ces objets au démarrage de l'application. Quand l'application n'imprime pas un document, cette mémoire peut être utile à d'autres tâches. Il est préférable de les allouer au début de l'impression, puis de les supprimer à la fin.

Pour allouer ces objets GDI, substituez la fonction membre [OnBeginPrinting](reference/cview-class.md#onbeginprinting) . Cette fonction est bien adaptée à cette fin pour deux raisons : l’infrastructure appelle cette fonction une fois au début de chaque travail d’impression et, contrairement à [OnPreparePrinting](reference/cview-class.md#onprepareprinting), cette fonction a accès à l’objet [CDC](reference/cdc-class.md) représentant le pilote de périphérique de l’imprimante. Vous pouvez stocker ces objets pour une utilisation pendant le travail d’impression en définissant des variables membres dans votre classe d’affichage qui pointent vers des objets GDI (par exemple, des `CFont *` membres, etc.).

Pour utiliser les objets GDI que vous avez créés, sélectionnez-les dans le contexte de périphérique d’impression dans la fonction membre [OnPrint](reference/cview-class.md#onprint) . Si vous avez besoin de différents objets GDI pour différentes pages du document, vous pouvez examiner le `m_nCurPage` membre de la structure [CPrintInfo](reference/cprintinfo-structure.md) et sélectionner l’objet GDI en conséquence. Si vous avez besoin d'un objet GDI pour plusieurs pages consécutives, Windows vous impose de le sélectionner dans le contexte du périphérique à chaque appel de `OnPrint`.

Pour libérer ces objets GDI, substituez la fonction membre [OnEndPrinting](reference/cview-class.md#onendprinting) . L'infrastructure appelle cette fonction à la fin de chaque travail d'impression, ce qui vous donne la possibilité de libérer les objets GDI propres à l'impression avant que l'application revienne à d'autres tâches.

## <a name="see-also"></a>Voir aussi

[Impression](printing.md)<br/>
[Comment l’impression par défaut est effectuée](how-default-printing-is-done.md)
