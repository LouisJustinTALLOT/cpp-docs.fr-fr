---
title: Utilisation du contrôle de barre d’outils | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e488d4b475cbc73f57bb90ccd081b6d490221d58
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202258"
---
# <a name="working-with-the-toolbar-control"></a>Utilisation du contrôle ToolBar
Cet article explique comment vous pouvez accéder à la [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objet sous-jacent un [CToolBar](../mfc/reference/ctoolbar-class.md) pour mieux contrôler vos barres d’outils. Il s’agit d’une rubrique avancée.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>Pour accéder au contrôle commun de barre d’outils sous-jacent de l’objet CToolBar  
  
1.  Appelez [CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl).  
  
 `GetToolBarCtrl` Retourne une référence à un [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objet. Vous pouvez utiliser la référence pour appeler des fonctions membres de la classe de contrôle de barre d’outils.  
  
> [!CAUTION]
>  Lors de l’appel `CToolBarCtrl` **obtenir** fonctions sont sécurisées, soyez prudent si vous appelez le **définir** fonctions. Il s’agit d’une rubrique avancée. Normalement, vous ne doit pas besoin d’accéder au contrôle sous-jacent de la barre d’outils.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur  
  
-   [Contrôles (contrôles communs Windows)](../mfc/controls-mfc.md)  
  
-   [Principes de base de barre d’outils](../mfc/toolbar-fundamentals.md)  
  
-   [Ancrer et rendre flottantes les barres d’outils](../mfc/docking-and-floating-toolbars.md)  
  
-   [Redimensionnement dynamique de la barre d’outils](../mfc/docking-and-floating-toolbars.md)  
  
-   [Info-bulles de barre d’outils](../mfc/toolbar-tool-tips.md)  
  
-   [Mises à jour de barre d’état flyby](../mfc/toolbar-tool-tips.md)  
  
-   [Gestion des notifications pour les info-bulle Info](../mfc/handling-tool-tip-notifications.md)  
  
-   Le [CToolBar](../mfc/reference/ctoolbar-class.md) et [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) classes  
  
-   [Gestion des notifications de personnalisation](../mfc/handling-customization-notifications.md)  
  
-   [Plusieurs barres d’outils](../mfc/toolbar-fundamentals.md)  
  
-   [À l’aide de vos anciennes barres d’outils](../mfc/using-your-old-toolbars.md)  
  
-   [Barres de contrôles](../mfc/control-bars.md)  
  
 Pour obtenir des informations générales sur l’utilisation de contrôles communs Windows, consultez [contrôles communs](/windows/desktop/Controls/common-controls-intro).  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation de la barre d’outils MFC](../mfc/mfc-toolbar-implementation.md)

