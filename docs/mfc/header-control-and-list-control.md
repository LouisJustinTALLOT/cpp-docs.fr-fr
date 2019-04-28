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
ms.openlocfilehash: 934b54de3266138225087d5519af2be51972cf9d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240073"
---
# <a name="header-control-and-list-control"></a>Contrôle Header et contrôle List

Dans la plupart des cas, vous allez utiliser le contrôle d’en-tête est incorporé dans un [CListCtrl](../mfc/reference/clistctrl-class.md) ou [CListView](../mfc/reference/clistview-class.md) objet. Toutefois, il existe des cas où un objet de contrôle d’en-tête distinct est souhaitable, telles que la manipulation de données, organisées en colonnes ou lignes, dans un [CView](../mfc/reference/cview-class.md)-objet dérivé. Dans ce cas, vous avez besoin de mieux contrôler l’apparence et le comportement par défaut d’un contrôle header incorporé.

Dans le cas courant que vous souhaitez un contrôle header afin d’offrir norme, comportement par défaut, il pouvez que vous souhaitez utiliser [CListCtrl](../mfc/reference/clistctrl-class.md) ou [CListView](../mfc/reference/clistview-class.md) à la place. Utilisez `CListCtrl` lorsque vous souhaitez que les fonctionnalités d’un contrôle d’en-tête par défaut, incorporé dans un contrôle commun list view. Utilisez [CListView](../mfc/reference/clistview-class.md) lorsque vous souhaitez que les fonctionnalités d’un contrôle d’en-tête par défaut, incorporé dans un objet de vue.

> [!NOTE]
>  Ces contrôles incluent uniquement un contrôle header intégrée si le contrôle list view est créé à l’aide de la **LVS_REPORT** style.

Dans la plupart des cas, l’apparence du contrôle header incorporé peut être modifié en modifiant les styles du contrôle d’affichage de liste contenant. En outre, plus d’informations sur le contrôle header peuvent être obtenus via les fonctions membres de contrôle list view parent. Toutefois, pour un contrôle complet et l’accès, les attributs et les styles du contrôle header incorporé, il est recommandé qu’obtenu un pointeur vers l’objet de contrôle d’en-tête.

L’objet de contrôle header incorporé est accessible à partir de le `CListCtrl` ou `CListView` avec un appel à la classe respective `GetHeaderCtrl` fonction membre. Le code suivant illustre cela :

[!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Utilisation d’image de listes avec des contrôles header](../mfc/using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
