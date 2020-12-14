---
description: 'En savoir plus sur : implémentation de la barre d’État dans MFC'
title: Implémentation de la barre d'état dans MFC
ms.date: 11/19/2018
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
ms.openlocfilehash: d42f8b4bf6ae72cf8eb4a12d1f5eafb8603c5e1b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216754"
---
# <a name="status-bar-implementation-in-mfc"></a>Implémentation de la barre d'état dans MFC

Un objet [CStatusBar](../mfc/reference/cstatusbar-class.md) est une barre de contrôle avec une ligne de volets de sortie de texte. Les volets de sortie sont fréquemment utilisés comme des lignes de message et comme indicateurs d'états. Par exemple, les lignes de message d’aide du menu décrivent brièvement la commande de menu sélectionnée et les indicateurs qui indiquent l’état du verrou de défilement, Verr. NUM et autres clés.

À partir de la version 4,0 de MFC, les barres d’État sont implémentées à l’aide de la classe [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md), qui encapsule un contrôle commun de barre d’État. Pour la compatibilité descendante, MFC conserve l’ancienne implémentation de la barre d’État dans la classe `COldStatusBar` . La documentation relative aux versions antérieures de MFC décrit `COldStatusBar` sous `CStatusBar` .

[CStatusBar :: GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl), une fonction membre nouvelle dans MFC 4,0, vous permet de tirer parti de la prise en charge par le contrôle commun Windows de la personnalisation de la barre d’État et des fonctionnalités supplémentaires. `CStatusBar` les fonctions membres vous offrent la plupart des fonctionnalités des contrôles communs Windows. Toutefois, lorsque vous appelez `GetStatusBarCtrl` , vous pouvez affecter à vos barres d’État une plus grande partie des caractéristiques d’une barre d’État. Quand vous appelez `GetStatusBarCtrl` , une référence à un objet est retournée `CStatusBarCtrl` . Vous pouvez utiliser cette référence pour manipuler le contrôle de barre d’État.

L’illustration suivante montre une barre d’État qui affiche plusieurs indicateurs.

![Barre d’État](../mfc/media/vc37dy1.gif "Barre d'état") <br/>
Une barre d’État

À l’instar de la barre d’outils, l’objet de barre d’État est incorporé dans sa fenêtre frame parente et est construit automatiquement lorsque la fenêtre frame est construite. La barre d’État, comme toutes les barres de contrôle, est automatiquement détruite lorsque le frame parent est détruit.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Mise à jour du texte d’un volet de barre d’État](../mfc/updating-the-text-of-a-status-bar-pane.md)

- Classes MFC [CStatusBar](../mfc/reference/cstatusbar-class.md) et [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)

- [Barres de contrôle](../mfc/control-bars.md)

- [Barres de boîte de dialogue](../mfc/dialog-bars.md)

- [Barres d’outils (implémentation de la barre d’outils MFC)](../mfc/mfc-toolbar-implementation.md)

## <a name="see-also"></a>Voir aussi

[Barres d’État](../mfc/status-bars.md)
