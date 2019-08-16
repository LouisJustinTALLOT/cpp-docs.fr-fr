---
title: Modification des styles de contrôle de liste
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
ms.openlocfilehash: b3cc65ce6ef0e84eaa2f6738cb18b6b862a6473a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509054"
---
# <a name="changing-list-control-styles"></a>Modification des styles de contrôle de liste

Vous pouvez modifier le style de fenêtre d’un contrôle de liste ([CListCtrl](../mfc/reference/clistctrl-class.md)) à tout moment une fois que vous l’avez créé. En modifiant le style de la fenêtre, vous modifiez le type d’affichage utilisé par le contrôle. Par exemple, pour émuler l’Explorateur, vous pouvez fournir des éléments de menu ou des boutons de barre d’outils pour basculer le contrôle entre différentes vues: vue icône, mode liste, et ainsi de suite.

Par exemple, quand l’utilisateur sélectionne votre élément de menu, vous pouvez appeler [GetWindowLong](/windows/win32/api/winuser/nf-winuser-getwindowlongw) pour récupérer le style actuel du contrôle, puis appeler [SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw) pour réinitialiser le style. Pour plus d’informations, consultez [utilisation des contrôles d’affichage de liste](/windows/win32/Controls/using-list-view-controls) dans le SDK Windows.

Les styles disponibles sont répertoriés dans [créer](../mfc/reference/clistctrl-class.md#create). Les styles **LVS_ICON**, **LVS_SMALLICON**, **LVS_LIST**et **LVS_REPORT** désignent les quatre vues de contrôle de liste.

## <a name="extended-styles"></a>Styles étendus

Outre les styles standard pour un contrôle de liste, il existe un autre ensemble, appelé styles étendus. Ces styles, présentés dans les [styles de vue de liste étendus](/windows/win32/Controls/extended-list-view-styles) dans le SDK Windows, fournissent une variété de fonctionnalités utiles qui personnalisent le comportement de votre contrôle de liste. Pour implémenter le comportement d’un certain style (tel que la sélection par pointage), effectuez un appel à [CListCtrl:: SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle), en passant le style requis. L’exemple suivant illustre l’appel de fonction:

[!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
>  Pour que la sélection par pointage fonctionne, vous devez également activer l’option **LVS_EX_ONECLICKACTIVATE** ou **LVS_EX_TWOCLICKACTIVATE** .

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
