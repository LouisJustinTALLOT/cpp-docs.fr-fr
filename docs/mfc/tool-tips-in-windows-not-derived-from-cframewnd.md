---
description: 'En savoir plus sur les éléments suivants : info-bulles dans Windows non dérivées de CFrameWnd'
title: Info-bulles dans les fenêtres non dérivées de CFrameWnd
ms.date: 11/04/2016
helpviewer_keywords:
- enabling tool tips [MFC]
- TOOLTIPTEXT structure [MFC]
- Help [MFC], tool tips for controls
- TTN_NEEDTEXT message [MFC]
- controls [MFC], tool tips
- handler functions [MFC], tool tips
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
ms.openlocfilehash: 1d5d2ba744800424a9dce325f9d4341956bc22ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264425"
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>Info-bulles dans les fenêtres non dérivées de CFrameWnd

Cette famille d’articles traite de l’activation d’info-bulles pour les contrôles contenus dans une fenêtre qui n’est pas dérivée de [CFrameWnd](../mfc/reference/cframewnd-class.md). Les info- [bulles des barres d’outils](../mfc/toolbar-tool-tips.md) fournissent des informations sur les info-bulles des contrôles dans un `CFrameWnd` .

Les sujets abordés dans cet article sont les suivants :

- [Activation des info-bulles](../mfc/enabling-tool-tips.md)

- [Gestion de la notification TTN_NEEDTEXT pour les info-bulles](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)

- [La structure TOOLTIPTEXT](../mfc/tooltiptext-structure.md)

Les info-bulles s’affichent automatiquement pour les boutons et autres contrôles contenus dans une fenêtre parente dérivée de `CFrameWnd` . En effet, `CFrameWnd` a un gestionnaire par défaut pour la notification [TTN_GETDISPINFO](/windows/win32/Controls/ttn-getdispinfo) , qui gère les notifications **TTN_NEEDTEXT** à partir de contrôles d’info-bulle associés aux contrôles.

Toutefois, ce gestionnaire par défaut n’est pas appelé lorsque l' **TTN_NEEDTEXT** notification est envoyée à partir d’un contrôle d’info-bulle associé à un contrôle dans une fenêtre qui n’est pas un `CFrameWnd` , tel qu’un contrôle sur une boîte de dialogue ou un mode formulaire. Par conséquent, il est nécessaire de fournir une fonction de gestionnaire pour le **TTN_NEEDTEXT** message de notification afin d’afficher des info-bulles pour les contrôles enfants.

Les info-bulles par défaut fournies pour votre Windows par [CWnd :: EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips) n’ont pas de texte associé. Pour récupérer le texte de l’info-bulle à afficher, la notification **TTN_NEEDTEXT** est envoyée à la fenêtre parente du contrôle d’info-bulle juste avant l’affichage de la fenêtre d’info-bulle. S’il n’existe aucun gestionnaire pour ce message afin d’affecter une valeur au membre *pszText* de la structure **ToolTipText** , aucun texte n’est affiché pour l’info-bulle.

## <a name="see-also"></a>Voir aussi

[Info-bulles](../mfc/tool-tips.md)
