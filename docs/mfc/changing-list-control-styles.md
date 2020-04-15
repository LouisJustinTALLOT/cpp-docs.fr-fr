---
title: Modification des styles de contrôle de liste
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
ms.openlocfilehash: 5f45e0549c3fc0f5747f8dd12a6310fafd7dd7bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370815"
---
# <a name="changing-list-control-styles"></a>Modification des styles de contrôle de liste

Vous pouvez modifier le style de fenêtre d’un contrôle de liste ([CListCtrl](../mfc/reference/clistctrl-class.md)) à tout moment après l’avoir créé. En changeant le style de fenêtre, vous modifiez le type de vue que le contrôle utilise. Par exemple, pour émuler l’Explorer, vous pouvez fournir des éléments de menu ou des boutons de barre d’outils pour changer le contrôle entre différentes vues : vue d’icône, vue de liste, etc.

Par exemple, lorsque l’utilisateur sélectionne votre élément de menu, vous pouvez passer un appel à [GetWindowLong](/windows/win32/api/winuser/nf-winuser-getwindowlongw) pour récupérer le style actuel du contrôle, puis appeler [SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw) pour réinitialiser le style. Pour plus d’informations, voir [Utiliser les contrôles de vue de liste](/windows/win32/Controls/using-list-view-controls) dans le SDK Windows.

Les styles disponibles sont répertoriés dans [Create](../mfc/reference/clistctrl-class.md#create). Les styles **LVS_ICON**, **LVS_SMALLICON**, **LVS_LIST**, et **LVS_REPORT** désigner les quatre vues de contrôle de liste.

## <a name="extended-styles"></a>Styles étendus

En plus des styles standard pour un contrôle de liste, il ya un autre ensemble, appelé styles étendus. Ces styles, discutés dans [Extended List View Styles](/windows/win32/Controls/extended-list-view-styles) dans le Windows SDK, fournissent une variété de fonctionnalités utiles qui personnalisent le comportement de votre contrôle de liste. Pour mettre en œuvre le comportement d’un certain style (comme la sélection de vol stationnaire), faites un appel à [CListCtrl::SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle), en passant le style nécessaire. L’exemple suivant montre l’appel de fonction :

[!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
> Pour que la sélection de vol stationnaire fonctionne, vous devez également avoir **LVS_EX_ONECLICKACTIVATE** ou **LVS_EX_TWOCLICKACTIVATE** allumé.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
