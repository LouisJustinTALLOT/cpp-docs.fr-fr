---
title: Méthodes de création d'une barre d'outils
ms.date: 11/04/2016
helpviewer_keywords:
- CToolBarCtrl class [MFC], and CToolBar class [MFC]
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- toolbar controls [MFC]
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
ms.openlocfilehash: f269ad990042f51554ec598b0bddbe5a6d7776b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383917"
---
# <a name="methods-of-creating-a-toolbar"></a>Méthodes de création d'une barre d'outils

MFC fournit deux classes pour créer des barres d’outils : [CToolBar](../mfc/reference/ctoolbar-class.md) et [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) (qui encapsule l’API de contrôle commun de Windows). `CToolBar` fournit toutes les fonctionnalités du contrôle commun de barre d’outils, et il gère la plupart des paramètres de contrôle communs requis et des structures pour vous ; Toutefois, votre fichier exécutable obtenu sera plus grand que celui créé à l’aide de `CToolBarCtrl`.

`CToolBarCtrl` généralement les résultats dans un fichier exécutable plus petit et que vous préférez peut-être utiliser `CToolBarCtrl` si vous ne souhaitez pas intégrer de la barre d’outils dans l’architecture MFC. Si vous envisagez d’utiliser `CToolBarCtrl` et intégrer la barre d’outils dans l’architecture MFC, vous devez prendre soin de communiquer les manipulations de contrôle de barre d’outils à MFC. Cette communication n’est pas difficile ; Toutefois, il est un travail supplémentaire qui n’est pas nécessaire lorsque vous utilisez `CToolBar`.

Visual C++ propose deux façons de tirer parti du contrôle commun de barre d’outils.

- Créer la barre d’outils à l’aide `CToolBar`, puis appelez [CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl) pour accéder à la `CToolBarCtrl` fonctions membres.

- Créer la barre d’outils à l’aide [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)du constructeur.

Les deux méthodes vous donnera accès aux fonctions membres du contrôle de barre d’outils. Lorsque vous appelez `CToolBar::GetToolBarCtrl`, elle retourne une référence à un `CToolBarCtrl` afin de pouvoir utiliser un ensemble de fonctions membres de l’objet. Consultez [CToolBar](../mfc/reference/ctoolbar-class.md) pour plus d’informations sur la construction et la création d’un à l’aide de la barre d’outils `CToolBar`.

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
