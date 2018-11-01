---
title: Méthodes de création d'une barre d'état
ms.date: 11/04/2016
helpviewer_keywords:
- CStatusBar class [MFC], vs. CStatusBarCtrl
- methods [MFC], creating status bars
- CStatusBarCtrl class [MFC], vs. CStatusBar
- CStatusBarCtrl class [MFC], creating
- methods [MFC]
- status bars [MFC], creating
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
ms.openlocfilehash: 1156f8bdeafb71dc9e6dbd9fc5b85607542918f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587974"
---
# <a name="methods-of-creating-a-status-bar"></a>Méthodes de création d'une barre d'état

MFC fournit deux classes pour créer des barres d’état : [CStatusBar](../mfc/reference/cstatusbar-class.md) et [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) (qui encapsule l’API de contrôle commun de Windows). `CStatusBar` fournit toutes les fonctionnalités de la barre d’état contrôle commun, il interagit avec les menus et barres d’outils automatiquement, et il gère la plupart des paramètres de contrôle communs requis et des structures pour vous ; Toutefois, votre fichier exécutable obtenu sera plus grand que celui créé à l’aide de `CStatusBarCtrl`.

`CStatusBarCtrl` généralement les résultats dans un fichier exécutable plus petit et que vous préférez peut-être utiliser `CStatusBarCtrl` si vous ne souhaitez pas intégrer de la barre d’état dans l’architecture MFC. Si vous envisagez d’utiliser `CStatusBarCtrl` et intégrer la barre d’état dans l’architecture MFC, vous devez prendre soin de communiquer les manipulations à MFC du contrôle de la barre d’état. Cette communication n’est pas difficile ; Toutefois, il est un travail supplémentaire qui n’est pas nécessaire lorsque vous utilisez `CStatusBar`.

Visual C++ propose deux façons de tirer parti du contrôle commun de barre de statut.

- Créer la barre à l’aide d’état `CStatusBar`, puis appelez [CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl) pour accéder à la `CStatusBarCtrl` fonctions membres.

- Créer la barre à l’aide d’état [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)du constructeur.

Les deux méthodes vous donnera accès aux fonctions membres du contrôle de barre d’état. Lorsque vous appelez `CStatusBar::GetStatusBarCtrl`, elle retourne une référence à un `CStatusBarCtrl` afin de pouvoir utiliser un ensemble de fonctions membres de l’objet. Consultez [CStatusBar](../mfc/reference/cstatusbar-class.md) pour plus d’informations sur la construction et la création de la barre à l’aide d’un état `CStatusBar`.

## <a name="see-also"></a>Voir aussi

[Utilisation de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

