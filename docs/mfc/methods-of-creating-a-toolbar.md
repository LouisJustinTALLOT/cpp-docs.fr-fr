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
ms.openlocfilehash: b70e6f4dc15023b878bb58d6b7d0739eeb173d53
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624250"
---
# <a name="methods-of-creating-a-toolbar"></a>Méthodes de création d'une barre d'outils

MFC fournit deux classes pour créer des barres d’outils : [CToolBar](reference/ctoolbar-class.md) et [CToolBarCtrl](reference/ctoolbarctrl-class.md) (qui encapsule l’API de contrôle commun Windows). `CToolBar`fournit toutes les fonctionnalités du contrôle commun de barre d’outils et gère un grand nombre des paramètres et structures de contrôle communs requis pour vous. Toutefois, l’exécutable qui en résulte sera généralement plus grand que celui créé à l’aide de `CToolBarCtrl` .

`CToolBarCtrl`entraîne généralement un fichier exécutable plus petit, et vous préférerez peut-être utiliser `CToolBarCtrl` si vous n’avez pas l’intention d’intégrer la barre d’outils dans l’architecture MFC. Si vous envisagez d’utiliser `CToolBarCtrl` et d’intégrer la barre d’outils dans l’architecture MFC, vous devez prendre soin de communiquer les manipulations des contrôles ToolBar aux MFC. Cette communication n’est pas difficile. Toutefois, il s’agit d’un travail supplémentaire qui n’est pas nécessaire lorsque vous utilisez `CToolBar` .

Visual C++ offre deux façons de tirer parti du contrôle commun de barre d’outils.

- Créez la barre d’outils à l’aide de `CToolBar` , puis appelez [CToolBar :: GetToolBarCtrl](reference/ctoolbar-class.md#gettoolbarctrl) pour accéder aux `CToolBarCtrl` fonctions membres.

- Créez la barre d’outils à l’aide du constructeur de [CToolBarCtrl](reference/ctoolbarctrl-class.md).

L’une ou l’autre des méthodes vous donne accès aux fonctions membres du contrôle ToolBar. Quand vous appelez `CToolBar::GetToolBarCtrl` , elle retourne une référence à un `CToolBarCtrl` objet afin que vous puissiez utiliser l’un ou l’autre ensemble de fonctions membres. Pour plus d’informations sur la construction et la création d’une barre d’outils à l’aide de, consultez [CToolBar](reference/ctoolbar-class.md) `CToolBar` .

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[Commandes](controls-mfc.md)
