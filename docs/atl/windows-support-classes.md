---
title: Windows prend en charge les Classes (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.windows
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9182241b1d33c63aae523cae0c2c9602466e4c2e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090423"
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
[Macros de mappage des messages](../atl/reference/message-map-macros-atl.md)<br/>
[Macros de classe de fenêtre](../atl/reference/window-class-macros.md)

