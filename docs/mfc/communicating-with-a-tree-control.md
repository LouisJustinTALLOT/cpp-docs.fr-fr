---
title: Communication avec un contrôle d’arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
ms.openlocfilehash: a5749b76468a7ba30cd48dc3a9b61f2de7ac67b9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654181"
---
# <a name="communicating-with-a-tree-control"></a>Communication avec un contrôle d’arborescence

Vous utilisez différentes méthodes pour appeler des fonctions membres dans un [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objet selon la façon dont l’objet a été créé :

- Si le contrôle d’arborescence est dans une boîte de dialogue, utilisez une variable membre de type `CTreeCtrl` que vous créez dans la classe de boîte de dialogue.

- Si le contrôle d’arborescence est une fenêtre enfant, utilisez la `CTreeCtrl` objet (ou pointeur) que vous avez utilisé pour construire l’objet.

- Si vous utilisez un `CTreeView` de l’objet, utilisez la fonction [CTreeView::GetTreeCtrl](../mfc/reference/ctreeview-class.md#gettreectrl) pour obtenir une référence au contrôle d’arborescence. Vous pouvez initialiser une autre référence avec cette valeur ou assigner l’adresse de la référence à un `CTreeCtrl` pointeur.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

