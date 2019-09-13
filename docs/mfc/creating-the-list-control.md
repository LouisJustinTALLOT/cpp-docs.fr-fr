---
title: Création du contrôle de liste
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating control
- list controls [MFC]
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
ms.openlocfilehash: f1c5d8db93421e1d3ae0e39aec82bdf0f5529f1f
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907922"
---
# <a name="creating-the-list-control"></a>Création du contrôle de liste

La façon dont le contrôle de liste ([CListCtrl](../mfc/reference/clistctrl-class.md)) est créé varie selon que vous utilisez le contrôle directement ou que vous utilisez la classe [CListView](../mfc/reference/clistview-class.md) à la place. Si vous utilisez `CListView`, le Framework construit la vue dans le cadre de sa séquence de création de document/vue. La création de la vue Liste crée également le contrôle List (les deux sont identiques). Le contrôle est créé dans la fonction gestionnaire [OnCreate](../mfc/reference/cwnd-class.md#oncreate) de la vue. Dans ce cas, le contrôle est prêt à ajouter des éléments, via un appel à [GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl).

### <a name="to-use-clistctrl-directly-in-a-dialog-box"></a>Pour utiliser CListCtrl directement dans une boîte de dialogue

1. Dans l’éditeur de boîtes de dialogue, ajoutez un contrôle de liste à votre ressource de modèle de boîte de dialogue. Spécifiez son ID de contrôle.

1. Utilisez l' [Assistant Ajout de variable membre](../ide/adding-a-member-variable-visual-cpp.md) pour ajouter une variable membre de `CListCtrl` type avec la propriété Control. Vous pouvez utiliser ce membre pour appeler `CListCtrl` des fonctions membres.

1. Utilisez l' [Assistant classe](reference/mfc-class-wizard.md) pour mapper les fonctions de gestionnaire de la classe de boîte de dialogue pour tous les messages de notification de contrôle de liste que vous devez gérer (voir [mappage de messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)).

1. Dans [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), définissez les styles pour le `CListCtrl`. Consultez [modification des styles de contrôle de liste](../mfc/changing-list-control-styles.md). Cela détermine le type de « vue » que vous recevez dans le contrôle, même si vous pouvez modifier l’affichage ultérieurement.

### <a name="to-use-clistctrl-in-a-nondialog-window"></a>Pour utiliser CListCtrl dans une fenêtre qui n’est pas une boîte de dialogue

1. Définissez le contrôle dans la vue ou la classe de fenêtre.

1. Appelez la fonction membre [Create](../mfc/reference/clistctrl-class.md#create) du contrôle, éventuellement dans [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), éventuellement aussi tôt que la fonction gestionnaire [OnCreate](../mfc/reference/cwnd-class.md#oncreate) de la fenêtre parente (si vous sous-classez le contrôle). Définissez les styles pour le contrôle.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
