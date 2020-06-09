---
title: Activation des info-bulles
ms.date: 11/04/2016
helpviewer_keywords:
- initializing tool tips [MFC]
- enabling tool tips [MFC]
- tool tips [MFC], initializing
- tool tips [MFC], enabling
ms.assetid: 06b7c889-7722-4ce6-8b88-9efa50fe6369
ms.openlocfilehash: bdd5c54f9174c42e17db0be7e13ea31acfea2dcf
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615728"
---
# <a name="enabling-tool-tips"></a>Activation des info-bulles

Vous pouvez activer la prise en charge des info-bulles pour les contrôles enfants d’une fenêtre (tels que les contrôles d’un mode formulaire ou d’une boîte de dialogue).

### <a name="to-enable-tool-tips-for-the-child-controls-of-a-window"></a>Pour activer les info-bulles pour les contrôles enfants d’une fenêtre

1. Appelez `EnableToolTips` pour la fenêtre pour laquelle vous souhaitez fournir des info-bulles.

1. Fournissez une chaîne pour chaque contrôle de votre gestionnaire de [notification TTN_NEEDTEXT](handling-ttn-needtext-notification-for-tool-tips.md) . Le gestionnaire se trouve dans la table des messages de la fenêtre qui contient les contrôles enfants (par exemple, votre classe d’affichage de formulaire). Ce gestionnaire doit appeler une fonction qui identifie le contrôle et définit **pszText** pour spécifier le texte utilisé par le contrôle d’info-bulle.

## <a name="see-also"></a>Voir aussi

[Info-bulles dans les fenêtres non dérivées de CFrameWnd](tool-tips-in-windows-not-derived-from-cframewnd.md)
