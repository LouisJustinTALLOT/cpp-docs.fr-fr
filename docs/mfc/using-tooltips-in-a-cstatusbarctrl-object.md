---
title: Utilisation d'info-bulles dans un objet CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: a607a5fb8c9470df42d12c771865b924891b2dac
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442545"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Utilisation d'info-bulles dans un objet CStatusBarCtrl

Pour activer les info-bulles pour un contrôle de barre d’État, créez l’objet `CStatusBarCtrl` avec le style SBT_TOOLTIPS.

> [!NOTE]
>  Si vous utilisez un objet `CStatusBar` pour implémenter votre barre d’État, utilisez la fonction `CStatusBar::CreateEx`. Elle vous permet de spécifier des styles supplémentaires pour l’objet `CStatusBarCtrl` incorporé.

Une fois que l’objet `CStatusBarCtrl` a été créé avec succès, utilisez [CStatusBarCtrl :: SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) et [CStatusBarCtrl :: GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext) pour définir et récupérer le texte info-bulle d’un volet spécifique.

Une fois que l’info-bulle a été définie, elle s’affiche uniquement si la partie a une icône et aucun texte, ou si tout le texte ne peut pas être affiché à l’intérieur de la partie. Les info-bulles ne sont pas prises en charge en mode simple.

## <a name="see-also"></a>Voir aussi

[Utilisation de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
