---
title: Contrôle de liste et vue Liste
ms.date: 11/04/2016
helpviewer_keywords:
- CListView class [MFC], and CListCtrl
- views [MFC], list and list control
- CListCtrl class [MFC], and CListView
- list views [MFC]
- list controls [MFC], List view
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
ms.openlocfilehash: d308cfe83f02dcfe3687790c6638d268cc69fc24
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621426"
---
# <a name="list-control-and-list-view"></a>Contrôle de liste et vue Liste

Pour plus de commodité, MFC encapsule le contrôle de liste de deux manières. Vous pouvez utiliser des contrôles de liste :

- Directement, en incorporant un objet [CListCtrl](reference/clistctrl-class.md) dans une classe de boîte de dialogue.

- Indirectement, à l’aide de la classe [CListView](reference/clistview-class.md).

`CListView`facilite l’intégration d’un contrôle de liste à l’architecture document/vue MFC, en encapsulant le contrôle de la même façon que [CEditView](reference/ceditview-class.md) encapsule un contrôle d’édition : le contrôle remplit toute la surface d’exposition d’une vue MFC. (La vue *est* le contrôle, casté en `CListView` .)

Un `CListView` objet hérite de [CCtrlView](reference/cctrlview-class.md) et de ses classes de base et ajoute une fonction membre pour récupérer le contrôle de liste sous-jacent. Utilisez afficher les membres pour travailler avec la vue en tant que vue. Utilisez la fonction membre [GetListCtrl](reference/clistview-class.md#getlistctrl) pour accéder aux fonctions membres du contrôle de liste. Utilisez les membres suivants pour :

- Ajoutez, supprimez ou manipulez des « éléments » dans la liste.

- Définissez ou récupérez les attributs de contrôle de liste.

Pour obtenir une référence au `CListCtrl` sous-jacent a `CListView` , appelez `GetListCtrl` à partir de votre classe d’affichage de liste :

[!code-cpp[NVC_MFCListView#4](../atl/reference/codesnippet/cpp/list-control-and-list-view_1.cpp)]

Cette rubrique décrit les deux façons d’utiliser le contrôle de liste.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](using-clistctrl.md)<br/>
[Commandes](controls-mfc.md)
