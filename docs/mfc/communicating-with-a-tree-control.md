---
title: Communication avec un contrôle d'arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
ms.openlocfilehash: 920608724ebb362b91efdcb3eab50b80acd20474
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289876"
---
# <a name="communicating-with-a-tree-control"></a>Communication avec un contrôle d'arborescence

Vous utilisez différentes méthodes pour appeler des fonctions membres dans un [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objet selon la façon dont l’objet a été créé :

- Si le contrôle d’arborescence est dans une boîte de dialogue, utilisez une variable membre de type `CTreeCtrl` que vous créez dans la classe de boîte de dialogue.

- Si le contrôle d’arborescence est une fenêtre enfant, utilisez la `CTreeCtrl` objet (ou pointeur) que vous avez utilisé pour construire l’objet.

- Si vous utilisez un `CTreeView` de l’objet, utilisez la fonction [CTreeView::GetTreeCtrl](../mfc/reference/ctreeview-class.md#gettreectrl) pour obtenir une référence au contrôle d’arborescence. Vous pouvez initialiser une autre référence avec cette valeur ou assigner l’adresse de la référence à un `CTreeCtrl` pointeur.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
