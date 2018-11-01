---
title: Implémentation de la barre d'état dans MFC
ms.date: 11/04/2016
f1_keywords:
- COldStatusBar
helpviewer_keywords:
- status bars [MFC], implementing in MFC
- CStatusBarCtrl class [MFC], and MFC status bars
- CStatusBar class [MFC], and CStatusBarCtrl class [MFC]
- CStatusBarCtrl class [MFC], and CStatusBar class [MFC]
- status bars [MFC], backward compatibility
- status bars [MFC], old with COldStatusBar class [MFC]
- COldStatusBar class [MFC]
- status bars [MFC], and CStatusBarCtrl class
- CStatusBar class [MFC], and MFC status bars
- status indicators
- status bars [MFC], Windows 95 implementation
ms.assetid: be5cd876-38e3-4d5c-b8cb-16d57a16a142
ms.openlocfilehash: 25848e4467a0d767c40ffb00a1bd4d50a062d3a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496277"
---
# <a name="status-bar-implementation-in-mfc"></a>Implémentation de la barre d'état dans MFC

Un [CStatusBar](../mfc/reference/cstatusbar-class.md) objet est une barre de contrôle avec une ligne de volets de sortie de texte. Les volets de sortie sont fréquemment utilisés comme des lignes de message et comme indicateurs d'états. Exemples : les lignes de message à l’aide de menu qui expliquent brièvement la commande de menu sélectionné et les indicateurs qui indiquent l’état de l’arrêt défil, VERR. NUM et défil.

Depuis la version 4.0 de MFC, les barres d’état sont implémentées à l’aide de la classe [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md), qui encapsule une barre de contrôle commun d’état. Pour la compatibilité descendante, MFC conserve l’ancienne implémentation de barre d’état dans la classe `COldStatusBar`. Décrit la documentation pour les versions antérieures de MFC `COldStatusBar` sous `CStatusBar`.

[CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl), une fonction membre new 4.0 de MFC, vous permet de tirer parti de la prise en charge du contrôle commun Windows pour la personnalisation et des fonctionnalités supplémentaires de la barre d’état. `CStatusBar` fonctions membres vous donnent la plupart des fonctionnalités des contrôles communs Windows ; Toutefois, lorsque vous appelez `GetStatusBarCtrl`, vous pouvez donner à votre barres d’état encore plus des caractéristiques d’une barre d’état. Lorsque vous appelez `GetStatusBarCtrl`, elle retournera une référence à un `CStatusBarCtrl` objet. Vous pouvez utiliser cette référence pour manipuler le contrôle de barre d’état.

La figure suivante montre une barre d’état affichant plusieurs indicateurs.

![Barre d’état](../mfc/media/vc37dy1.gif "vc37dy1") une barre d’état

Comme la barre d’outils, l’objet de barre d’état est incorporé dans sa fenêtre frame parente et est généré automatiquement lors de la construction de la fenêtre frame. La barre d’état, comme toutes les barres de contrôle est détruite automatiquement également lorsque le frame parent est détruit.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [La mise à jour le texte d’un volet de barre d’état](../mfc/updating-the-text-of-a-status-bar-pane.md)

- Classes MFC [CStatusBar](../mfc/reference/cstatusbar-class.md) et [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)

- [Barres de contrôles](../mfc/control-bars.md)

- [Barres de boîte de dialogue](../mfc/dialog-bars.md)

- [Barres d’outils (implémentation de barre d’outils MFC)](../mfc/mfc-toolbar-implementation.md)

## <a name="see-also"></a>Voir aussi

[Barres d’état](../mfc/status-bars.md)

