---
title: Modification des styles de contrôle de liste
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
ms.openlocfilehash: 2ba9ae81f7b1693be0df3565256a65e4e3561fd3
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344467"
---
# <a name="changing-list-control-styles"></a>Modification des styles de contrôle de liste

Vous pouvez modifier le style d’un contrôle de liste ([CListCtrl](../mfc/reference/clistctrl-class.md)) à tout moment après l’avoir créée. En modifiant le style de fenêtre, vous modifiez le type d’affichage, que le contrôle utilise. Par exemple, pour émuler l’Explorateur, vous pouvez fournir des éléments de menu ou des boutons de barre d’outils pour basculer le contrôle entre différents affichages : affichage de l’icône, vue de liste et ainsi de suite.

Par exemple, lorsque l’utilisateur sélectionne l’élément de menu, vous pouvez effectuer un appel à [GetWindowLong](/windows/desktop/api/winuser/nf-winuser-getwindowlonga) pour récupérer le style actuel du contrôle, puis appelez [SetWindowLong](/windows/desktop/api/winuser/nf-winuser-setwindowlonga) pour réinitialiser le style. Pour plus d’informations, consultez [à l’aide des contrôles List View](/windows/desktop/Controls/using-list-view-controls) dans le SDK Windows.

Styles disponibles sont répertoriés dans [créer](../mfc/reference/clistctrl-class.md#create). Les styles **LVS_ICON**, **LVS_SMALLICON**, **LVS_LIST**, et **LVS_REPORT** désigner les affichages de contrôle de liste de quatre.

## <a name="extended-styles"></a>Styles étendus

Outre les styles standards pour un contrôle de liste, il existe un autre jeu de styles étendus. Ces styles, décrits dans [Styles étendus de la vue liste](/windows/desktop/Controls/extended-list-view-styles) dans le SDK Windows, fournissent de nombreuses fonctionnalités utiles qui personnalisent le comportement de votre contrôle de liste. Pour implémenter le comportement d’un style spécifique (par exemple, la sélection de pointage), effectuez un appel à [CListCtrl::SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle), en passant le style voulu. L’exemple suivant illustre l’appel de fonction :

[!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
>  Pour que la sélection fonctionne, vous devez également avoir **activé LVS_EX_ONECLICKACTIVATE** ou **LVS_EX_TWOCLICKACTIVATE** sous tension.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
