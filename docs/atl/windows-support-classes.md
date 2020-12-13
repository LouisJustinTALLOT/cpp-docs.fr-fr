---
description: 'En savoir plus sur : classes de prise en charge Windows'
title: Classes de prise en charge Windows (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
ms.openlocfilehash: c88a6ef878a428581ca090e78b2fac3b5e02131d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138059"
---
# <a name="windows-support-classes"></a>Classes de prise en charge Windows

Les classes suivantes fournissent la prise en charge de Windows :

- [_U_MENUorID](../atl/reference/u-menuorid-class.md) Fournit des wrappers pour `CreateWindow` et `CreateWindowEx` .

- [CWindow](../atl/reference/cwindow-class.md) Contient des méthodes pour manipuler une fenêtre. `CWindow` est la classe de base des classes `CWindowImpl`, `CDialogImpl` et `CContainedWindow`.

- [CWindowImpl](../atl/reference/cwindowimpl-class.md) Implémente une fenêtre basée sur une nouvelle classe de fenêtre. Vous permet également de sous-classer ou de superclasser la fenêtre.

- [CDialogImpl](../atl/reference/cdialogimpl-class.md) Implémente une boîte de dialogue.

- [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) Implémente une boîte de dialogue (modale ou non modale) qui héberge des contrôles ActiveX.

- [CSimpleDialog](../atl/reference/csimpledialog-class.md) Implémente une boîte de dialogue (modale ou non modale) avec des fonctionnalités de base.

- [CAxWindow](../atl/reference/caxwindow-class.md) Manipule une fenêtre qui héberge un contrôle ActiveX.

- [CAxWindow2T](../atl/reference/caxwindow2t-class.md) Fournit des méthodes pour manipuler une fenêtre qui héberge un contrôle ActiveX et prend également en charge l’hébergement de contrôles ActiveX sous licence.

- [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) Implémente une fenêtre contenue dans un autre objet.

- [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) Gère les informations d’une nouvelle classe de fenêtre.

- [CDynamicChain](../atl/reference/cdynamicchain-class.md) Prend en charge le chaînage dynamique des tables des messages.

- [CMessageMap](../atl/reference/cmessagemap-class.md) Permet à un objet d’exposer ses tables de messages à d’autres objets.

- [CWinTraits](../atl/reference/cwintraits-class.md) Fournit une méthode simple pour standardiser les caractéristiques d’un objet fenêtre ATL.

- [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) Fournit des valeurs par défaut pour les styles de fenêtre et les styles étendus utilisés pour créer une fenêtre. Ces valeurs sont ajoutées à l’aide de l’opérateur OR logique, aux valeurs fournies lors de la création d’une fenêtre.

## <a name="related-articles"></a>Articles connexes

[Classes de fenêtre ATL](../atl/atl-window-classes.md)

[Tutoriel ATL](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../atl/atl-class-overview.md)<br/>
[Macros de table des messages](../atl/reference/message-map-macros-atl.md)<br/>
[Macros de classe de fenêtre](../atl/reference/window-class-macros.md)
