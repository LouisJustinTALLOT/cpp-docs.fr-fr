---
description: 'En savoir plus sur : Introduction aux classes de fenêtres ATL'
title: Présentation des classes de fenêtre ATL
ms.date: 11/04/2016
helpviewer_keywords:
- window classes
ms.assetid: 503efc2c-a269-495d-97cf-3fb300d52f3d
ms.openlocfilehash: 54a9d9764450025e51f9fac368a3434ca786fe09
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152722"
---
# <a name="introduction-to-atl-window-classes"></a>Présentation des classes de fenêtre ATL

Les classes ATL suivantes sont conçues pour implémenter et manipuler des fenêtres :

- [CWindow](../atl/reference/cwindow-class.md) vous permet d’attacher un handle de fenêtre à l' `CWindow` objet. Vous appelez ensuite `CWindow` des méthodes pour manipuler la fenêtre.

- [CWindowImpl](../atl/reference/cwindowimpl-class.md) vous permet d’implémenter une nouvelle fenêtre et de traiter les messages avec une table des messages. Vous pouvez créer une fenêtre basée sur une nouvelle classe Windows, superclasser une classe existante ou sous-classe une fenêtre existante.

- [CDialogImpl](../atl/reference/cdialogimpl-class.md) vous permet d’implémenter une boîte de dialogue modale ou non modale et de traiter les messages avec une table des messages.

- [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) est une classe prédéfinie qui implémente une fenêtre dont la table des messages est contenue dans une autre classe. L’utilisation de `CContainedWindowT` vous permet de centraliser le traitement des messages dans une classe.

- [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) vous permet d’implémenter une boîte de dialogue (modale ou non modale) qui héberge des contrôles ActiveX.

- [CSimpleDialog](../atl/reference/csimpledialog-class.md) vous permet d’implémenter une boîte de dialogue modale avec des fonctionnalités de base.

- [CAxWindow](../atl/reference/caxwindow-class.md) vous permet d’implémenter une fenêtre qui héberge un contrôle ActiveX.

- [CAxWindow2T](../atl/reference/caxwindow2t-class.md) vous permet d’implémenter une fenêtre qui héberge un contrôle ActiveX sous licence.

En plus des classes de fenêtres spécifiques, ATL fournit plusieurs classes conçues pour faciliter l’implémentation d’un objet fenêtre ATL. Les voici :

- [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) gère les informations d’une nouvelle classe de fenêtre.

- [CWinTraits](../atl/reference/cwintraits-class.md) et [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) fournissent une méthode simple de normalisation des caractéristiques d’un objet fenêtre ATL.

## <a name="see-also"></a>Voir aussi

[classes de fenêtre](../atl/atl-window-classes.md)
