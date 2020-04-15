---
title: Utilisation du contrôle ToolBar
ms.date: 11/04/2016
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
ms.openlocfilehash: 371f1944fae655556bbc9f89d7ffcce7cc326e5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365245"
---
# <a name="working-with-the-toolbar-control"></a>Utilisation du contrôle ToolBar

Cet article explique comment vous pouvez accéder à [l’objet CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) sous-jacent à un [CToolBar](../mfc/reference/ctoolbar-class.md) pour un meilleur contrôle sur vos barres d’outils. C’est un sujet avancé.

## <a name="procedures"></a>Procédures

#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>Pour accéder au contrôle commun de la barre d’outils sous-jacent à votre objet CToolBar

1. Appelez [CToolBar:GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl).

`GetToolBarCtrl`renvoie une référence à un objet [CToolBarCtrl.](../mfc/reference/ctoolbarctrl-class.md) Vous pouvez utiliser la référence pour appeler les fonctions des membres de la classe de contrôle de la barre d’outils.

> [!CAUTION]
> Tout `CToolBarCtrl` en appelant les fonctions **Get** est sûr, faites preuve de prudence si vous appelez les fonctions **Set.** C’est un sujet avancé. Normalement, vous ne devriez pas avoir besoin d’accéder au contrôle sous-jacent de la barre d’outils.

### <a name="what-do-you-want-to-know-more-about"></a>Qu’est-ce que vous voulez savoir plus sur

- [Contrôles (contrôles communs Windows)](../mfc/controls-mfc.md)

- [Principes fondamentaux de la barre d’outils](../mfc/toolbar-fundamentals.md)

- [Docking et barres d’outils flottantes](../mfc/docking-and-floating-toolbars.md)

- [Resizing dynamiquement la barre d’outils](../mfc/docking-and-floating-toolbars.md)

- [Info-bulles de barre d'outils](../mfc/toolbar-tool-tips.md)

- [Mises à jour de la barre d’état Flyby](../mfc/toolbar-tool-tips.md)

- [Gestion des notifications pour les info-bulles](../mfc/handling-tool-tip-notifications.md)

- Les classes [CToolBar](../mfc/reference/ctoolbar-class.md) et [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Gestion des notifications de personnalisation](../mfc/handling-customization-notifications.md)

- [Plusieurs barres d’outils](../mfc/toolbar-fundamentals.md)

- [Utilisation de vos anciennes barres d'outils](../mfc/using-your-old-toolbars.md)

- [Barres de contrôle](../mfc/control-bars.md)

Pour plus d’informations générales sur l’utilisation de contrôles communs Windows, voir [contrôles communs](/windows/win32/Controls/common-controls-intro).

## <a name="see-also"></a>Voir aussi

[Implémentation de la barre d'outils MFC](../mfc/mfc-toolbar-implementation.md)
