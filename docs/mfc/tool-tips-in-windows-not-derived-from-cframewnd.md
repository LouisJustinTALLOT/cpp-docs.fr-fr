---
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
ms.openlocfilehash: 3d44f2c503b689360f040e6804d319c331d5c0ca
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260658"
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>Info-bulles dans les fenêtres non dérivées de CFrameWnd

Cette série d’articles couvre l’activation de l’info-bulles pour les contrôles contenus dans une fenêtre qui n’est pas dérivée [CFrameWnd](../mfc/reference/cframewnd-class.md). L’article [barres d’outils, info-bulles](../mfc/toolbar-tool-tips.md) fournit des informations sur les info-bulles pour les contrôles dans un `CFrameWnd`.

Les sujets abordés dans cette série d’articles incluent :

- [Activation des info-bulles](../mfc/enabling-tool-tips.md)

- [Gestion de la notification TTN_NEEDTEXT pour les info-bulles](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)

- [La ToolTipText, Structure](../mfc/tooltiptext-structure.md)

Info-bulles sont affichent automatiquement pour les boutons et autres contrôles contenus dans une fenêtre parente dérivé `CFrameWnd`. Il s’agit, car `CFrameWnd` a un gestionnaire par défaut pour le [TTN_GETDISPINFO](/windows/desktop/Controls/ttn-getdispinfo) notification, qui gère les **TTN_NEEDTEXT** notifications à partir de l’outil de conseil contrôles associés aux contrôles.

Toutefois, ce gestionnaire par défaut est appelé pas lorsque le **TTN_NEEDTEXT** notification est envoyée à partir d’un contrôle d’info-bulle associé à un contrôle dans une fenêtre qui n’est pas un `CFrameWnd`, tel qu’un contrôle sur une boîte de dialogue ou une vue de formulaire. Par conséquent, il est nécessaire pour fournir une fonction de gestionnaire pour le **TTN_NEEDTEXT** message de notification pour afficher des info-bulles pour les contrôles enfants.

L’info-bulles par défaut fournis pour les fenêtres en [CWnd::EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips) n’ont pas de texte qui s’y rapportent. Pour récupérer le texte de l’info-bulle à afficher, le **TTN_NEEDTEXT** notification est envoyée à la fenêtre du parent du contrôle info-bulle juste avant que la fenêtre outil de Conseil s’affiche. S’il n’existe aucun gestionnaire pour ce message affecter une valeur à la *pszText* membre de la **TOOLTIPTEXT** structure, il n’y aura aucun texte affiché pour l’info-bulle.

## <a name="see-also"></a>Voir aussi

[Info-bulles](../mfc/tool-tips.md)
