---
description: 'En savoir plus sur : création du contrôle List'
title: Création du contrôle de liste
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating control
- list controls [MFC]
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
ms.openlocfilehash: 5be1a9ce7a2cd8279d576dfc41e44c810c433515
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309574"
---
# <a name="creating-the-list-control"></a>Création du contrôle de liste

La façon dont le contrôle de liste ([CListCtrl](reference/clistctrl-class.md)) est créé varie selon que vous utilisez le contrôle directement ou que vous utilisez la classe [CListView](reference/clistview-class.md) à la place. Si vous utilisez `CListView` , le Framework construit la vue dans le cadre de sa séquence de création de document/vue. La création de la vue Liste crée également le contrôle List (les deux sont identiques). Le contrôle est créé dans la fonction gestionnaire [OnCreate](reference/cwnd-class.md#oncreate) de la vue. Dans ce cas, le contrôle est prêt à ajouter des éléments, via un appel à [GetListCtrl](reference/clistview-class.md#getlistctrl).

### <a name="to-use-clistctrl-directly-in-a-dialog-box"></a>Pour utiliser CListCtrl directement dans une boîte de dialogue

1. Dans l’éditeur de boîtes de dialogue, ajoutez un contrôle de liste à votre ressource de modèle de boîte de dialogue. Spécifiez son ID de contrôle.

1. Utilisez l' [Assistant Ajout de variable membre](../ide/adding-a-member-variable-visual-cpp.md) pour ajouter une variable membre de type `CListCtrl` avec la propriété Control. Vous pouvez utiliser ce membre pour appeler des `CListCtrl` fonctions membres.

1. Utilisez l' [Assistant classe](reference/mfc-class-wizard.md) pour mapper les fonctions de gestionnaire de la classe de boîte de dialogue pour tous les messages de notification de contrôle de liste que vous devez gérer (voir [mappage de messages à des fonctions](reference/mapping-messages-to-functions.md)).

1. Dans [OnInitDialog](reference/cdialog-class.md#oninitdialog), définissez les styles pour le `CListCtrl` . Consultez [modification des styles de contrôle de liste](changing-list-control-styles.md). Cela détermine le type de « vue » que vous recevez dans le contrôle, même si vous pouvez modifier l’affichage ultérieurement.

### <a name="to-use-clistctrl-in-a-nondialog-window"></a>Pour utiliser CListCtrl dans une fenêtre qui n’est pas une boîte de dialogue

1. Définissez le contrôle dans la vue ou la classe de fenêtre.

1. Appelez la fonction membre [Create](reference/clistctrl-class.md#create) du contrôle, éventuellement dans [OnInitialUpdate](reference/cview-class.md#oninitialupdate), éventuellement aussi tôt que la fonction gestionnaire [OnCreate](reference/cwnd-class.md#oncreate) de la fenêtre parente (si vous sous-classez le contrôle). Définissez les styles pour le contrôle.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](using-clistctrl.md)<br/>
[Contrôles](controls-mfc.md)
