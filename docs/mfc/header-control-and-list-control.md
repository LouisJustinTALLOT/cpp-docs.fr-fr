---
title: Contrôle Header et contrôle List
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], with CHeaderCtrl
- CListCtrl class [MFC], header controls
- CHeaderCtrl class [MFC], with CListCtrl
- controls [MFC], header
- header controls [MFC]
- header controls [MFC], list controls used with
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
ms.openlocfilehash: 53dd6f1a7878d82a7f7ac48dd7082d791323941b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370474"
---
# <a name="header-control-and-list-control"></a>Contrôle Header et contrôle List

Dans la plupart des cas, vous utiliserez le contrôle d’en-tête qui est intégré dans un objet [CListCtrl](../mfc/reference/clistctrl-class.md) ou [CListView.](../mfc/reference/clistview-class.md) Cependant, il y a des cas où un objet de contrôle d’en-tête séparé est souhaitable, tel que manipuler des données, disposées en colonnes ou en rangées, dans un objet dérivé de [CView.](../mfc/reference/cview-class.md) Dans ces cas, vous avez besoin d’un plus grand contrôle sur l’apparence et le comportement par défaut d’un contrôle d’en-tête intégré.

Dans le cas courant que vous voulez un contrôle d’en-tête pour fournir la norme, comportement par défaut, vous pouvez utiliser [CListCtrl](../mfc/reference/clistctrl-class.md) ou [CListView](../mfc/reference/clistview-class.md) à la place. Utilisez `CListCtrl` lorsque vous voulez la fonctionnalité d’un contrôle d’en-tête par défaut, intégré dans une liste afficher le contrôle commun. Utilisez [CListView](../mfc/reference/clistview-class.md) lorsque vous souhaitez la fonctionnalité d’un contrôle d’en-tête par défaut, intégré dans un objet de vue.

> [!NOTE]
> Ces contrôles n’incluent qu’un contrôle d’en-tête intégré si le contrôle de vue de liste est créé en utilisant le style **LVS_REPORT.**

Dans la plupart des cas, l’apparence du contrôle d’en-tête intégré peut être modifiée en modifiant les styles du contrôle de vue de liste contenant. En outre, les informations sur le contrôle de l’en-tête peuvent être obtenues grâce aux fonctions des membres du contrôle de vue de la liste mère. Toutefois, pour un contrôle complet et un accès, aux attributs et aux styles du contrôle de l’en-tête intégré, il est recommandé d’obtenir un pointeur à l’objet de contrôle de l’en-tête.

L’objet de contrôle d’en-tête intégré peut être accessible à partir de l’un ou l’autre `CListCtrl` ou `CListView` avec un appel à la fonction de membre de `GetHeaderCtrl` la classe respective. Le code suivant illustre cela :

[!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>Qu’est-ce que vous voulez savoir plus sur

- [Utilisation de listes d’images avec des commandes d’en-tête](../mfc/using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
