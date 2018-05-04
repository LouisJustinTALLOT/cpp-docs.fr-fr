---
title: Introduction aux Classes de fenêtre ATL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window classes
ms.assetid: 503efc2c-a269-495d-97cf-3fb300d52f3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea9b275831aee3ea96da1036019db07f9e2dfc93
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="introduction-to-atl-window-classes"></a>Introduction aux Classes de fenêtre ATL
Les classes ATL suivantes sont conçues pour implémenter et manipuler des fenêtres :  
  
-   [CWindow](../atl/reference/cwindow-class.md) permet de joindre un handle de fenêtre pour le `CWindow` objet. Vous appelez ensuite `CWindow` méthodes pour manipuler la fenêtre.  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md) vous permet d’implémenter une nouvelle fenêtre et de traiter les messages avec une table des messages. Vous pouvez créer une fenêtre basée sur un nouveau Windows, surclasser une classe existante ou d’une classe, une fenêtre existante.  
  
-   [CDialogImpl](../atl/reference/cdialogimpl-class.md) vous permet d’implémenter une modale ou une boîte de dialogue non modale et traiter les messages avec une table des messages.  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) est une classe prédéfinie qui implémente une fenêtre dont table des messages est contenue dans une autre classe. À l’aide de `CContainedWindowT` vous permet de centraliser le traitement des messages dans une classe.  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) vous permet d’implémenter une boîte de dialogue (modale ou non modale) qui héberge des contrôles ActiveX.  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md) vous permet d’implémenter une boîte de dialogue modale avec les fonctionnalités de base.  
  
-   [Objet CAxWindow](../atl/reference/caxwindow-class.md) vous permet d’implémenter une fenêtre qui héberge un contrôle ActiveX.  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md) vous permet d’implémenter une fenêtre qui héberge un contrôle ActiveX sous licence.  
  
 En plus des classes de fenêtre spécifique, ATL fournit plusieurs classes destinées à faciliter l’implémentation d’un objet fenêtre ATL. En voici la liste :  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) gère les informations d’une nouvelle classe de fenêtre.  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md) et [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) fournissent une méthode simple de standardiser les traits d’un objet fenêtre ATL.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes de fenêtre](../atl/atl-window-classes.md)

