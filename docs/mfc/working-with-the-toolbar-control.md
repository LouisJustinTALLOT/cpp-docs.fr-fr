---
description: 'En savoir plus sur : utilisation du contrôle ToolBar'
title: Utilisation du contrôle ToolBar
ms.date: 11/04/2016
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
ms.openlocfilehash: bb5b14b35deeff515468a16c82a606704300a395
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197463"
---
# <a name="working-with-the-toolbar-control"></a>Utilisation du contrôle ToolBar

Cet article explique comment vous pouvez accéder à l’objet [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) sous-jacent à [CToolBar](../mfc/reference/ctoolbar-class.md) pour mieux contrôler vos barres d’outils. Il s’agit d’une rubrique avancée.

## <a name="procedures"></a>Procédures

#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>Pour accéder au contrôle commun de barre d’outils sous-jacent à votre objet CToolBar

1. Appelez [CToolBar :: GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl).

`GetToolBarCtrl` retourne une référence à un objet [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) . Vous pouvez utiliser la référence pour appeler des fonctions membres de la classe de contrôle ToolBar.

> [!CAUTION]
> Bien que `CToolBarCtrl` l’appel des fonctions d' **extraction** soit sécurisé, soyez prudent si vous appelez les fonctions **Set** . Il s’agit d’une rubrique avancée. Normalement, vous n’avez pas besoin d’accéder au contrôle de barre d’outils sous-jacent.

### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Contrôles (contrôles communs Windows)](../mfc/controls-mfc.md)

- [Notions de base de barre d'outils](../mfc/toolbar-fundamentals.md)

- [Ancrer et rendre flottantes les barres d'outils](../mfc/docking-and-floating-toolbars.md)

- [Redimensionnement dynamique de la barre d’outils](../mfc/docking-and-floating-toolbars.md)

- [Info-bulles de barre d'outils](../mfc/toolbar-tool-tips.md)

- [Mises à jour de la barre d’État Flyby](../mfc/toolbar-tool-tips.md)

- [Gestion des notifications pour les info-bulles](../mfc/handling-tool-tip-notifications.md)

- Classes [CToolBar](../mfc/reference/ctoolbar-class.md) et [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Gestion des notifications de personnalisation](../mfc/handling-customization-notifications.md)

- [Barres d’outils multiples](../mfc/toolbar-fundamentals.md)

- [Utilisation de vos anciennes barres d'outils](../mfc/using-your-old-toolbars.md)

- [Barres de contrôle](../mfc/control-bars.md)

Pour obtenir des informations générales sur l’utilisation des contrôles communs Windows, consultez [contrôles communs](/windows/win32/Controls/common-controls-intro).

## <a name="see-also"></a>Voir aussi

[Implémentation de la barre d’outils MFC](../mfc/mfc-toolbar-implementation.md)
