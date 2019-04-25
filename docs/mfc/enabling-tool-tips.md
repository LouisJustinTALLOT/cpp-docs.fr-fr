---
title: Activation des info-bulles
ms.date: 11/04/2016
helpviewer_keywords:
- initializing tool tips [MFC]
- enabling tool tips [MFC]
- tool tips [MFC], initializing
- tool tips [MFC], enabling
ms.assetid: 06b7c889-7722-4ce6-8b88-9efa50fe6369
ms.openlocfilehash: 892ed76ef7e021544505600110cd2569d6078312
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174950"
---
# <a name="enabling-tool-tips"></a>Activation des info-bulles

Vous pouvez activer la prise en charge d’outils info-bulle pour les contrôles enfants d’une fenêtre (par exemple, les contrôles sur une formulaire vue ou boîte de dialogue).

### <a name="to-enable-tool-tips-for-the-child-controls-of-a-window"></a>Pour activer les info-bulles pour les contrôles enfants d’une fenêtre

1. Appelez `EnableToolTips` pour la fenêtre pour laquelle vous souhaitez fournir des info-bulles.

1. Fournir une chaîne pour chaque contrôle dans votre [la notification TTN_NEEDTEXT](../mfc/handling-ttn-needtext-notification-for-tool-tips.md) gestionnaire. Le gestionnaire se trouve dans la table des messages de la fenêtre qui contient les contrôles enfants (par exemple, votre classe de vue de formulaire). Ce gestionnaire doit appeler une fonction qui identifie le contrôle, puis définit **pszText** pour spécifier le texte utilisé par le contrôle info-bulle.

## <a name="see-also"></a>Voir aussi

[Info-bulles dans les fenêtres non dérivées de CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)
