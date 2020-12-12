---
description: 'En savoir plus sur : utilisation des info-bulles dans un objet CStatusBarCtrl'
title: Utilisation d'info-bulles dans un objet CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: d77610a511698000dc70a1aa1cb1edb22fb3eb7a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143245"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Utilisation d'info-bulles dans un objet CStatusBarCtrl

Pour activer les info-bulles pour un contrôle de barre d’État, créez l' `CStatusBarCtrl` objet avec le style SBT_TOOLTIPS.

> [!NOTE]
> Si vous utilisez un `CStatusBar` objet pour implémenter votre barre d’État, utilisez la `CStatusBar::CreateEx` fonction. Elle vous permet de spécifier des styles supplémentaires pour l' `CStatusBarCtrl` objet incorporé.

Une fois l' `CStatusBarCtrl` objet créé, utilisez [CStatusBarCtrl :: SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) et [CStatusBarCtrl :: GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext) pour définir et récupérer le texte info-bulle d’un volet spécifique.

Une fois que l’info-bulle a été définie, elle s’affiche uniquement si la partie a une icône et aucun texte, ou si tout le texte ne peut pas être affiché à l’intérieur de la partie. Les info-bulles ne sont pas prises en charge en mode simple.

## <a name="see-also"></a>Voir aussi

[Utilisation de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
