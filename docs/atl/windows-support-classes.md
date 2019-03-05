---
title: Classes de prise en charge de Windows (ATL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.atl.windows
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
ms.openlocfilehash: e7e9e1f4fb94537cdd131e58ef3fc481ee1c012e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281029"
---
# <a name="windows-support-classes"></a>Classes de prise en charge de Windows

Les classes suivantes fournissent la prise en charge pour windows :

- [_U_MENUorID](../atl/reference/u-menuorid-class.md) fournit des wrappers pour `CreateWindow` et `CreateWindowEx`.

- [CWindow](../atl/reference/cwindow-class.md) contient des méthodes pour manipuler une fenêtre. `CWindow` est la classe de base des classes `CWindowImpl`, `CDialogImpl` et `CContainedWindow`.

- [CWindowImpl](../atl/reference/cwindowimpl-class.md) implémente une fenêtre basée sur une nouvelle classe de fenêtre. Vous permet également à la sous-classe ou superclasse la fenêtre.

- [CDialogImpl](../atl/reference/cdialogimpl-class.md) implémente une boîte de dialogue.

- [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) implémente une boîte de dialogue (modale ou non modale) qui héberge des contrôles ActiveX.

- [CSimpleDialog](../atl/reference/csimpledialog-class.md) implémente une boîte de dialogue (modale ou non modale) avec les fonctionnalités de base.

- [Objet CAxWindow](../atl/reference/caxwindow-class.md) manipule une fenêtre qui héberge un contrôle ActiveX.

- [CAxWindow2T](../atl/reference/caxwindow2t-class.md) fournit des méthodes pour manipuler une fenêtre qui héberge un contrôle ActiveX et prend également en charge pour l’hébergement de contrôles ActiveX sous licence.

- [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) implémente une fenêtre contenue dans un autre objet.

- [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) gère les informations d’une nouvelle classe de fenêtre.

- [CDynamicChain](../atl/reference/cdynamicchain-class.md) prend en charge le chaînage dynamique des tables des messages.

- [CMessageMap](../atl/reference/cmessagemap-class.md) autorise un objet d’exposer son message est mappé à d’autres objets.

- [CWinTraits](../atl/reference/cwintraits-class.md) fournit une méthode simple suivant : standardiser les caractéristiques d’un objet fenêtre ATL.

- [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) fournit les valeurs par défaut pour les styles de fenêtre et les styles étendus utilisés pour créer une fenêtre. Ces valeurs sont ajoutées, à l’aide de l’opérateur OR logique, pour les valeurs fournies lors de la création d’une fenêtre.

## <a name="related-articles"></a>Articles connexes

[ATL, classes de fenêtre](../atl/atl-window-classes.md)

[Didacticiel ATL](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../atl/atl-class-overview.md)<br/>
[Macros de table des messages](../atl/reference/message-map-macros-atl.md)<br/>
[Macros de classe de fenêtre](../atl/reference/window-class-macros.md)
