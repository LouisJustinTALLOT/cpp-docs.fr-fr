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
ms.openlocfilehash: f9dd34b27ddbdc0b99fafbb23ad1cf9782d98605
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626418"
---
# <a name="header-control-and-list-control"></a>Contrôle Header et contrôle List

Dans la plupart des cas, vous utiliserez le contrôle header qui est incorporé dans un objet [CListCtrl](reference/clistctrl-class.md) ou [CListView](reference/clistview-class.md) . Toutefois, il existe des cas où un objet de contrôle d’en-tête distinct est souhaitable, tel que la manipulation de données, organisées en colonnes ou en lignes, dans un objet dérivé de [CView](reference/cview-class.md). Dans ce cas, vous avez besoin d’un contrôle accru sur l’apparence et le comportement par défaut d’un contrôle d’en-tête incorporé.

Dans le cas courant où vous souhaitez qu’un contrôle header fournisse un comportement par défaut standard, vous souhaiterez peut-être utiliser [CListCtrl](reference/clistctrl-class.md) ou [CListView](reference/clistview-class.md) à la place. Utilisez `CListCtrl` lorsque vous souhaitez les fonctionnalités d’un contrôle d’en-tête par défaut, incorporé dans un contrôle commun d’affichage de liste. Utilisez [CListView](reference/clistview-class.md) lorsque vous souhaitez les fonctionnalités d’un contrôle header par défaut, incorporé dans un objet View.

> [!NOTE]
> Ces contrôles incluent uniquement un contrôle d’en-tête intégré si le contrôle d’affichage de liste est créé à l’aide du style de **LVS_REPORT** .

Dans la plupart des cas, l’apparence du contrôle d’en-tête incorporé peut être modifiée en modifiant les styles du contrôle d’affichage de liste conteneur. En outre, les informations sur le contrôle header peuvent être obtenues via les fonctions membres du contrôle List View parent. Toutefois, pour un contrôle complet et un accès aux attributs et styles du contrôle d’en-tête incorporé, il est recommandé d’obtenir un pointeur vers l’objet de contrôle header.

L’objet de contrôle d’en-tête incorporé est accessible à partir de `CListCtrl` ou `CListView` avec un appel à la fonction membre de la classe respective `GetHeaderCtrl` . Le code suivant illustre cela :

[!code-cpp[NVC_MFCControlLadenDialog#14](codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Utilisation de listes d’images avec des contrôles Header](using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](using-cheaderctrl.md)<br/>
[Commandes](controls-mfc.md)
